# ML_Lab-2547241

Coursework repository of Jupyter/Colab notebooks for a Machine Learning lab course (student registration number 2547241), covering data cleaning/EDA, linear regression, and KNN classification.

## What's here

The repo contains three Colab notebooks (each has an "Open in Colab" badge and was authored/run in Google Colab):

- **`ML_2547241_Lab1&2.ipynb`** — Lab 1 & 2: Data cleaning and exploratory analysis on two datasets, `city_day.csv` (daily air quality index by Indian city) and `crop_production.csv` (state-level crop production).
  - Task 1: initial data profiling (shape, dtypes, missing values, unique values) for both datasets.
  - Task 2: missing-value treatment (column drops, median imputation) with written justification per column.
  - Task 3: harmonizing city→state names and standardizing state name strings so the two datasets can be merged.
  - Task 4: AQI distribution analysis (histograms/boxplots) to assess whether pollution is broadly distributed or concentrated in a few cities.
  - Task 5: outlier handling on AQI using the IQR method and winsorization (capping), with before/after boxplots.
  - Task 6: yearly AQI trend analysis (line plot), identifying most/least polluted years and writing a plain-language response to a hypothetical journalist.
  - Task 7: seasonal (monthly) AQI analysis to check an NGO's claim about Oct–Dec harvest-season pollution.
  - Task 8: merging the two datasets at state level and analyzing AQI vs. crop production correlations.
  - Task 9: a written summary memo synthesizing the findings.

- **`ML_2547241_Lab3.ipynb`** — Lab 3: Simple linear regression, done two ways (scikit-learn's `LinearRegression` and manually-derived OLS formulas), on a `student_survey.qcsv` dataset.
  - Experiment 1: predicting GPA from CIA (internal assessment) percentage.
  - Experiment 2: predicting GPA from attendance percentage.
  - Compares scikit-learn vs. manual-OLS predictions (they match to floating-point precision) and pickles the learned weights (`linear_regression_weights.pkl`, `linear_regression_weights_exp2.pkl`).

- **`ML_2547241_Lab4.ipynb`** — Lab 4: KNN classification on the sklearn Breast Cancer Wisconsin (Diagnostic) dataset, plus a comparison of regression vs. classification evaluation metrics.
  - Feature scaling with `StandardScaler` and justification for why it matters for a distance-based algorithm.
  - Train/test split comparison (80:20, 70:30, 90:10) with a heuristic K = √n (rounded to odd).
  - K-sweep around the heuristic K, decision-boundary visualization via 2D PCA, and 5-fold/10-fold cross-validation to pick a final K (K = 18).
  - Full evaluation of the final model: accuracy, precision, recall, F1, confusion matrix, ROC curve/AUC.
  - A worked comparison between regression metrics (MAE/MSE/RMSE/R², from Lab 3) and classification metrics, plus a set of short-answer analytical questions (why KNN is "lazy", bias-variance tradeoff vs. K, why recall matters more than accuracy for cancer diagnosis, etc.).
  - A stability check re-running the final model across multiple random seeds.

## Tech stack

Python, run in Google Colab / Jupyter notebooks. Libraries used (per the notebooks' imports): `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn` (`LinearRegression`, `KNeighborsClassifier`, `StandardScaler`, `PCA`, `train_test_split`, `cross_val_score`, `KFold`, and the `sklearn.metrics` / `sklearn.datasets` modules), and the standard library `pickle`.

## Setup / running

A `requirements.txt` listing the libraries imported across the notebooks is included. To run the notebooks as-is:

1. Open a notebook directly in Google Colab via the badge link at the top of each `.ipynb` file, or open it locally with Jupyter (`pip install -r requirements.txt`, then `jupyter notebook`).
2. Lab 1&2 and Lab 3 read input data from hardcoded Colab paths (`/content/city_day.csv`, `/content/crop_production.csv`, `/content/student_survey.qcsv`). **These CSV files are not included in this repo** — they must be uploaded to the Colab `/content/` directory (or the paths edited) before the notebooks will run. Lab 4 loads its data directly from `sklearn.datasets.load_breast_cancer()` and needs no external file.

## Status

Work in progress / coursework snapshot:
- All three notebooks contain complete code — no stub functions or `TODO`/`FIXME` markers were found. Lab 3 and Lab 4 are fully executed with saved outputs throughout.
- Lab 1&2 is mostly executed, but the Task 3 (state-name harmonization) and Task 8 (state-level merge/correlation heatmap) cells currently show no saved output: they haven't been re-run since the Jorapokhar city→state mapping fix, which changed which states are included in the merge. The Task 8 write-up's correlation numbers predate that fix and are flagged inline as indicative only until the notebook is re-run end-to-end.
- The repo is also **not runnable standalone**: two of the three notebooks depend on external CSV files that aren't checked in, so reproducing the results elsewhere than the original Colab session requires supplying the missing data files yourself.
- This is a lab-assignment repo (individual experiments with write-ups), not a packaged/deployable project — there's no shared library code, CLI, or app entry point.
