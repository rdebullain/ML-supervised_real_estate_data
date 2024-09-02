# Midterm Project

## Project/Goals
The goal of this project is to predict the sold price of real estate properties using a dataset of property listings. The dataset contains various attributes about the properties, including location, description, flags, and more. The objective is to preprocess the data, build and evaluate predictive models, and determine the best-performing model.

![house price prediction](https://miro.medium.com/v2/resize:fit:1400/1*3Psu7nDr2LvhWH4R6-Tqeg.jpeg)

## Process

### Step 1: Data Collection and Initial Exploration
- **Details:** 
  - Collected data from JSON files in the specified directory.
  - Listed all JSON files in the directory and read them into dataframes.
  - Normalized the data to handle nested structures in the JSON files.
  - Combined all normalized dataframes into a single dataframe for further processing.

![Heat Map](https://github.com/rdebullain/data_project_midterm/blob/main/images/Correlation%20Heatmap.png?raw=true)

![Sold Price Distribution](https://github.com/rdebullain/data_project_midterm/blob/main/images/Sold%20Price%20Distribution.png?raw=true)

![Year Built Boxplot](https://github.com/rdebullain/data_project_midterm/blob/main/images/Year%20Built%20Boxplot.png?raw=true)

### Step 2: Data Preprocessing
- **Details:**
  - Dropped rows with missing target variable `description.sold_price`.
  - Handled missing values in categorical and numerical columns.
  - Imputed missing values for categorical columns using the most frequent strategy.
  - Imputed missing values for numerical columns using the median strategy.
  - Feature engineering, including calculating `days_on_market`.
  - One-hot encoded categorical variables.
  - Dropped redundant and irrelevant columns.

### Step 3: Data Cleaning and Feature Engineering
- **Details:**
  - Converted data types appropriately (e.g., dates to datetime, numeric values to numeric types).
  - Capped outliers in numerical columns to reduce the impact of extreme values.
  - Added custom transformations and normalized nested JSON fields.
  - Ensured all data transformations are consistent and ready for modeling.

### Step 4: Model Training and Evaluation
- **Details:**
  - Loaded the processed data.
  - Separated features and target variable.
  - Split the data into training and testing sets.
  - Trained multiple models (Linear Regression, Support Vector Machines, Random Forest, and XGBoost).
  - Evaluated models using metrics such as MSE, RMSE, MAE, and R².
  - Selected the best-performing models based on evaluation metrics.

### Step 5: Feature Selection and Model Refinement
- **Details:**
  - Scaled the data using StandardScaler.
  - Performed feature selection using Lasso and SelectFromModel.
  - Refit models with selected features.
  - Re-evaluated models with selected features to ensure improvement in performance.

### Step 6: Cross-Validation and Hyperparameter Tuning
- **Details:**
  - Created custom cross-validation folds based on city prefixes.
  - Performed hyperparameter search using cross-validation folds.
  - Trained the best model on the entire training set and evaluated it on the test set.
  - Saved the best model for future predictions.

## Results
- **Model Performance:**
  - **Linear Regression:** 
    - MSE: 5.48e+09
    - RMSE: 74000.45
    - MAE: 42958.05
    - R²: 0.8897
  - **Support Vector Machines:** 
    - MSE: 5.15e+10
    - RMSE: 226836.03
    - MAE: 150471.07
    - R²: -0.0365
  - **Random Forest:** 
    - MSE: 1.51e+09
    - RMSE: 38893.83
    - MAE: 13246.01
    - R²: 0.9695
  - **XGBoost:** 
    - MSE: 2.83e+09
    - RMSE: 53182.95
    - MAE: 36968.54
    - R²: 0.9430

## Challenges
- Handling missing values and ensuring consistency across all data transformations.
- Managing the complexity of nested JSON data and normalizing it correctly.
- Balancing the trade-off between model complexity and performance.
- Ensuring the model does not overfit during hyperparameter tuning.

## Future Goals
- Improve model performance by experimenting with more advanced feature engineering techniques.
- Explore additional machine learning models and ensemble methods.
- Incorporate more domain knowledge into the model to enhance predictions.
- Deploy the model as a web service for real-time predictions.

## Code
All the code for data processing, model training, evaluation, and prediction is contained in separate Python scripts. Below are the key functions used in the project:

### Data Processing
- `process_json_files`: Process JSON files, normalize data, and save to CSV.

### Custom Cross-Validation and Hyperparameter Search
- `custom_cross_validation`: Create training and validation folds.
- `hyperparameter_search`: Perform hyperparameter search using cross-validation folds.

### Model Training and Evaluation
- Trained models: Linear Regression, Support Vector Machines, Random Forest, XGBoost.
- Evaluation metrics: MSE, RMSE, MAE, R².

### Feature Selection
- Feature selection methods: Lasso, SelectFromModel.

### Prediction Pipeline
- Functions to load model, preprocess data, and make predictions.

This project showcases the complete workflow from data collection and preprocessing to model training, evaluation, and deployment. The final model can be used to predict the sold price of real estate properties based on various attributes.
