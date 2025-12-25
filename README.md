# STAT 4601 Time Series Analysis Project
## CO2 Concentration Forecasting using SARIMA Models

[![R](https://img.shields.io/badge/R-4.0+-blue.svg)](https://www.r-project.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📋 Overview

This project analyzes monthly CO2 concentration data from the **Mauna Loa Observatory** (NOAA Global Monitoring Laboratory) using time series analysis techniques. The goal is to build and validate a **Seasonal ARIMA (SARIMA)** model to forecast future CO2 levels.

## 📊 Data Source

- **Source:** NOAA Global Monitoring Laboratory
- **URL:** https://gml.noaa.gov/webdata/ccgg/trends/co2/co2_mm_mlo.txt
- **Time Period:** April 2013 - October 2025 (151 months)
- **Variable:** Monthly average CO2 concentration (ppm)

## 🔬 Methodology

1. **Data Preparation:** Download and extract time series data from NOAA
2. **Exploratory Analysis:** Visualize trends and seasonal patterns
3. **Stationarity Testing:** ADF tests, mean/variance stability tests
4. **Model Identification:** ACF/PACF analysis for order selection
5. **Model Fitting:** Exhaustive SARIMA model search
6. **Diagnostic Checking:** Residual analysis, Shapiro-Wilk, Ljung-Box tests
7. **Forecasting:** 5-month ahead predictions with validation

## 📁 Project Structure

```
4601 project/
├── 4601_project.ipynb    # Main Jupyter notebook with R kernel
└── README.md             # This file
```

## 🛠️ Requirements

### R Packages

```r
install.packages('forecast')  # ARIMA modeling and forecasting
install.packages('httr')      # HTTP requests for data download
install.packages('readr')     # Data reading utilities
install.packages('ggplot2')   # Data visualization
install.packages('tseries')   # Time series tests (ADF)
```

### Environment

- R version 4.0 or higher
- Jupyter Notebook with R kernel (IRkernel)
- Internet connection (for data download)

## 🚀 Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/4601-project.git
   cd 4601-project
   ```

2. **Install R packages:**
   ```r
   install.packages(c('forecast', 'httr', 'readr', 'ggplot2', 'tseries'))
   ```

3. **Open the notebook:**
   ```bash
   jupyter notebook 4601_project.ipynb
   ```

4. **Run all cells** to reproduce the analysis

## 📈 Key Results

### Final Model

**SARIMA(1,0,1)(0,1,1)[12]** was selected as the best model based on:
- Lowest AIC among models with valid residuals
- Normal residuals (Shapiro-Wilk test passed)
- White noise residuals (all Ljung-Box tests passed)

### Model Equation

$$
(1 - \phi_1 B)(1 - B^{12})Z_t = \theta_0 + (1 + \theta_1 B)(1 + \Theta_1 B^{12})a_t
$$

### Parameter Estimates

| Parameter | Estimate | Description |
|-----------|----------|-------------|
| φ₁ (AR1)  | ~0.89    | Autoregressive coefficient |
| θ₁ (MA1)  | ~-0.54   | Moving average coefficient |
| Θ₁ (SMA1) | ~-0.87   | Seasonal MA coefficient |
| θ₀ (Drift)| ~0.22    | Drift term |

### Forecast Performance

- **MAE:** < 0.5 ppm
- **MAPE:** < 0.15%
- **95% CI Coverage:** High coverage rate on validation data

## 📊 Analysis Sections

1. **Setup and Dependencies** - Package installation and loading
2. **Data Acquisition** - Download CO2 data from NOAA
3. **Data Splitting** - 146 months training, 5 months validation
4. **Stationarity Analysis** - ADF tests, stability tests
5. **Model Identification** - ACF/PACF analysis
6. **Initial Model Fitting** - Candidate model comparison
7. **Comprehensive Search** - Exhaustive SARIMA grid search
8. **Final Model Analysis** - Residual diagnostics
9. **Forecasting** - 5-month ahead predictions
10. **Conclusions** - Summary and key findings

## 🔍 Statistical Tests Used

| Test | Purpose | Null Hypothesis |
|------|---------|-----------------|
| Augmented Dickey-Fuller (ADF) | Unit root testing | Series has unit root |
| Shapiro-Wilk | Normality of residuals | Residuals are normal |
| Ljung-Box | White noise testing | No autocorrelation |
| ANOVA | Mean stability | Constant mean over time |
| Bartlett's | Variance stability | Constant variance over time |

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **NOAA Global Monitoring Laboratory** for providing the CO2 concentration data
- **STAT 4601 Course** - Time Series Analysis
- R packages: `forecast`, `tseries`, `ggplot2`

## 📧 Contact

For questions or suggestions, please open an issue in this repository.

---

*Last updated: December 2025*
