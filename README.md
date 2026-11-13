# SF Multicell Twin — an open 5G NR ray-tracing lab

A complete, reproducible radio digital twin for teaching and research: a
three-site, nine-sector 5G NR layout (3.6 GHz) ray-traced with **Sionna RT**
over a downtown San Francisco city tile, with an interactive web artefact
wired directly to the trace output.

**Start here**
- ▶ Interactive artefact (13 Nov 2026 re-run): https://ysrao.github.io/twin5GNR-multicell-SF/twin5GNR-multicell-SionnaRT-EvalMesh-Nov13.html — the "Run Sionna RT on T4 (Colab)" button on that page opens the notebook that produced its data.
- Published v7 reference page: https://ysrao.github.io/twin5GNR-multicell-SF/twin5GNR-multicell-SionnaRT-Veg.html
- Notebook (Colab, author-hosted copy): https://colab.research.google.com/drive/1N_8UYlC4-CAJZH1zzeMLSJArcV7XsZmz

## Quickstart for students (fully local, $0)

1. Get the city mesh from its owner: the **Vexcel San Francisco 3D evaluation
   sample** (3D Tiles). Put the level-18 `.glb` tiles in a folder named `mesh`
   next to the notebook. (The mesh is Vexcel's and is not hosted here.)
2. Download `SF_sites.csv` and the notebook from the links in
   *Data and code availability* below.
3. Open the notebook in Colab (T4 GPU runtime), set `DATA_SOURCE = 'local'`
   in step 3, and **Run all**. A full-tile trace takes ~25 s. Results are
   written to `./out` on your own storage — the notebook never reads the
   author's accounts at run time.

## What's in the package

| Piece | Where |
|---|---|
| Notebook `twin5GNR_v7_SionnaRT_T4.ipynb` | Colab link above / author's Drive |
| Site file `SF_sites.csv` (84 rows: 12 v7 macro shifts + 72 v8 small-cell shifts) | Author's Drive (view-only) |
| Result files (full-tile 40 m run; tower-B patch 10 m run) + plots | Author's Drive (view-only) |
| Interactive artefacts (wired re-run page + published v7/v8 pages) | This repo (GitHub Pages) |
| Implementation code package | `multicell-code-v7-v8.zip` in this repo |

## Lab exercises (built in)

`SF_sites.csv` defines each tower shifted 125 m E/W/N/S from its as-built
position, at heights of 20/30/35/50 m — 12 designed cases. Set the case in
the notebook's CSV cell (step 4b), re-run, and compare coverage. The v8 rows
extend the same idea to a 28 GHz small-cell layout. The notebook also walks
through a **verification exercise**: a 10 m run over the least-blocked patch
checks the tracer independently of the scene (91.9% of cells with a path;
84.9% coverage at RSRP ≥ −90 dBm).

## A result worth knowing before you build on this

The same layout traced on two different meshes of the same tile gives very
different coverage: **80.5%** (original fused scene, published v7) vs
**16.6%** (evaluation mesh, full tile) at RSRP ≥ −90 dBm. Scene provenance
and mesh detail are first-order variables in ray-traced coverage studies —
report them like RF parameters. The re-run does not revise v7's published
numbers; the wired page states the comparison openly.

## Roadmap — improvements welcome

- Vegetation layer (ITU-R P.833) on the re-run pipeline
- The 28 GHz v8 small-cell trace from the CSV's v8 rows
- A second city tile; additional radio materials beyond ITU concrete
- Re-run on a higher-fidelity / Sionna-ready scene when available
- Classroom materials: worked solutions, instructor notes

Please open an issue or a pull request. Accepted contributions are credited
in the release notes. Versioned releases are deposited to Zenodo for a DOI.

## Data and code availability

- Notebook, `SF_sites.csv`, result JSONs, plots: author's Google Drive,
  view-only links (download sources; the package runs fully local).
  - SF_sites.csv: https://drive.google.com/file/d/1bD1k7IzARGZEmANB1xVUUKYJtr61ohXR/view
  - Full-tile results: https://drive.google.com/file/d/10lLrGeWa5TEtvjBcY9r20AhZUm7JDinl/view
  - Patch-B 10 m results: https://drive.google.com/file/d/1_UkrX1H0aBxQdcJv0VnDMkXCf81tOtDL/view
- City mesh: Vexcel San Francisco 3D evaluation sample — obtain from Vexcel;
  not redistributed here.
- Software: Sionna RT 2.2.0, Mitsuba 3, trimesh, DracoPy (all open-source).

## Licensing

Code (this repo and the notebook's code): **MIT** — see `LICENSE`.
Documentation, `SF_sites.csv`, result data, and figures: **CC BY 4.0**
(attribution to Rao S. Yenamandra). Third-party material (the Vexcel mesh;
open-source components) remains under its owners' terms.

## Citation

See `CITATION.cff`. Please cite the package (and the accompanying paper,
once posted) when you use it in teaching or research.
