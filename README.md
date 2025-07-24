# Week2
An end-to-end project for forecasting electric vehicle (EV) adoption using time-series analysis and machine learning. This repository uses Washington State registration data to clean, visualize, and engineer features. It compares Random Forest and Gradient Boosting models to predict future county-level EV counts to aid in infrastructure planning.

# EV Adoption Forecasting using Machine Learning

![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)
![Libraries](https://img.shields.io/badge/Libraries-Pandas%2C%20Scikit--learn%2C%20Matplotlib-orange.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## Project Overview

This repository contains a data science project focused on forecasting the adoption of electric vehicles (EVs). As EV adoption surges, urban planners and policymakers require accurate forecasts to anticipate infrastructure needs, particularly for charging stations. This project demonstrates a complete machine learning workflow to predict future EV counts based on historical registration data.

The analysis uses a dataset of monthly EV registrations from Washington State, performing everything from data cleaning and exploratory analysis to time-series feature engineering. It implements and compares two powerful ensemble models, **Random Forest** and **Gradient Boosting**, to generate reliable forecasts.

---

## 📋 Problem Statement

Using a real-world electric vehicle dataset, this project aims to create a robust regression model to forecast future EV adoption. The goal is to predict the number of electric vehicles in upcoming years based on historical trends, helping to inform and guide infrastructure planning.

---

## 📊 Dataset

The dataset used is the "Electric Vehicle Population By County" dataset, which contains monthly counts of registered vehicles from the Washington State Department of Licensing (DOL).

-   **Source:** [Kaggle Dataset Link](https://www.kaggle.com/datasets/sahirmaharajj/electric-vehicle-population-size-2024/data)
-   **Key Features:** `Date`, `County`, `State`, `Vehicle Primary Use`, `Battery Electric Vehicles (BEVs)`, `Plug-In Hybrid Electric Vehicles (PHEVs)`, and `Electric Vehicle (EV) Total`.

---

## ⚙️ Project Workflow

The project follows a structured data science workflow:

1.  **Data Loading and Cleaning:** The dataset is loaded, data types are corrected, and missing values are handled. Outliers in the `Percent Electric Vehicles` feature are capped using the IQR method.
2.  **Exploratory Data Analysis (EDA):** Visualizations are created to understand the overall trend of EV adoption over time and the breakdown of vehicle types (BEV vs. PHEV).
3.  **Feature Engineering:** To prepare the data for time-series forecasting, several features were created for each county:
    * **Time-Based Features:** `year`, `month`, `months_since_start`.
    * **Lag Features:** EV totals from 1, 2, and 3 months prior.
    * **Rolling Features:** 3-month rolling average of EV totals.
    * **Growth Features:** Percentage change in EV count and a rolling growth slope.
4.  **Modeling and Evaluation:**
    * Two models were trained: **Random Forest Regressor** (tuned with `RandomizedSearchCV`) and a **Gradient Boosting Regressor**.
    * The models were evaluated and compared using **MAE**, **RMSE**, and **R² Score** on a time-based test set.
5.  **Forecasting:** The best-performing model is used to generate a 3-year forecast for specific counties, visualizing both the monthly and cumulative adoption trends.

---

## 🛠️ Technology Stack

-   **Language:** Python 3
-   **Libraries:**
    -   Pandas for data manipulation and analysis.
    -   NumPy for numerical operations.
    -   Scikit-learn for machine learning models, preprocessing, and evaluation.
    -   Matplotlib & Seaborn for data visualization.
    -   Joblib for saving the trained model.

---

## 🚀 Getting Started

### Prerequisites

-   Python 3.9 or higher
-   Jupyter Notebook or JupyterLab

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/your-repository-name.git](https://github.com/your-username/your-repository-name.git)
    cd your-repository-name
    ```


### Usage

1.  **Launch Jupyter Notebook:**
    ```bash
    jupyter notebook
    ```
2.  Open the `EV_Adoption_Forecasting.ipynb` file and run the cells sequentially to see the full analysis and forecasting process.
3.  The trained model is saved as `forecasting_ev_model.pkl`, which can be loaded for direct predictions.

---

## 📈 Key Results & Visualizations

The model achieves a very high R² score on the test set, demonstrating strong performance, particularly in predicting stable, low-growth counties.

**1. Comparative Feature Importance:**
The models identified recent historical data (`ev_total_lag2` and `ev_total_lag1`) as the most important predictors.

![Feature Importance Plot](path/to/your/feature_importance_plot.png)

**2. 3-Year Forecast for Kings County:**
The model projects a continued linear growth in monthly EV registrations for a sample county.
