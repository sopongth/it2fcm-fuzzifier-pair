# Code for "Disentangling the Fuzzifier Pair From Its Type-1 Ingredients in Interval Type-2 Fuzzy C-Means Under Multiclass Imbalance"

S. Phumeechanya and P. Sermwuthisarn, manuscript submitted to *IEEE Access* (2026).

This repository contains the fifty-six Jupyter notebooks that produce every experimental result reported in the
paper and in its supplementary material. Each notebook runs one experiment or analysis and writes its results to a
JSON file and, in most cases, to a plain-text report that prints the same values. Code that only draws figures or
typesets tables is not part of the release: every reported value can be read from the JSON files or computed directly
from them (means, medians and percentages of the stored per-instance values); a few details of figure captions and table
notes are recomputed with the notebooks' functions from the stored instances and settings, as Section S1 of the
supplementary material states. The result files themselves are not
distributed; running the notebooks as described under *Running* writes them.

The number at the start of each file name is the notebook's identifier, not a position in a complete sequence. It names the
notebook's output folder (`results/<id>/`), its result and checkpoint files and its optional environment variables, and the
files fixed before some runs (`plan_48.json`, `plan_56.json`, `predictions_35.json`, `predictions_44.json`,
`predictions_51.json`, `predictions_52.json`, cited in the supplementary material, most with their time stamps and hashes) carry
it as well, so the identifiers are kept. The table below maps each notebook to the sections and tables of the paper and
the supplementary material that report its results.

## 1. Contents

