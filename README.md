# Olympic Medal Prediction Using Historical Data

## Project Overview
This project uses historical Olympic athlete-event data to predict whether an athlete will win a medal. The project applies data mining, business analytics, and machine learning techniques to support decision-making for National Olympic Committees, sports federations, and performance analysts.

The main purpose of this project is not to replace coaches or experts. Instead, the model can be used as an early screening tool to identify athlete-event records that may deserve deeper review.

## Business Problem
Olympic organizations have limited resources such as funding, coaching time, training support, and travel opportunities. Because not every athlete or event can receive equal attention, decision-makers need a structured way to identify athlete-event profiles with higher medal potential.

This project supports the question:

**Which athlete-event profiles should be prioritized for additional review because they show a higher likelihood of medal success?**

## Dataset
The dataset used in this project is:

**120 Years of Olympic History: Athletes and Results**  
Source: Kaggle  
Time Period: 1896–2016  
Dataset Grain: One athlete participating in one Olympic event in a specific year

After duplicate removal, the cleaned dataset contains:

- 269,731 athlete-event records
- 39,772 medal records
- 229,959 non-medal records

The target variable is:

**Medal_Won**
- 1 = Athlete won Gold, Silver, or Bronze
- 0 = Athlete did not win a medal

## Technologies Used
- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook

## Project Workflow
1. Loaded the raw Olympic dataset
2. Removed duplicate records
3. Created the binary target variable `Medal_Won`
4. Engineered BMI from Height and Weight
5. Checked missing values and data quality
6. Performed exploratory data analysis
7. Built machine learning models
8. Compared model performance
9. Created business insights and implementation recommendations

## Data Preparation
The final analytic table used nine predictors and one target variable.

Predictors used:
- Sex
- Age
- Height
- Weight
- BMI
- Year
- Season
- Sport
- Event

Fields removed to prevent leakage:
- Medal
- ID
- Name

The `Medal` column was removed because it directly reveals the target. `ID` and `Name` were removed to avoid memorization of athletes.

## Key EDA Insights
- Medal outcomes are rare, with only 14.75% of records resulting in medals.
- Medal prediction is an imbalanced classification problem.
- Age and BMI show some signal but do not clearly separate medal and non-medal records alone.
- Summer Olympic records have a higher medal rate than Winter records.
- Sport and Event are important because medal rates vary across competition types.
- NOC patterns are useful for exploration but should be interpreted carefully because of fairness and historical participation differences.

## Machine Learning Models
The project compared the following models:

- Logistic Regression with Age imputed
- Logistic Regression with Age dropped
- Decision Tree
- Random Forest

## Final Model
The final selected model was:

**Logistic Regression with Age Dropped**

This model was selected because it achieved the best F1-score and strong recall for the medal class.

## Model Results
Final model performance:

- Accuracy: 0.6564
- Precision: 0.2586
- Recall: 0.6922
- F1-score: 0.3766
- ROC AUC: 0.7295

The model correctly identified about 69% of actual medal-winning records in the test set. This makes it useful as a screening tool, but not as an automatic decision-making system.

## Why Random Forest Was Not Selected
Random Forest had higher accuracy, but it had lower recall and lower F1-score than the final Logistic Regression model. Since the business goal is to identify medal winners, recall and F1-score were more important than accuracy alone.

## Business Use
This model can help create a ranked list of athlete-event records for further review. Coaches, analysts, and decision-makers can use the model output along with expert judgment, recent performance, injury history, and sport-specific knowledge.

The best use of this model is:

**Decision support, not automatic selection.**

## Limitations
- The dataset covers 1896–2016, so historical changes may affect future predictions.
- Many important real-world factors are missing, such as injuries, training quality, rankings, funding, and coaching support.
- Medal outcomes are highly imbalanced.
- Some variables have missing values.
- The model should be monitored and retrained if used in future Olympic planning.

## Author
Vaishali Bundela
