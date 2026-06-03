# AI-Driven Recruitment Optimization Pipeline

## Overview

This project presents an end-to-end machine learning solution designed to improve recruitment efficiency through intelligent candidate screening and ranking. The goal is to help organizations reduce hiring time, improve candidate selection quality, minimize recruitment costs, and support fair hiring practices through data-driven decision-making.

The solution was developed as part of the BAN 6440 Final Project and demonstrates how machine learning, MLOps, and cloud interoperability can be combined to create a scalable recruitment optimization platform.

---

## Business Problem

Recruitment teams often spend significant time manually reviewing large volumes of applications. This process creates several challenges:

* Long hiring cycles
* High operational costs
* Inconsistent candidate evaluations
* Increased risk of unconscious bias
* Candidate dropout due to delayed responses

This project introduces an AI-powered recruitment pipeline that acts as a decision-support system by automatically classifying applicants into:

* Fast-Track to Interview
* Manual HR Review
* Archive

The objective is not to replace human recruiters but to enhance their decision-making process with predictive analytics.

---

## Project Objectives

The system was designed to achieve the following goals:

* Reduce average hiring time from 45 days to under 14 days
* Improve identification of qualified candidates
* Minimize recruitment costs
* Maintain compliance with fairness and privacy regulations
* Provide scalable deployment architecture for enterprise environments

---

## Dataset

The dataset contains historical recruitment records for approximately 1,500 candidates.

### Features

| Feature             | Description                         |
| ------------------- | ----------------------------------- |
| Age                 | Candidate age                       |
| Gender              | Candidate gender                    |
| EducationLevel      | Academic qualification level        |
| ExperienceYears     | Years of professional experience    |
| PreviousCompanies   | Number of previous employers        |
| DistanceFromCompany | Candidate commute distance          |
| InterviewScore      | Interview evaluation score          |
| SkillScore          | Technical assessment score          |
| PersonalityScore    | Psychometric assessment score       |
| RecruitmentStrategy | Recruitment sourcing channel        |
| HiringDecision      | Target variable (Hired / Not Hired) |

---

## Data Preparation

A comprehensive data quality pipeline was implemented to improve model reliability.

### Data Cleaning Steps

* Missing numerical values imputed using median values
* Missing categorical values replaced using mode or "Unknown"
* Outliers detected using the Interquartile Range (IQR) method
* Winsorization applied to extreme observations
* Feature scaling performed using StandardScaler
* One-hot encoding applied to categorical variables
* Data leakage checks performed before model training

---

## Machine Learning Models Evaluated

Three classification algorithms were benchmarked:

### Logistic Regression

* Interpretable baseline model
* Low computational complexity

### Random Forest Classifier

* Handles nonlinear relationships effectively
* Resistant to overfitting
* Provides feature importance analysis

### Gradient Boosting (XGBoost / LightGBM)

* Captures complex interactions
* Strong predictive performance

---

## Best Performing Model

### Random Forest Classifier

The Random Forest model was selected as the champion model after cross-validation testing.

**Model Configuration**

* Estimators: 150
* Max Depth: 8
* Balanced Class Weights
* 5-Fold Stratified Cross Validation

---

## Model Performance

| Metric    | Score |
| --------- | ----- |
| AUC       | 0.882 |
| Accuracy  | 84.5% |
| Precision | 78.1% |
| Recall    | 73.4% |
| F1 Score  | 75.7% |

These results demonstrate strong predictive capability while maintaining balanced performance across classes.

---

## Feature Importance

The model identified the following features as the strongest predictors of hiring outcomes:

1. InterviewScore
2. SkillScore
3. PersonalityScore
4. ExperienceYears

Protected attributes such as Age and Gender showed minimal predictive influence, supporting fairness objectives.

---

## Enterprise Architecture

The solution follows a cloud-native MLOps architecture.

### Data Layer

**Google BigQuery**

* Centralized storage for recruitment records
* High-performance analytics

### Processing Layer

**Databricks + Apache Spark**

* Data transformation
* Feature engineering
* Model training

### Experiment Tracking

**MLflow**

* Model versioning
* Hyperparameter tracking
* Reproducibility and governance

### Deployment Layer

**Azure Kubernetes Service (AKS)**

* Containerized model serving
* Dynamic scaling
* High availability

### Generative AI Extension

**OpenAI GPT-4o**

* Generates personalized candidate feedback
* Supports HR communication workflows

---

## MLOps Workflow

1. Candidate data enters the system
2. Data validation and preprocessing occur
3. Features are engineered and transformed
4. Models are trained and evaluated
5. Best model is registered in MLflow
6. Model is deployed to AKS
7. Candidates are automatically classified
8. GPT-generated feedback is produced when required

---

## Fairness and Governance

The project incorporates responsible AI practices.

### Fairness Controls

* Four-Fifths Rule compliance
* Demographic parity monitoring
* Gender impact ratio: 0.96

### Privacy Controls

* GDPR compliance
* CCPA compliance
* Candidate anonymization
* Data minimization principles

### Model Monitoring

Population Stability Index (PSI) is used to monitor model drift.

| PSI Score   | Action                      |
| ----------- | --------------------------- |
| < 0.10      | Stable                      |
| 0.10 – 0.25 | Retrain model               |
| > 0.25      | Trigger alerts and rollback |

---

## Deployment Strategy

The model is exposed through a FastAPI-based REST API deployed on Azure Kubernetes Service.

### Candidate Routing Logic

| Probability Score | Action                  |
| ----------------- | ----------------------- |
| ≥ 0.75            | Fast-Track to Interview |
| 0.40 – 0.74       | Manual HR Review        |
| < 0.40            | Archive                 |

---

## Reliability Targets

### Service Level Objectives (SLOs)

* Availability: ≥ 99.95%
* Inference Latency: ≤ 200ms
* Server Error Rate: ≤ 0.1%

---

## Business Impact

The proposed solution transforms recruitment from a manual screening process into a predictive decision-support system.

### Expected Benefits

* 72% reduction in recruiter screening workload
* Faster candidate processing
* Reduced hiring costs
* Improved hiring consistency
* Enhanced candidate experience
* Strong governance and compliance framework

---

## Technologies Used

* Python
* Scikit-Learn
* Pandas
* NumPy
* Matplotlib
* Seaborn
* MLflow
* Apache Spark
* Databricks
* Google BigQuery
* Azure Kubernetes Service (AKS)
* Docker
* OpenAI GPT-4o
* FastAPI

---

## Repository Structure

```text
BAN-6440-Final-Project-R/
│
├── data/
├── notebooks/
├── models/
├── visualizations/
├── deployment/
├── reports/
├── requirements.txt
├── README.md
└── LICENSE
```

---

## Author

**Abosede Bolanle Olaitan**

BAN 6440 Final Project
Nexford University

---

## License

This project is intended for academic and educational purposes. Please review repository licensing terms before commercial use.
