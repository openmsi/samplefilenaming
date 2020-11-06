**DMREF Sample Tracking and Sample-Centric, File Naming Protocol**

v0.4

- Naming is sample based.
- Samples can include either physical or simulated samples
- Uniform format describes basics of sample production
- Format includes parent sample for derived samples
- Provides one node and back-link in directed acyclic graph
- Connects each file to a sample and processing history
- Filenames are annoyingly long, but descriptive
- Following the protocol is obligatory

System avoids added metadata entry tool. The goal in keying everything to these basic parts of sample and filenames captures the part of the history we can&#39;t catch elsewhere.

**Elements of Naming:**

- Lab identifier (where the sample or file was created)
  - important to create the starting point for connections between information
- Tool identifier (what tool created the sample or wrote the digital file)
  - It can be tricky to determine if this should be a specific instrument, piece of software, or computer
- Date Stamp (when created)
- Identifier for individual members of a group
  - If 10 samples are created in a process or 10 identical starting samples are processed then they get separated with this letter/number identifier
- Provenance identifier
  - Choice: Initials for Hopkins lab and Project identifier for things done elsewhere like CHESS or APS?
- Split/Cut identifier (to separate sub samples)
  - How do people do this for this project? Are there positional differences to worry about?
- Parent Sample ShortID (an identifier of a parent sample when one exists)

It&#39;s important that everyone understands the naming system and uses it correctly and consistently. As a group we need to identify any problems with the system and flesh out the vocabulary (agreed initials or abbreviations) so we can automate parsing of these names. Sample names will have a uniform format that looks like this:

AAA\_BBB\_YYYMMDD\_C\_III\_S\_(QQQQQQQQQ)-EE

| Name Item | Definition and Options |
| --- | --- |
| AAA | Lab Identifier |
|
 | - HYF: HyFire LaboratoryMCP
 | - Materials Characterization and Processing LaboratoryHEMI3D: 3D Characterization Laboratory
 | - CHESS: Cornell High Energy Synchrotron Source
 | - APS: Advanced Photon Source… |
| BBB | Tool Identifier. This list will evolve with the project when new analyses are desired. Additions can be done by investigators, but should be done thoughtfully so abbreviations make sense. All additions should include timely updates of the master description in the project github repo |
|
 | - TMSEM: Tescan Mira SEM image
 | - OEBSD: Oxford EBSD
 | - EEDS: EDAX EDS
 | - TL816Zi: Oscilloscope, Teledyne Lecroy 816Zi-B on HyFIRE…
 | - CP-FEM?: how do we distinguish these tools? Software or mode of investigation?
| YYYYMMDD | Year, month, day in numeric format. |
| C | Alphanumeric identifier if we have groups of otherwise the same sample. Runs 1-9 then A-Z. Useful if, for example, a process starts with multiple pieces of the sample material. |
| III | Provenance identifier. If AAA is a Hopkins lab then this is your initials (e.g. I would use DCE). If AAA is CHESS or the APS, then this is the GUP or other identifier. |
| S | Identifies a portion of a split or cut sample; it&#39;s 0 in the case the sample is not split. One common operation is to &quot;split&quot; a sample into multiple pieces, at some point, e.g. after a process, and then do different things to the different pieces including maybe even processing them again (re-extruding or rolling or heat treating). These new derivative samples inherit the original sample ID, but have an &quot;\_S&quot; included to indicate which &quot;piece&quot; of the original sample it came from (where S has the same format as C above). 
||• If a related operation is non-destructive analysis of a piece of the whole sample _without_ actually splitting the sample (e.g. diffraction along the length of the rod). In this latter case, &quot;\_NDS&quot; is instead appended (the first literal characters are &quot;\_ND&quot;, followed by S as defined above). 
||• For both the sample splitting and non-destructive position sensitive analysis, we should decide if and how to denote the relative positions of the samples
| QQQQQQQQQ | &quot;Short&quot; ID of parent sample from which this one is derived. If not derived from a prior sample, this is left off. If derived from more than one prior sample, each &quot;short&quot; ID is appended serially. Assuming the individual is the same for both, the short ID is of the form &quot;BBB\_YYYYMMDD\_C&quot; + an additional &quot;\_S&quot; if it is one part of a split sample. If the prior sample is from a different individual, the short ID is of the form &quot;BBB\_YYYYMMDD\_C\_III&quot; (with the III of the _prior sample_ person) + an additional &quot;\_S&quot; if a split sample. If the lab identifier is also different, then it should be included as well, i.e. &quot;AAA\_BBB\_YYYYMMDD\_C&quot; (with &quot;\_III&quot; and &quot;\_S&quot; appended as appropriate). Some examples are given below.
| EE | Optional Extra information. What information is included here is entirely up to you and it can be left off entirely. The only requirement is that it start with a &quot;-&quot;. This is to capture anything important about the sample and the measurement that won&#39;t be captured somewhere else (like in the file). If you use this, document it and alert others so we can be consistent. |