| Notebook | What it computes | Reported in |
|---|---|---|
| `01_decision_identity_synthetic` | Decisions of class-uniform and class-wise reducers against the type-1 decision, on 14,400 synthetic configurations and on test images; the overlap band | Sec. VII-B; Sec. S5; Tables S7, S8 |
| `02_decision_identity_documents` | Two-class FCM and interval memberships on 100 DIBCO document images: decision identity, F-measure, ratio of the Sambuc index of two footprint constructions | Secs. IV, VII-F; Sec. S3; Table S4 |
| `03_screening_controlled_bsds` | Mutual-information ceiling and the gain of a footprint built with a second source, in a controlled setting and on BSDS500 | Secs. IV, V; Sec. S4; Table S5 |
| `04_screening_documents` | The same screening quantity on the document images: ceiling, predicted and realized gain, bound | Secs. IV, V; Sec. S4; Table S6 |
| `05_runs_alternative_reading` | FCM, the type-1 control and the interval algorithm with the alternative reading of the bounds of Hwang and Rhee (2007), eq. (5), on seventeen data sets; best pair per instance of the alternative reading against FCM | Secs. VII-B, VII-C; Secs. S5, S12; Table S19 (incl. Best pair) |
| `06_runs_type1_methods` | FCM, the type-1 control, the Nie-Tan variant and the alternative reading on the main sets and the noise and imbalance sweeps; label-free indices; run times | Sec. VII-G; Table 4; Tables S19, S20 |
| `07_runs_minmax_reading` | The interval algorithm with the bounds read as minimum and maximum, on the instances of 06 | Secs. VII-B, VII-G; Table 4; Secs. S5, S12; Table S20 |
| `08_analysis_main` | Label-tuned and label-free comparisons, claim rule, across-set tests, decomposition of the gain; best-pair comparison (best pair with the mean center exponent, chosen for each instance, against FCM at m = 2) | Secs. VII-B, VII-C, VII-E; Table 4; Fig. S9 (values); Table S19 (Best pair column) |
| `09_equivalence_grid_design` | Hodges-Lehmann estimates, equivalence tests, restricted grids, share of settings at the grid's edge, the per-fuzzifier comparison design | Secs. VII-C, VII-G, IX; Secs. S13, S14; Tables S21, S22, S23 |
| `10_prototypes_further_sets` | Prototype error against the true centers, four further real data sets, convergence of every method | Secs. VII-D, VII-E, VII-G; Tables S24, S25, S43, S44, S109 |
| `11_regime_mechanism` | Share of the largest class kept in one cluster and clusters left empty; the representative instances; decisions on all document images and on three of them; footprint widths on natural images; prototype errors on the five scenarios | Secs. IV, VII-D, VII-E, VII-F; Figs. 2, 3; Figs. S3, S4, S7 (values) |
| `12_fcm_size_variables` | Fuzzy c-means with cluster-size variables (FCMA, FCMA-d) against the other methods, on every main set but DIBCO, the imbalance sweep and the four further sets; the representative Dermatology and Page-blocks instances | Sec. VII-E; Table 5; Table S9; Fig. S8 (values) |
| `13_clusters_initializations` | Type-1 methods with a free number of clusters; ten initializations; the two-grid example of Hwang and Rhee; prototype error of FCMA | Secs. VII-D, VII-E; Tables S26, S27, S28, S29 |
| `14_real_data_protocol` | Clustering 75 % of each class with C, 2C or 3C clusters and recognizing the rest | Sec. S16 |
| `15_few_labels_kernel` | Settings chosen with 2-20 % of the labels; interval type-2 kernel fuzzy c-means against kernel fuzzy c-means | Sec. VII-E; Tables S31, S32 |
| `16_scene_measures_data_sizes` | Alignment ratio and Sambuc index on four synthetic scenes; size of every tabular data set and synthetic instance | Sec. IV; Sec. S3; Tables S3, S30 (except the image and MNIST rows); values of Fig. S1 |
| `17_mixture_indices_mnist` | Gaussian mixtures (four settings); label-free selection by four validity indices; MNIST | Sec. VII-E; Tables S33, S34, S35; MNIST rows of Table S30 |
| `18_balanced_tuned_mixture_grids` | Measures that weight every class equally; Gaussian mixtures with sixteen settings; restricted fuzzifier grids | Secs. VII-E, IX; Table 5; Tables S36, S37, S38 |
| `19_per_set_intervals` | Per-instance differences in ARI of IT2 from FCM and from T1d at the selected settings, label-tuned and label-free, with 95 % t-intervals and claim-rule verdicts, on every data set | Fig. S6 (values) |
| `20_davies_bouldin_selection` | FCM, T1d and IT2 at every setting on every data set but DIBCO; settings chosen without labels by the Davies-Bouldin index, the crisp Xie-Beni index and the silhouette | Sec. VII-E; Table S39 |
| `21_size_insensitive_fcm` | csiFCM and csiFCM-d (cluster-size-insensitive fuzzy c-means) on every main set but DIBCO, the imbalance sweep and the four further sets, against IT2, FCM and T1d | Sec. VII-E; Table 5; Table S40 |
| `22_update_and_fuzzifier_robustness` | Check of the two-bound update (Proposition 2) on 2,000 random configurations; ARI of FCM, T1d and IT2 at every setting (best, median and worst over each grid, share of the IT2 grid above the best type-1 setting, a region and a default of IT2) | Secs. VI, VII-B, VII-E; Secs. S6, S17; Table S41 |
| `23_general_type2_alpha_planes` | A general type-2 variant (triangular fuzzifier, alpha-planes 1/3, 2/3, 1) at the settings of IT2 on the imbalance sweep at ratio 20, Ecoli and New-thyroid, the equal-size controls and the main sets, against FCM, T1d and IT2; its decision with two classes; a check of the iteration limit | Sec. VII-E; Sec. S17; Table S42 |
| `24_further_imbalanced_sets` | Six further UCI sets chosen by a criterion fixed in advance (at least five classes, size ratio at least 10): FCM, T1d, IT2, FCMA and FCMA-d at every setting; label-tuned and silhouette comparisons, grid summaries, the largest class kept and near-empty clusters, and the predictions fixed before the runs | Secs. VII-E, IX; Table 5; Sec. S36; Table S96 |
| `25_further_checks` | Type-1 algorithms and IT2 choosing their number of clusters on the six sets of 24; the iteration limit raised to 3,000 at the selected settings; FCM on a grid of 108 fuzzifiers with the selection optimism of every method; class-balanced measures on the six sets and HCV data in detail; Ecoli with its smallest classes merged or removed; the corrected resampled t-test on every per-set comparison of real data | Secs. VII-C, VII-E, VII-G, IX; Secs. S8, S36; Tables S10, S97, S98 |
| `26_further_baselines` | Fuzzy c-means with multiple fuzzification coefficients (Khang et al. 2020; 108 settings) under the protocol of the paper on every set; semi-supervised fuzzy c-means (Pedrycz and Waletzky 1997) against IT2 with 2-20 % of the labels | Secs. II, VII-E; Table 5; Sec. S20; Tables S49, S50 |
| `27_rkm_it2fl` | Rough k-means with interval type-2 fuzzy local enhancement for imbalanced clusters (Zhang et al. 2020), at its published setting and at 108 settings, under the protocol of the paper on every set | Secs. II, VII-E, IX; Table 5; Sec. S20; Table S51 |
| `28_corrected_tests_holm` | Per-set comparisons by ARI (and by accuracy where the stored records carry it) from the stored records with the claim rule and the corrected resampled t-test; Holm correction across data sets within each comparison family | Sec. IX; Sec. S8 |
| `29_regime_competitors_wide_grid` | Every method (FCM, T1d, IT2-NT, FCMA, FCMA-d, csiFCM, csiFCM-d, MC-FCM, RKM-IT2FL, Gaussian mixtures) on the three regime sweeps at ratio 20 and on Ecoli, Dermatology and HCV data, with balanced accuracy, macro F1, classes found and the recall of the smallest class; csiFCM and Gaussian mixtures on the six sets of 24; IT2 on a wider grid (m1 = 1.01, m2 = 50 and 100) | Secs. VII-E, IX; Table 5; Sec. S19; Tables S45, S46, S47, S48 |
| `30_family_test_rho_sensitivity` | The corrected resampled t-test at three values of its correlation parameter on every per-set comparison; one Friedman family over all methods on the 16 main sets with Holm-corrected post hoc comparisons | Secs. VII-A, IX; Sec. S9; Table S11 |
| `31_update_decomposition_floor_control` | The two-bound update decomposed per cluster and feature at the selected settings (near and far terms, distance of empty prototypes to the midrange); a type-1 control with a floor on the prototype weights (T1f) against IT2, FCM and T1d | Secs. VI, VII-E; Sec. S21; Tables S52, S53 |
| `32_timing_rkm_mnist_heldout_labels` | Run times of five methods measured in one session; RKM-IT2FL near zeta = 1; MNIST with 20 instances; a point-disjoint held-out design on five real sets; settings chosen from 2-20 % of the labels against semi-supervised and seeded fuzzy c-means with the fuzzifier on the grid | Secs. VII-E, VII-G, IX; Sec. S22; Tables S54, S55, S56, S57 |
| `33_stored_result_analyses` | From stored results only: AMI and selection by AMI or balanced accuracy on the imbalanced sets; Holm adjustment within sets; across-set Wilcoxon tests with Hodges-Lehmann intervals on the regime and pre-specified sets; the correlation parameter implied by the subsample overlap; equivalence within 2 ARI points; ties in the selection from few labels | Secs. VII-A, VII-E, IX; Sec. S23; Tables S58, S59, S60, S61, S62 |
| `34_finer_imbalance_sweep` | A finer synthetic sweep (3-10 classes, size ratio 2-50, two or ten features, two separations) with FCM, T1d, IT2, csiFCM-d, T1f, a Gaussian mixture and k-means | Sec. VII-E; Sec. S24; Tables S63, S64 |
| `35_four_further_imbalanced_sets` | Four further real sets meeting the filter of Sec. S36 (Wine Quality white, Covertype, Avila, Anuran Calls), with the prediction for each fixed from FCM before any interval run | Secs. VII-E, IX; Sec. S37; Table S99 |
| `36_robustness_checks` | HCV data under four preprocessings; the point-disjoint design for the mixture, csiFCM-d and T1f; the mixture and k-means on MNIST; k-means on the imbalanced sets; run times on the imbalanced sets | Secs. VII-E, VII-G, IX; Sec. S25; Tables S65, S66 |
| `37_mechanism_controls` | On the regime sets (sweeps at ratio 20 with three, five and eight classes, Ecoli, HCV data, Dermatology, Covertype, Anuran Calls): IT2 against FCM, T1d, IT2-NT, the Nie-Tan update with a floor on its weights (NT+floor), the floored type-1 update T1f and a type-1 update with a constant asymmetry (EXP, two expectiles of one membership map), each control against its base, and the share of the gain of IT2 over T1d that each reproduces; IT2 after random rotations of the features; convergence at the selected settings and distance from the hard-flat limit | Sec. S26; Tables S67, S68, S69 |
| `37b_mechanism_controls_covertype` | Part A of 37 on Covertype alone, with the data loaded from the UCI archive when no cached copy of 35 is present (used for the Covertype rows of 37) | Sec. S26; Tables S67, S68, S69 |
| `38_stored_budget_recall_silhouette` | From stored results only: across-set tests over the sets chosen in advance; each method selected from as many settings as its competitor has; recall of every class; selection by the silhouette with the corrected test | Sec. S27; Tables S70, S71, S72, S73 |
| `39_controls_on_all_sets_mixture_preprocessing_nongaussian` | T1f and EXP on the main sets; the mixture on a wider grid and with BIC; Ecoli and Covertype under other preprocessings; the finer sweep with non-Gaussian classes | Table 5 (GMM-w. column); Sec. S28; Tables S74, S75, S76, S77 |
| `40_point_disjoint_all_real_sets` | A point-disjoint held-out design (five stratified halvings, four subsamples per half) on the 25 real sets used before the prospective suite: IT2 against FCM, T1d, T1f, csiFCM-d and the Gaussian mixture, tested by the combined 5x2cv F test and the corrected resampled t-test with rho = 1; across-set Wilcoxon and sign tests | Table 3; Sec. S31; Table S83 |
| `41_controls_shuttle_and_point_disjoint` | The type-1 controls (T1f, EXP, IT2-NT, NT+floor) on Shuttle, and T1f and EXP in the point-disjoint design on Shuttle, HCV data, Ecoli and Dermatology | Sec. S31; Table S84 |
| `42_calibration_and_stored_reanalysis` | A/A calibration of the per-set tests (each method against itself from other seeds); from stored results: other selections and measures, one correlation for the corrected test, across-set tests with leave-one-set-out | Sec. S10; Tables S12, S13 |
| `43_baseline_panel_clusters_and_label_baselines` | A panel of 13 methods with points disjoint (k-means, Ward, spectral, HDBSCAN, DP-GMM, GMM-wide, EXP and the methods of 40) with a confirmatory family; the number of clusters; seeded k-means and PCKMeans | Table 3 (GMM-wide column, regime sets); Sec. S29; Tables S78, S79, S80 |
| `44_keel_prospective_suite` | 19 KEEL multi-class sets and an imbalanced 20 Newsgroups subset, predictions written from FCM before any interval run (`predictions_44.json`, time stamp and hash), then every method with points disjoint | Table 7; Sec. S38; Tables S100, S101 |
| `45_fixed_points_runtime_and_random_search` | Fixed points and basins; the hard-flat limit; the coincident fixed point; run time on Covertype; random-search tuning; the implementation check of the weight floor | Secs. VI, VII-G; Sec. S43; Tables S110, S111, S112, S113, S114, S115 |
| `48_test_calibration_further_competitors_and_references` | An enlarged A/A calibration with the rule for the primary per-set test written before the runs (`plan_48.json`); further competitors with points disjoint; equilibrium k-means and EM-IFCM, also selected by the IMI index; reference partitions and the recall of every class | Sec. S11; Tables S14, S15, S16, S17 |
| `49_ten_initializations_point_disjoint` | The point-disjoint design of notebook 40 with eight further k-means++ initializations for FCM, T1d, IT2, T1f and GMM-wide on the 13 regime sets and Dermatology, means over ten; per-set tests, the primary family with Holm and Benjamini-Hochberg, across-set tests and the spread of ARI between initializations | Table 6 (ten initializations); Sec. S32; Table S85 |
| `50_per_split_tests_families_and_coincident_point` | From the stored point-disjoint runs: the ten held-out differences of every primary comparison with the F test, the corrected test and an exact sign-flip test; the primary family with Holm and Benjamini-Hochberg, also with csiFCM-d and with every competitor added; the coincident fixed point without the weight floor | Secs. S11, S43; Tables S18, S112 |
| `51_natural_images_bsds500` | Color segmentation of the BSDS500 test images: predictions written from FCM before any other method (`predictions_51.json`, time stamp and hash), then FCM, T1d, IT2, T1f, GMM-wide and k-means with settings selected on one half of the images and scored on the other; ARI, balanced accuracy and probabilistic Rand index; label maps (`maps_51.npz`) | Fig. 4; Sec. S40; Table S105 |
| `52_prediction_rule_checks_and_median_reference` | An FCM twin from other initializations on the natural images and the KEEL suite (A/A check of the prediction rule, interaction between predicted groups, split-level tests within groups); variation of information and segmentation covering at the selected settings; the parts of the 5x2cv F statistic and single runs with ten initializations; BSDS500 against the human segmentation of median granularity with predictions written first (`predictions_52.json`, time stamp and hash) | Secs. S32, S39; Tables S102, S103, S104 |
| `53_hdbscan_tuning_and_equal_budgets` | HDBSCAN tuned over minimum cluster size and minimum number of samples in the point-disjoint design, with the number of clusters found; every method of the panel tuned over 4 or 24 randomly drawn settings and over its full grid (mean ranks, Friedman test, IT2 against each method across sets) | Sec. S30; Tables S81, S82 |
| `54_further_checks_twin_ami_gmmwide` | The FCM twin check of the prediction rule with the median-granularity image reference; the 52 tests of the primary family rescored by adjusted mutual information (settings selected by AMI or by ARI) with Holm's correction; GMM-wide in the point-disjoint design on the ten main sets on which it had not been run | Table 3 (GMM-wide column, main sets); Table 6 (AMI); Sec. S33; Tables S86, S87, S88 |
| `55_reanalyses_type1_family_image_groups` | Re-analyses of stored runs: the point-disjoint family of 52 tests under the 5x2cv F test, the corrected test and a t-test on the halving means (two and ten initializations); T1f and EXP pooled into one type-1 control family with intervals, equivalence tests and the share of the gain reproduced; natural-image groups defined by the reference alone; the share of points in the overlap band and in the set where the reducer of Hwang and Rhee can act | Table 6 (ten initializations); Sec. S34; Tables S89, S90, S91 |
| `56_ten_halvings_test_size_band_transfer` | Ten halvings in the point-disjoint design with one per-set test declared before the runs (t-test on the halving means, Holm over 52 tests); the size of the three per-set tests (A/A copies, bootstrap, simulation); the band and the set of the reducer of Hwang and Rhee at the selected settings, with convergence; the two squares of Hwang and Rhee with nine points per cluster; Ecoli with five classes; settings carried over from the other regime sets; the primary family at a common budget | Secs. V, VII-A, VII-C, VII-E, VII-G, VIII; Table 6; Sec. S35; Tables S92, S93, S94, S95 |
| `57_all_bsds_images_spatial_pair` | Every BSDS500 test image (coarsest reference, at most 12 clusters) with ARI, balanced accuracy, PRI, variation of information and segmentation covering; FCM_S1, its decoupled type-1 version and IT2 with the same spatial term | Sec. VII-F; Sec. S41; Tables S106, S107, S108 |

