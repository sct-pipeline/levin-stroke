# levin-stroke

Processing pipeline for project involving stroke patients. PI is Dr. Levin.

The processing pipeline outputs the following metrics:

- Cord cross-sectional area at C2/C3 vertebral level
- DTI metrics & MTR, MTsat within white matter tracts: R/L CST, dorsal column, R/L RST

The processing pipeline uses the following images:

- T2w
- DWI
- GRE with/without MT pulse

The main steps involve:

- QC data for artifacts
- Curate data for BIDS compliance
- Run analysis script (which relies on [SCT](https://spinalcordtoolbox.com/)).
- QC analysis, manual correction of spinal cord masks and vertebral labeling
- Re-run analysis with corrected masks
- Aggregate results into CSV file

How to use:
```
pip install -r requirements.txt
sct_run_batch -jobs -1 -path-data ~/data/levin-stroke -path-output ~/levin_results/ -script ~/code/levin-stroke/process_data.sh
```
