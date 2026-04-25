# Australian Rainfall Prediction

### End-to-End Machine Learning Project (EDA → Modeling → Optimization)

---

## Project Overview

This project builds a complete machine learning pipeline to predict whether it will rain tomorrow in different locations across Australia using historical weather data.

The workflow covers:

- Exploratory Data Analysis (EDA)
- Feature Engineering
- Model Building & Comparison
- Class Imbalance Handling
- Threshold Optimization
- Hyperparameter Tuning
- Final Model Selection

The final system achieves strong predictive performance using **XGBoost**, with a balanced trade-off between precision and recall.

---

## Dataset Description

- **Source**: Australian Bureau of Meteorology (processed dataset)
- **Rows**: 145,460
- **Features**: 23 original weather attributes
- **Target Variable**: RainTomorrow (Yes / No)

### Key Features:
- Temperature (MinTemp, MaxTemp)
- Humidity (9am, 3pm)
- Atmospheric Pressure
- Wind Speed & Direction
- Cloud Cover
- Rainfall & Evaporation
- Sunshine Duration

---

## Problem Statement

Predict whether it will rain the next day based on current and historical weather conditions.

This is a **binary classification** problem with a moderately imbalanced dataset.

---

## Key Insights from EDA

- **Humidity** (especially Humidity3pm) is the strongest predictor of rainfall
- **Low pressure systems** strongly correlate with rain events
- **Cloud cover** and **sunshine duration** are highly informative
- Rainfall exhibits temporal dependency (RainToday strongly influences RainTomorrow)
- Weather patterns vary significantly across geographic locations

---

## Feature Engineering

New features were created to improve model performance:

- **Temperature Range** (MaxTemp − MinTemp)
- **Humidity Difference** (Morning vs Afternoon)
- **Pressure Difference**
- **Wind Speed Difference**
- **Seasonal Features** (Summer, Winter, etc.)
- **Encoded categorical variables** (Location, Wind Direction)

---

## Models Implemented

Multiple machine learning models were trained and evaluated:

### 1️⃣ Logistic Regression (Baseline)
- ROC-AUC: 0.865
- High recall, low precision

### 2️⃣ Random Forest
- ROC-AUC: 0.890
- High precision, lower recall

### 3️⃣ Tuned Random Forest (Threshold Optimization)
- F1 Score: 0.656
- Balanced performance

### 4️⃣ XGBoost (Best Model)
- ROC-AUC: 0.895
- F1 Score: 0.658
- Best overall balance between precision and recall

---

## Hyperparameter Tuning (XGBoost)

**RandomizedSearchCV** was applied to optimize:

- `max_depth`
- `learning_rate`
- `n_estimators`
- `subsample`
- `colsample_bytree`
- `min_child_weight`

**Result:**
- Slight improvement in ROC-AUC (0.895 → 0.897)
- Minimal performance gain, indicating strong baseline model quality

---

## Final Model Performance

| Model | Precision | Recall | F1 Score | ROC-AUC |
|-------|-----------|--------|----------|---------|
| Logistic Regression | 0.51 | 0.77 | 0.61 | 0.865 |
| Random Forest | 0.78 | 0.46 | 0.58 | 0.890 |
| Tuned RF | 0.61 | 0.71 | 0.66 | 0.890 |
| XGBoost (Final) | 0.57 | 0.78 | 0.66 | 0.895 |

---

## Final Model Selection

**Selected Model: XGBoost**

### Why?
- Best ROC-AUC score
- Strong recall (captures most rainfall events)
- Balanced F1-score
- Stable performance across tuning experiments

---

## Evaluation Strategy

The model was evaluated using:

- Accuracy (secondary metric due to imbalance)
- Precision
- Recall
- F1 Score
- ROC-AUC (primary metric)
- Confusion Matrix
- Threshold Tuning Analysis

---

## Key Learnings

- **Accuracy alone is misleading** for imbalanced datasets
- **Threshold tuning** significantly improves model usability
- Different models optimize different trade-offs:
  - Logistic Regression → Recall-focused
  - Random Forest → Precision-focused
  - XGBoost → Balanced performance
- **Feature engineering** had more impact than hyperparameter tuning

---

## Tech Stack

- **Python**
- **Pandas, NumPy**
- **Scikit-learn**
- **XGBoost**
- **Matplotlib, Seaborn**

---

## Project Structure

```
rainfall-prediction-project/
│
├── notebooks/          # EDA and modeling notebooks
├── models/             # Saved trained models (.pkl)
├── src/                # Reusable scripts
├── app/                # Streamlit app (future deployment)
├── visuals/            # Charts and plots
├── README.md           # Project documentation
```

---

## Future Improvements

- Deploy model using **Streamlit** or **FastAPI**
- Add **real-time weather API** integration
- Improve performance with **ensemble stacking**
- Build **interactive dashboard** for insights

---

## Author

**Ridwan Oduola**  
Data Scientist | Machine Learning Engineer

---

## ⭐ If you like this project

Feel free to ⭐ star the repository and explore other projects on my portfolio.