The settings selected in the label-tuned comparisons of Table 4, the imbalance sweep at ratio 20 and the four further sets (Section S6) are written by 08 and 10, those of FCMA and FCMA-d (Table S9) by 12. Fig. 1 of the paper is a diagram and Figs. S2 and S5 are drawn from the closed forms in the paper; none needs code. Where a
figure is listed, the notebook writes the values the figure plots (per-instance differences, decisions, widths), not the
drawing. Paper and supplement number their tables, figures and sections separately: the paper has Tables 1-8, Figs. 1-4 and Algorithms 1 and 2, the supplement Tables S1-S115, Figs. S1-S9 and Sections S1-S43. Fig. 2 of the paper and Figs. S3 and S4 show document and natural images with the memberships, decisions and widths that 02 and 11 compute.

Each notebook begins with a markdown cell that states what it computes, which inputs it reads, which files it writes
and which options restrict it to a part of the work. Comments in the code are kept to one line at the top of each cell. The code is organized in a few cells: setup (folders, data loading, the clustering algorithms), the runs,
the analysis, and a final cell that prints the report and writes the files.

**Names used in the code.** `FCM` fuzzy c-means; `T1dec` the type-1 control T1d; `IT2FCM-mm` the interval algorithm
with the bounds read as minimum and maximum (IT2 in the paper); `IT2FCM` the alternative reading (IT2p); `IT2FCM-NT`
the Nie-Tan variant (IT2-NT); `FCMA`, `FCMA-d` fuzzy c-means with cluster-size variables; `KFCM`, `KFCM-d`, `IT2-K`
kernel fuzzy c-means and its interval type-2 version; `csiFCM`, `csiFCM-d` cluster-size-insensitive fuzzy c-means; `GMM`
Gaussian mixtures; `GT2` the general type-2 variant; `MCFCM` (MC-FCM in the paper) fuzzy c-means with multiple fuzzification coefficients;
`ssFCM` semi-supervised fuzzy c-means; `GMMX` GMM-wide; `NT`, `NTF` IT2-NT and NT+floor; `EKM` equilibrium k-means; `EMIFCM` (EM-IFCM in the paper) imbalanced FCM with edge modification; `RKM` (RKM-IT2FL in the paper) rough k-means with interval type-2 fuzzy local enhancement. Fields
ending in `_pair` and `_power` refer to the fuzzifier-pair footprint and to the power construction. Data sets are
named by short lower-case keys (`iris`, `wdbc`, `ecoli`, `page_blocks`, `hcv`, `shuttle`, …) and the synthetic
instances by their scenario and parameter (`imb_C3_r20` is the imbalance sweep with three classes at size ratio 20).

