# Phishing Website Detection: Feature Elimination for Improved Accuracy

## Overview

This repository contains a machine learning project focused on detecting phishing websites using the UCI Machine Learning Phishing Dataset. The approach involves exploratory data analysis (EDA), feature selection through correlation analysis and elimination of redundant features, and training a Random Forest Classifier to classify URLs as phishing (0) or legitimate (1). By removing highly correlated and redundant features, the model achieves high accuracy while reducing complexity and potential overfitting.

The notebook demonstrates how feature engineering can enhance model performance, achieving **96.07% accuracy** on the test set and **95.09% cross-validation accuracy**.

## Dataset

- **Source**: [UCI Machine Learning Repository - Phishing Websites Dataset](https://archive.ics.uci.edu/dataset/327/phishing+websites)
- **Description**: The dataset consists of 11,055 instances with 30 features derived from URL and website characteristics (e.g., URL length, IP address presence, SSL state). The target variable `Result` is binary: -1 (phishing) or 1 (legitimate).
- **Features Analyzed**:
  - Numerical and categorical features like `having_IP_Address`, `URL_Length`, `SSLfinal_State`, etc.
  - EDA reveals biases, such as erratic URL lengths leaning toward phishing sites.
- **Preprocessing**:
  - Dropped `id` column (negligible utility).
  - Mapped `Result`: -1 → 0 (phishing), 1 → 1 (legitimate).
  - Removed redundant features based on correlation heatmap: `on_mouseover`, `RightClick`, `Iframe`, `double_slash_redirecting`, `Favicon`, `HTTPS_token`.

## Methodology

1. **Exploratory Data Analysis (EDA)**:
   - Loaded dataset using Pandas.
   - Visualized distributions with Seaborn countplots (e.g., `URL_Length` and `having_IP_Address`).
   - Computed and visualized correlation matrix to identify multicollinearity.

2. **Feature Selection**:
   - Used correlation analysis to drop highly correlated features, improving model efficiency and reducing bias.

3. **Model Training**:
   - **Algorithm**: Random Forest Classifier (200 estimators, max depth 10).
   - **Split**: 80/20 train-test split with stratification.
   - **Evaluation Metrics**: Accuracy, Cross-Validation Accuracy, ROC-AUC Score.

4. **Implementation**:
   - Libraries: NumPy, Pandas, Matplotlib, Seaborn, Scikit-learn.

## Results

- **Test Accuracy**: 96.07%
- **Cross-Validation Accuracy**: 95.09% (± 0.81%)
- **ROC-AUC Score**: 0.9584

These results indicate a robust model with strong generalization, outperforming baseline approaches by eliminating redundant features that could introduce noise or bias.

| Metric                  | Value          |
|-------------------------|----------------|
| Test Accuracy           | 96.07%        |
| CV Accuracy (Mean)      | 95.09%        |
| CV Accuracy (Std)       | ±0.81%        |
| ROC-AUC Score           | 0.9584        |

## How to Run

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/phishing-detection-feature-elimination.git
   cd phishing-detection-feature-elimination
