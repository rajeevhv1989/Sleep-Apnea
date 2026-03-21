# Multi-Channel Sleep Apnea Detection Framework

![Python](https://img.shields.io/badge/python-3.10+-blue.svg) ![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg) ![License](https://img.shields.io/badge/license-MIT-green.svg)

An automated machine learning and deep learning framework for sleep apnea detection using multi-channel respiratory signals and SpO2, validated on the PhysioNet Apnea-ECG database.

## 🚀 Project Overview
This project implements a robust pipeline for detecting sleep apnea events from 1-minute physiological signal windows. Unlike many existing approaches that rely solely on ECG, this framework leverages:
- **Multi-channel Respiration:** Nasal airflow, Chest (Chest), and Abdomen (ABD) signals.
- **Oxygen Saturation (SpO2):** Capturing clinical desaturation events.
- **ECG Advanced Features:** HRV, Poincaré plots, and EDR.

## ✨ Key Features
- **123-Feature Extraction:** Comprehensive feature set including time-domain, frequency-domain (Welch), Wavelet (db4), and Hjorth parameters.
- **Paradoxical Breathing Detection:** Novel features calculating phase differences between thoracic and abdominal effort.
- **LOSO-CV Validation:** Leave-One-Subject-Out Cross-Validation ensuring zero data leakage and subject-independent generalization.
- **Hybrid Modeling:** Supports traditional ML (Gradient Boosting, Random Forest) and Deep Learning (Improved 1D-CNN, Bi-LSTM).
- **Optimized Pipeline:** Built-in caching system to reduce re-computation time from 2 hours to ~35 minutes.

## 📊 Performance Summary
| Model | Accuracy | Sensitivity | Specificity | AUROC |
| :--- | :--- | :--- | :--- | :--- |
| **Gradient Boosting** | **96.2%** | **95.4%** | **96.8%** | **0.991** |
| **Improved 1D-CNN** | 97.3% | 98.5% | 96.4% | 0.995 |
| **Bi-LSTM** | 94.4% | 98.9% | 90.4% | 0.970 |

*Results based on PhysioNet Apnea-ECG dataset using LOSO-CV evaluation.*

## 🛠️ Installation & Usage

### Requirements
```bash
pip install wfdb imbalanced-learn PyWavelets tensorflow pandas numpy scipy scikit-learn matplotlib seaborn
```

### Running the Analysis
1. Open the notebook in Google Colab.
2. Configure the `Config` class for specific records.
3. Run the pipeline cells. The first run will download data and populate the `/content/cache` directory.
4. Use the `ModelEvaluator` class to generate statistical reports and 95% Confidence Intervals.

## 📁 Repository Structure
- `core_analysis.ipynb`: The main notebook containing the full pipeline.
- `cache/`: (Generated) Local storage for pre-processed features.
- `exported_models/`: Saved weights for the 1D-CNN and Bi-LSTM models.
- `Paper1_Figures/`: Publication-ready plots (ROC curves, Confusion Matrices, Feature Importance).

## 📜 Citation
If you use this code in your research, please cite the associated paper:
> *Rajeev H Venkatesh, et al. (2025). Multi-Channel Respiratory and SpO2 Signal Analysis for Automated Sleep Apnea Detection.*

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