## 2. Requirements

Python 3.11 or later and the packages in `requirements.txt`:

```
pip install -r requirements.txt
```

The notebooks were run on Google Colab (CPU runtime) and tested locally with Python 3.12, NumPy 2.4, SciPy 1.17,
pandas 3.0, scikit-learn 1.8, scikit-image 0.26, Pillow 12 and xlrd 2. No GPU is used; the code is NumPy throughout.
`git` must be on the path for the notebooks that fetch the image collections (02-07, 11, 51, 52, 54, 55 and 57), and
`gzip` for unpacking Page-blocks and Shuttle (10-32 and 34-57). Internet access is needed on the first run of each notebook that downloads data
(Section 5).

## 3. Running

### On Google Colab

1. Open https://colab.research.google.com, choose *File > Upload notebook* and upload one notebook.
2. Choose *Runtime > Run all*. The notebook downloads its data, runs, prints its report and writes its files to
   `results/<number>/` in the session's working directory. Every package it needs is part of the Colab image, except
   `xlrd` (it reads the Excel file of the Cardiotocography set), which 24-27, 29, 31, 32 and 34-57 install themselves if it is missing, and `common-datasets` (the KEEL files), which 44, 52, 54 and 55 install themselves.
3. Keep the results between sessions, because later notebooks read them: mount Google Drive and set the results
   folder in a cell inserted at the top of the notebook, before the first code cell:

   ```python
   from google.colab import drive; drive.mount("/content/drive")
   import os; os.environ["RESULTS_DIR"] = "/content/drive/MyDrive/it2fcm_results"
   ```

   Every notebook then reads and writes under that folder, and the notebooks that need the output of earlier ones
   find it there without further settings.
