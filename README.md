# 📦 Demand Forecasting with Holt-Winters Seasonal Model

This project applies **Time Series Forecasting Techniques** to predict weekly demand (`units_sold`) for various SKUs across multiple stores. The focus is on understanding historical demand patterns, identifying seasonality, and using classical forecasting models to generate accurate short-term predictions.

🔍 **Goal**: To forecast SKU-level weekly demand using the Holt-Winters additive model and evaluate its performance on unseen data.

---

## 📌 Table of Contents

- [Project Overview](#project-overview)
- [Dataset Description](#dataset-description)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Time Series Analysis](#time-series-analysis)
- [Forecasting Approach](#forecasting-approach)
- [Model Evaluation](#model-evaluation)
- [Key Insights](#key-insights)
- [Future Improvements](#future-improvements)
- [How to Run](#how-to-run)
- [Author](#author)

---

## 📈 Project Overview

Forecasting product demand is a critical task in inventory planning, supply chain management, and business strategy. In this notebook, a univariate time series forecasting approach is used to model weekly demand (`units_sold`) by decomposing the series and applying the **Holt-Winters Additive Exponential Smoothing** method.

---

## 📂 Dataset Description

The dataset includes transactional data with the following relevant fields:

- `store_id`: Store identifier
- `sku_id`: Product SKU identifier
- `is_featured_sku`: Binary flag indicating if the SKU was promoted
- `is_display_sku`: Binary flag for display status
- `units_sold`: Number of units sold (forecast target)
- `base_price`, `total_price`: Pricing information

---

## 🔍 Exploratory Data Analysis

Key analyses performed:

- **Distribution Analysis**:  
  - Sales (`units_sold`) is right-skewed.
  - Most SKUs are not frequently featured or displayed.
  
- **Correlation Matrix**:  
  - `is_featured_sku` and `is_display_sku` show **positive correlation** with `units_sold`.  
  - `total_price` and `units_sold` are **slightly negatively correlated**.

- **Missing Value Treatment**:  
  - A single missing value in `total_price` was imputed with the median value for that SKU.

---

## 🕒 Time Series Analysis

- **STL Decomposition**:
  - **Trend**: Stable, with no long-term growth or decline.
  - **Seasonality**: Annual periodic spikes (e.g., festive seasons or promotional periods).
  - **Residuals**: Irregular fluctuations remain after removing trend & seasonality.

- **Autocorrelation Analysis (ACF)**:
  - Clear sinusoidal pattern confirms the **presence of seasonality**.

- **Volatility**:
  - Standard deviation of week-over-week percentage change ≈ **26%** — indicates moderate fluctuation.

- **Smoothing Techniques**:
  - **4-week Moving Average**: Captures short-term variations.
  - **52-week Moving Average**: Reveals long-term baseline.

---

## 📉 Forecasting Approach

- **Model Used**:  
  [Holt-Winters Exponential Smoothing (Additive)](https://en.wikipedia.org/wiki/Exponential_smoothing#Triple_exponential_smoothing)  
  - Additive trend + additive seasonality (fixed amplitude).
  - Suitable due to observed constant seasonal magnitude over time.

- **Train-Test Split**:  
  - 80% data used for training, 20% for testing.

---

## ✅ Model Evaluation

- **Metric Used**:  
  - **Root Mean Squared Error (RMSE)** ≈ **13,387 units**

- **Visual Inspection**:  
  - Forecast captures overall seasonal pattern well.
  - Peaks are slightly under-predicted, reflecting the model’s smoothing limitations.

---

## 🔍 Key Insights

- Demand is **highly seasonal** but lacks a global trend.
- Promotions (`is_featured_sku`, `is_display_sku`) drive a noticeable lift in sales.
- Holt-Winters performs well for **baseline forecasting**, but peak underestimation may require model enhancement.

---

## 🚀 Future Improvements

- ✅ Add benchmark models: Prophet, SARIMA, or XGBoost with time-based features  
- ✅ Fine-tune Holt-Winters smoothing parameters via grid search  
- ✅ Incorporate exogenous variables like promotions and price in SARIMAX or regression-based forecasting  
- ✅ Improve residual handling (e.g., outlier removal, Box-Cox transformations)

---

## ▶️ How to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/rasika1205/Demand-Forecasting.git
   cd Demand-Forecasting
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Launch the notebook:

   ```bash
   jupyter notebook Demand\ Forecasting.ipynb
   ```

---

## 🧑‍💻 Author

**Rasika Gautam**
*B.Tech in Mathematics & Computing, NSUT*
Data Science & AI Enthusiast | 📊 Time Series | Forecasting
[GitHub Profile](https://github.com/rasika1205)


