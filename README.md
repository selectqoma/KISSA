# Lives on Air

A research dataset and article about biographical radio drama and documentary features in German archives. Python scrapers collect programme metadata from DRA, Wirklichkeit im Radio, and Hörspiel und Feature, then classify and analyse likely biographical works.

The active dataset is German-only. Other source adapters are experiments. The pipeline caches archive text for analysis; it does not download audio.

## Run

Requires Python 3.11+.

```sh
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
pip install -e .
python -m lives_on_air.scrapers.german_batch --dra-limit-per-term 80 --dra-max-pages 8 --dra-detail-workers 8
python -m lives_on_air.analysis.combine_outputs
python -m lives_on_air.analysis.deep_analysis
python -m lives_on_air.analysis.export_3d_map
```

Source tables go to `data/interim/`; merged data and analysis tables go to `data/processed/`. Read the [article](article/index.html) for findings and limitations. Classification identifies candidates for research, not confirmed biographies.