4. Run the notebooks in the order of Section 4. A notebook that stops (for example after a disconnection) can be run
   again from the top; the notebooks with many runs save a checkpoint after every instance and resume from it.

### Locally

```
git clone https://github.com/sopongth/it2fcm-fuzzifier-pair.git
cd it2fcm-fuzzifier-pair
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
export RESULTS_DIR=$PWD/results
jupyter nbconvert --to notebook --execute --ExecutePreprocessor.timeout=-1 \
    notebooks/01_decision_identity_synthetic.ipynb --output-dir executed
```

`--execute` runs the notebook and writes an executed copy (with its printed report) to `executed/`; the result files
go to `$RESULTS_DIR/01/`. Running the notebooks in Jupyter Lab (`jupyter lab`, open a notebook, *Run All Cells*) is
equivalent. A notebook can also be exported to a script (`jupyter nbconvert --to script`) and run with `python`;
the code does not depend on the notebook environment.

### Where the files go

Every notebook writes to `RESULTS_DIR/<number>/` (`RESULTS_DIR` defaults to `./results`, relative to the working
directory):

| File | Content |
|---|---|
| `results_<number>.json` | every computed value, keyed by data set, method and setting (per-instance values, medians, test statistics and p-values, selected settings) |
| `results_<number>_report.txt` | the report printed at the end of the notebook (all notebooks except 01, 02 and 11, which print the report in the notebook only; 02 also writes `dibco_rows.json`, 03 the JSON files of its stages, 17 the MNIST projection `mnist_pca20.npz`); most notebooks also keep a time-stamped copy of the report under `reports/` |
| `*.pkl` | checkpoints of the long runs, one per data set (`runs06_iris.pkl`, `db20_ecoli.pkl`, …): the per-setting records that later notebooks read |
| `data/` | the downloaded tables (10 and the notebooks that download UCI data) |
| `dibco_all/`, `bsds/` | the cloned image collections (DIBCO by 02, 04-07 and 11; BSDS500 by 03, 11, 51, 52, 54, 55 and 57); each notebook clones its own copy into its output folder unless `DIBCO_ROOT` or `BSDS_ROOT` points to an existing one, so set them to share a copy |

