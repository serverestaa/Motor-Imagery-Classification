
# Brain-Computer Interface (BCI) Motor Imagery Classification

This project implements a complete pipeline for processing and classifying EEG data from motor imagery tasks, based on the BCI Competition IV Dataset 2a.

## Overview

The project processes EEG data recorded during motor imagery tasks (imagining moving left hand, right hand, feet, or tongue) and builds machine learning models to classify these mental tasks. The pipeline includes:

1. **Data Exploration**: Analyzing the dataset structure and trial distribution
2. **Preprocessing**: Cleaning EEG signals and preparing them for feature extraction
3. **Feature Extraction**: Generating discriminative features from EEG signals
4. **Classification**: Training and evaluating multiple machine learning models
5. **Evaluation**: Comparing performance across subjects and methods

## Dataset

The project uses the BCI Competition IV Dataset 2a, which contains EEG recordings from 9 subjects performing 4 different motor imagery tasks:
- Class 1: Left hand motor imagery
- Class 2: Right hand motor imagery
- Class 3: Feet motor imagery
- Class 4: Tongue motor imagery

Each subject's data includes:
- 22 EEG channels
- 3 EOG channels
- Training and evaluation sessions
- Event markers for trial timing and class labels

## Project Structure

```
.
├── BCICIV_2a_gdf/           # Raw GDF data files
├── processed_data/          # Preprocessed EEG data
├── feature_data/            # Extracted features
├── models/                  # Trained classification models
├── results/                 # Performance metrics and visualizations
├── BCI.ipynb                # Main Jupyter notebook with all code
└── README.md                # This file
```

## Pipeline Components

### 1. Data Exploration

- Loading and inspecting GDF files
- Analyzing event markers and trial structure
- Visualizing class distribution across subjects
- Exploring trial timing and structure

### 2. Preprocessing

The preprocessing pipeline includes:
- EOG artifact removal using regression
- Bandpass filtering (8-30 Hz) to focus on mu and beta rhythms
- Epoch extraction around cue events
- Removal of trials marked with artifacts
- Spatial filtering preparation

### 3. Feature Extraction

Multiple feature extraction methods are implemented:
- **Time-domain features**: Statistical measures from different time windows
- **ERD/ERS patterns**: Event-related desynchronization/synchronization
- **Band power features**: Power in mu and beta frequency bands
- **Common Spatial Patterns (CSP)**: Spatial filters that maximize variance differences
- **Riemannian geometry features**: Based on covariance matrices
- **Dimensionality reduction**: PCA and LDA applied to combined features

### 4. Classification

The project evaluates several classification algorithms:
- Linear Discriminant Analysis (LDA)
- Support Vector Machines (SVM)
- Random Forests
- Multi-layer Perceptron (MLP)
- Ensemble methods (voting classifier)

Each classifier is optimized using grid search with cross-validation.

### 5. Evaluation

Performance evaluation includes:
- Cross-validation accuracy
- Test set accuracy
- Confusion matrices
- Classification reports (precision, recall, F1-score)
- Comparison across subjects, feature sets, and classifiers

## Usage

### Prerequisites

Required Python packages:
```
mne
numpy
pandas
matplotlib
scikit-learn
pyriemann
scipy
seaborn
joblib
```

### Running the Pipeline

1. **Data Preparation**:
   - Place the GDF files in the `BCICIV_2a_gdf` directory

2. **Execute the Notebook**:
   - Run the cells in `BCI.ipynb` sequentially
   - The notebook will create necessary directories automatically

3. **Examine Results**:
   - Check the `results` directory for performance metrics and visualizations
   - Review the trained models in the `models` directory

## Results Interpretation

The project generates several visualizations to help interpret the results:
- Class distribution plots
- ERD/ERS patterns for different motor imagery tasks
- CSP patterns showing spatial filters
- LDA projections of the feature space
- Confusion matrices for each classifier
- Accuracy comparison across feature sets and classifiers

## Extending the Project

Possible extensions include:
- Online BCI implementation
- Deep learning approaches (CNNs, RNNs)
- Transfer learning between subjects
- Adaptive methods for session-to-session transfer
- Feature selection techniques
- Hyperparameter optimization with more advanced methods

## References

- BCI Competition IV Dataset 2a: http://www.bbci.de/competition/iv/
- MNE-Python: https://mne.tools/
- PyRiemann: https://pyriemann.readthedocs.io/
