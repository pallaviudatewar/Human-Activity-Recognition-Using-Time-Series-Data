# Human Activity Recognition Using Time Series Data

## Introduction

This project explores the classification of human activities using time series data collected from a Wireless Sensor Network. The AReM dataset comprises seven different types of activities, each represented in its folder containing multiple files. Each file captures six time series corresponding to a particular activity instance, with features named as avg rss12, var rss12, avg rss13, var rss13, vg rss23, and ar rss23.

## Dataset Description

The AReM dataset contains 88 instances, each with 480 consecutive values across six time series. The dataset is publicly available and can be downloaded from [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Activity+Recognition+system+based+on+Multisensor+data+fusion+%28AReM%29).

## Methodology

### Data Partitioning

Datasets 1 and 2 in the 'bending1' and 'bending2' folders, along with datasets 1, 2, and 3 in the other folders, are designated as test data. The remaining datasets are used for training.

### Feature Extraction

Time-domain features are extracted for use in classification, including:
- Minimum
- Maximum
- Mean
- Median
- Standard deviation
- First quartile
- Third quartile

These features can be normalized or used directly, as per the model's requirement.

### Feature Selection

Based on exploratory analysis and domain knowledge, three key time-domain features are chosen for their potential significance in classifying activities.

## Binary Classification Using Logistic Regression

Scatter plots are created for selected features from the training data, highlighting the distinction between 'bending' activities and others. Further experiments include breaking down each time series into two equal lengths and extracting features from these subdivisions to observe any differences in classification outcomes.

### Logistic Regression with Cross-Validation

Logistic regression models are trained with varying lengths of time series subdivisions (l ∈ {1, 2, ..., 20}), and 5-fold cross-validation is used to select the best combination of time series length and the number of features. Stratified cross-validation is employed if necessary to handle class imbalance.

## Results

### Model Performance

The confusion matrix, ROC curve, and AUC are provided for the best logistic regression model on the training data. Parameters and associated p-values for the model are reported.

### Testing on Unseen Data

The chosen classifier is then tested on the test dataset, which is processed similarly to the training set. Comparison of test accuracy with cross-validation accuracy from the training phase is discussed.

### Stability and Class Imbalance

Questions of model stability due to well-separated classes and potential class imbalance are addressed. If imbalance is detected, logistic regression based on case-control sampling is performed, and its results are analyzed.

## Penalized Logistic Regression

The process is repeated using L1-penalized logistic regression, cross-validating over the number of subdivisions and the penalty weight. A comparison is made between this method and variable selection using p-values.

## Multiclass Classification

The test error was reported for the multiclass classification scenario after determining the best number of time series subdivisions (l) through cross-validation. Confusion matrices and ROC curves were also provided where applicable to assess model performance comprehensively.

## Naïve Bayes Classification

The Naïve Bayes classifier was applied using both Gaussian and Multinomial priors. A comparative analysis of these classifiers was conducted to determine which prior is more effective for this particular multiclass classification problem.

## Discussion

### Binary Classification

- **Logistic Regression Models**: Demonstrated capability to distinguish between bending activities and others, with scatter plots showing clear clustering patterns.
- **Time Series Segmentation**: Breaking down time series into shorter segments revealed changes in feature behavior and impacted classification performance.
- **Model Complexity**: Optimal complexity was achieved by balancing the number of features against predictive accuracy through cross-validation.

### Multiclass Classification

- **Multinomial Logistic Regression**: Employed with L1 penalization to classify multiple activity types.
- **Model Evaluation**: Utilized metrics appropriate for multiclass classification to ensure a thorough assessment of model performance.

### Comparative Analysis

- **Model Comparison**: The strengths and limitations of logistic regression with L1 penalization versus Naïve Bayes classifiers were explored.
- **Feature Selection Techniques**: The efficacy of recursive feature elimination and p-value based selection was critically examined.

## Conclusion

The analysis of the AReM dataset has shown that feature engineering and model selection are critical in the classification of human activities from time series data. Both binary and multinomial logistic regression, as well as Naïve Bayes classifiers, have provided valuable insights. This project highlights the importance of preprocessing, feature extraction, and model evaluation in creating robust classification models for time series data.