The environment variables, all optional:

| Variable | Meaning | Default |
|---|---|---|
| `RESULTS_DIR` | root of all output folders | `results` |
| `DIR_06`, `DIR_07`, `DIR_10`, `DIR_12`, `DIR_15`, `DIR_20`, `DIR_22`, `DIR_24`, `DIR_25`, `DIR_26`, `DIR_27` | folder of that notebook's output, when it is kept elsewhere | `RESULTS_DIR/<number>` |
| `J08`, `J10`, `J12`, `J21`, `J23`, `J26`, `J27` | the files `results_<number>.json` of those notebooks | `RESULTS_DIR/<number>/results_<number>.json` |
| `DIBCO_ROOT`, `BSDS_ROOT` | an existing clone of the DIBCO collection or of BSDS500 | cloned into the notebook's output folder (on Colab into `/content`) |
| `SETS22`, `SETS23`, `SETS24`, `SETS25`, `SETS25B`, `SETS25C`, `SETS26`, `SETS26A`, `SETS26B`, `SETS27`, `SETS27A`, `SETS28`, `SETS29A`-`SETS29C`, `SETS30`, `SETS31A`, `SETS31B`, `SETS32A`, `SETS32B`, `SETS32D`, `SETS32E` | a comma-separated list of data-set keys that restricts the corresponding notebook (or part of it) to those sets, for a partial run; `SETS24` also restricts the six-set parts of 25-32 | all sets of that notebook |
| `SETS33`-`SETS41D`, `FAMS29A`, `FAMS34`-`FAMS41D`, `PARTS39` | the data sets, method families or parts of 29 and 33-41, for a partial run | all |
| `N_MN32`, `SKIP32C` | the number of MNIST instances of 32; set `SKIP32C=1` to skip the MNIST part of 32 | 20; not skipped |
| `N_INST37`, `N_INST39C`, `N_INST41`, `N_ROT37`, `FAMS37B`, `R40`, `S40`, `R41`, `S41`, `N_DRAW38` | fewer instances, rotations, halvings, subsamples or random draws than the defaults of 37-41 (for a quick check) | the values of the paper |
| `EPS_T1F`, `EPS_T1F37`, `EPS_T1F40`, `EPS_T1F41`, `EPS_T1F4X`, `EXP_C` | floor multipliers of T1f and NT+floor, and the asymmetry constants of EXP | `0.5,1,2` in 37-57 (`1` in 34-36 and in part E of 39); `1,4,16` |
| `N_JOBS` | parallel processes of 34-37b, 39-45 and 48-57 | all cores |
| `DIR_29`, `DIR_35`, `J30`, `J35` | output folders and result files of 29 and 35, when kept elsewhere | `RESULTS_DIR/<number>` |

Notebooks 11-21 also read `DATA_10` (the data folder of 10), 33, 36 and 39 read `DIR_32` and `DIR_37`, and notebooks 34-57 read further optional variables of the same kinds (data sets, parts, families, numbers of halvings, images or clusters, such as `SETS56`, `PARTS57`, `R56`, `CMAX57`, `ALPHA57`); each is listed with its default in the notebook's first cell. Every other setting of the experiments is fixed in the code (Section 6).

## 4. Order

Notebooks 01-06, 16, 24, 34, 35, 44 and 51 are independent. The others read the output of earlier ones (each notebook's header lists
its inputs):

| Notebook | Needs the output of |
|---|---|
| 07 | 06 |
| 08, 09 | 06, 07 |
| 10 | none (06, 07 optional, for a reproduction check) |
| 11 | 08, 10 |
| 12, 21 | 06, 07, 08, 10 |
| 13 | 06, 07, 08, 10, 12 |
| 14, 15 | 06, 07, 08, 10 |
| 17, 18 | 06, 07, 08, 10, 15 |
| 19, 20 | 06, 07, 08, 10 |
| 22 | 20 (otherwise it recomputes the runs), 10 for the four further sets |
| 23 | 20 or 22, 10 for New-thyroid |
| 24 | none |
| 25 | 06, 07, 10, 20 (or 22), 24 |
| 26 | 06, 07, 10, 15, 20 (or 22), 24 |
| 27 | 06, 07, 10, 20 (or 22), 24 |
| 28 | 06, 07, 10, 20 (or 22), 24, 25 (no clustering runs) |
| 29 | 06, 07, 10, 12, 15, 20 (or 22), 24 |
| 30 | 06, 07, 10, 12, 20 (or 22), 24, 25, and the result files of 08, 12, 21, 23, 26, 27 (no clustering runs) |
| 31 | 06, 07, 10, 20 (or 22), 24 |
| 32 | 06, 07, 10, 15, 20 (or 22), 24, 26, 27 |
| 33 | 24, 29, 30, 32 (no clustering runs) |
| 34 | none |
| 35 | none |
| 36 | 10, 24, 29, 32 |
| 37 | 10, 35 (if present) |
| 38 | 24, 29, 30, 35 (no clustering runs) |
| 39 | 10 and 37 (if present) |
| 37b | 10, 35 (if present) |
| 40 | 10, 35 (if present) |
| 41 | 10, 35 (if present) |
| 42 | 29, 30, 40 |
| 43 | 40 |
| 44 | none (data downloaded) |
| 45 | 37, 37b, 40 |
| 48 | 40, 42, 43 |
| 49 | 40, 43 |
| 50 | 40, 43 |
| 51 | none (data downloaded) |
| 52 | 40, 43, 44, 49, 51 |
| 53 | 40, 43 |
| 54 | 40, 43, 52 |
| 55 | 40, 43, 51, 52, 54 |
| 56 | 40, 42, 43, 48 |
| 57 | 51 |

Running the notebooks in the order of their identifiers (the order of the table in Section 1) satisfies every dependency. Most notebooks check their inputs in their
first cells and stop with a message when one is missing (17, 18 and 23 stop when they open a missing checkpoint), or, where the header says "if present", skip the corresponding check.

The notebooks that run the clustering methods over many settings process one data set after another, print a line per
data set and save a checkpoint after every instance, so a run that stops can be continued from the checkpoint.

## 5. Data

No data are distributed with the code. The notebooks download what they need on first use and cache the tables in
their output folders; notebooks 12-15, 17, 18 and 20-32 read the four further sets from the data folder of 10 (`DIR_10/data`) and skip a set
whose file is absent; the image collections are cloned by each notebook that uses them unless `DIBCO_ROOT` and `BSDS_ROOT` point to a copy; and
scikit-learn caches MNIST in its own data folder. The DIBCO notebooks take every `*DIBCO*_source.*` image in the cloned
collection (100 images, eight editions, at the time of the runs; Table S4 lists the count per edition). Within a row, a
notebook may use only some of the sets:

| Data | Source | Terms | Used by |
|---|---|---|---|
| Iris, Wine, WDBC (UCI) | bundled with scikit-learn | CC BY 4.0 (UCI) | 05-32, 34-37b, 39-45, 48-57 |
| WBC, Sonar, Seeds, Glass, Ionosphere, Banknote, Ecoli (UCI) | GitHub mirror `jbrownlee/Datasets` | CC BY 4.0 (UCI) | 05-08, 10-32, 34-37b, 39-45, 48-57 |
| Pima Indians Diabetes | GitHub mirror `jbrownlee/Datasets` | formerly distributed through UCI, no longer in its catalog; original owner NIDDK | 05-08, 10-32, 34-37b, 39-45, 48-57 |
| Dermatology, Yeast, Page-blocks (UCI) | UCI Machine Learning Repository, with OpenML as fallback | CC BY 4.0 (UCI) | 10-32, 34-37b, 39-45, 48-57 (downloaded by the notebook or read from the data folder of 10, as its header states) |
| New-thyroid (UCI) | GitHub mirror `jbrownlee/Datasets`, then the UCI Machine Learning Repository, then OpenML | CC BY 4.0 (UCI) | 10-32, 34-37b, 39-45, 48-57 (downloaded by the notebook or read from the data folder of 10, as its header states) |
| Zoo, HCV data, Wine Quality, Steel Plates Faults, Cardiotocography, Statlog Shuttle (UCI) | UCI Machine Learning Repository (Cardiotocography with OpenML as fallback) | CC BY 4.0 (UCI) | 24-27, 29, 31, 32, 34-37b, 39-45, 48-57 |
| Wine Quality (white), Covertype, Avila, Anuran Calls (UCI) | UCI Machine Learning Repository (Covertype through scikit-learn's `fetch_covtype`, with the UCI archive as fallback) | CC BY 4.0 (UCI) | 35, 37, 37b, 39-45, 48-57 (they read the cached copy of 35 when present) |
| KEEL multi-class sets | the `common-datasets` Python package (KEEL collection) | terms of the KEEL repository and of the original sources; cited in the paper | 44, 52, 54, 55 |
| 20 Newsgroups (six-class imbalanced subset) | scikit-learn (`fetch_20newsgroups`) | distributed for research by its authors; cited in the paper | 44 |
| DIBCO 2009-2018 document images | GitHub collection `RichSu95/Document_Binarization_Collection` (about 1 GB) | no license stated on the contest pages; used for research only | 02, 04-07, 11 |
| BSDS500 | GitHub repository `BIDS/BSDS500` (about 0.4 GB) | noncommercial research and educational use (providers' terms) | 03, 11, 51, 52, 54, 55, 57 |
| MNIST | OpenML (`mnist_784`) | CC BY-SA 3.0 | 17, 32, 36 |
| Test images | bundled with scikit-image | CC0 (camera, coffee, chelsea); public domain (astronaut, NASA) | 01 |

Each data set remains subject to the terms of its providers; the creators and DOIs of the UCI sets are listed in
Section S6 of the supplementary material. The synthetic data are generated by the notebooks. Preprocessing
(standardization of every feature; the class coding and feature removals of Section S6; for the KEEL and text sets, the steps listed in the header of 44) is done in the code.

## 6. Reproducing the reported values

- **Seeds.** Every random quantity has a fixed seed: instances of real data sets `3000 + i`, synthetic scenarios
  `1000 + i`, noise sweep `6000 + i`, imbalance sweep `7000 + i`, k-means++ initializations `10000 (q + 1) + i`
  (instance `i`, initialization `q`), silhouette subsample `8000 + i`, DIBCO pixel samples `5000 + i` (image `i`), label draws
  `9000 + 100 i + j` (draw `j`), MNIST instances `11000 + 100 i + b` (size ratio `b`), MNIST principal components `0`,
  DIBCO halves `7`, bootstrap resamples of the Hodges-Lehmann intervals `35`, Gaussian mixtures the seed of their
  initialization; checks of the theory `1000 C + 100 M + k` (classes `C`, dimension `M`, prototype set `k`), check of the two-bound update `0`, test-image
  prototypes `0` and reducer weights `7`, scenes `0`-`7`; screening on the document images `1000 + i` (image `i`), BSDS500 pixel
  pools `3` and bootstrap `19`; the sweeps of 34 and 39 the seeds set in their code; random rotations `37000 + 1000 r + i` (rotation `r`); point-disjoint halvings `40000 + r` (halving `r`) and their subsamples `3000 + 1000 r + 100 h + i` (half `h`); the random budget draws of 38 the seed set in its code.
- **Settings.** Fuzzifier grid {1.05, 1.1, 1.3, 1.5, 2, 3, 5, 10, 20} (seven values {1.05, 1.5, 2, 3, 5, 10, 20} for the four further
  sets, the sets chosen in advance, most regime sets of the point-disjoint design, the KEEL suite, the natural images, the kernel check and MNIST); center exponent the smaller, the larger or the mean of the pair; stopping tolerance 1e-6 on the
  prototypes, at most 300 iterations; two initializations per instance (10 in two checks); m = 4 is added to the grid for the example of Hwang and Rhee.
- **Selection and statistics.** Label-tuned selection chooses the setting on one half of the instances and evaluates
  it on the other; label-free selection uses the silhouette (or another validity index where stated). With overlapping subsamples a difference is
  reported as better or worse only when a t-test and a Wilcoxon signed-rank test give p < 0.05 on both halves (the claim
  rule); on real data the corrected resampled t-test of Nadeau and Bengio is reported as well (25 onward), with rho = f/(1 - f) (3 for 75 % subsamples, 0.43 for Page-blocks), the value the paper uses; notebooks 25 onward also report rho = n_test/n_train = 1/3 (stored under the key `rho_paper` in their code and result files), and rho = 1 is used in the point-disjoint design of 40 and of the notebooks that reuse it, which also uses the combined 5x2cv F test of Alpaydin.
- **Controls.** T1f floors the prototype weights at varpi C^(-m_b) with varpi in {0.5, 1, 2} (only varpi = 1 in 34-36 and in part E of 39; environment variables `EPS_T1F*`); EXP gives the points beyond each end the weight (1 + kappa) l with kappa in {1, 4, 16} (`EXP_C`); NT+floor applies the floor of T1f to the Nie-Tan weights. The paper writes these constants as varpi and kappa.
- **Finding a reported value.** The column *Reported in* of Section 1 gives the notebook; its text report lists the
  values in the order of the corresponding table, with the data sets under the keys given above, and the JSON file holds
  the same values with their per-instance components. A table entry such as "+12.2 (better)" is the mean of the
  per-instance differences in the JSON file (averaged over the two halves), times 100, together with the verdict of the claim rule stored next to it.
- **Numerical floor.** The prototype updates divide by a cluster's total weight, floored at 1e-12 (`EPS`). At weight
  exponents of 10 or more this total can fall below the floor, and the prototype then differs from the one of exact
  arithmetic. The reported values use the updates as implemented; notebook 45 (part F, function `fit_scaled`) gives the
  same updates with each cluster's weights rescaled by their largest value, which leaves the prototypes unchanged in exact
  arithmetic, and reports which values and verdicts change (Table S115).
- **Platform.** The reported values were produced on Google Colab. The computations are deterministic for a given
  platform, but a different processor or library version can resolve a few near ties in the iterations differently,
  which may change some values in the last digit or a small number of individual runs.

## 7. License

The code is released under the MIT License (`LICENSE`). It depends only on NumPy, SciPy, pandas, scikit-learn,
scikit-image, xlrd, joblib and common-datasets (BSD or MIT licenses) and Pillow (MIT-CMU license), all of which permit this use; none of their code is
copied here. All fuzzy and type-2 clustering algorithms, including the baselines of other authors (FCMA, csiFCM, MC-FCM, ssFCM,
RKM-IT2FL, the general type-2 variant and the kernel variant), are our own implementations written from the cited
papers; no third-party algorithm code is included. k-means, Ward linkage, spectral clustering, HDBSCAN and the mixtures are those of scikit-learn. The data sets are not covered by this license (Section 5).

## 8. Citation

Please cite the paper (see `CITATION.cff`); the full reference will be added on publication.
