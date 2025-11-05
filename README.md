# macro-market-dashboard
This repository presents a Python-based Macro–Market Dashboard analyzing how key economic indicators — inflation, unemployment, and interest rates — influence stock market performance. It combines data cleaning, visualization, and VAR modeling to uncover dynamic relationships between macro trends and equity returns.

# 📊 Macro-Market Dashboard (2015–2024)
### Analyzing the Relationship Between Macroeconomic Indicators and Equity Market Performance

---

## 🎯 Objective
This project explores how macroeconomic variables such as **inflation**, **interest rates**, and **unemployment** interact with **equity market performance** (S&P 500).  
It demonstrates the end-to-end data analysis pipeline — from data collection and cleaning to statistical modeling and visualization.

---

## 🧠 Motivation
Financial markets are deeply linked to macroeconomic conditions. Understanding these linkages helps analysts, economists, and investors anticipate market movements and evaluate policy effects.

---

## 🧰 Tech Stack
- **Python** (Pandas, NumPy, Matplotlib, Seaborn, Statsmodels)
- **pandas-datareader** (for live FRED data)
- **Jupyter Notebook**
- **FRED – Federal Reserve Economic Data**

---

## 🗂️ Dataset Description
Data sourced directly from **FRED** using `pandas_datareader.data`:

| Variable | FRED Code | Description |
|-----------|------------|--------------|
| Inflation | `CPIAUCSL` | Consumer Price Index |
| Unemployment Rate | `UNRATE` | Civilian Unemployment Rate (%) |
| Interest Rate | `FEDFUNDS` | Federal Funds Effective Rate (%) |
| Equity Index | `SP500` | S&P 500 Index Level |

**Time Range:** January 2015 – December 2024  
**Frequency:** Monthly  

---

## 🔍 Methodology

### 1️⃣ Data Retrieval
- Pulled time-series data from FRED API for all four variables.
- Merged into a single DataFrame aligned by date.

### 2️⃣ Data Cleaning
- Handled missing dates via forward-fill.
- Calculated monthly percentage changes.
- Created stationary series via differencing for time-series modeling.

### 3️⃣ Exploratory Data Analysis
- **Line Charts:** Visual trends across inflation, unemployment, interest rate, and S&P 500.  
- **Heatmaps:** Correlation among macro variables and market index.  
- **Scatter + Regression:** Relationship between market returns and each macro factor.  
- **Rolling Correlations:** Changing relationships over time.

### 4️⃣ Stationarity & Modeling
Performed **ADF tests** and differencing to ensure stationarity before modeling.

| Variable | Stationary? | Transformation |
|-----------|-------------|----------------|
| Inflation | No | 2nd Difference |
| Interest Rate | No | 2nd Difference |
| Unemployment | Yes | None |
| S&P 500 Return | Yes | None |

---

## 📈 Statistical Modeling

### 🔹 ARIMA Models
Used ACF/PACF plots to fit univariate ARIMA models:
- **Inflation:** ARIMA(1, 2, 1)
- **Interest Rate:** ARIMA(1, 2, 1)
- **Unemployment:** ARMA(3, 1)

### 🔹 VAR Model
Built a **Vector Autoregression (VAR)** using stationary series:
- `SP500_Return`, `Unemployment_Rate`, `Inflation_Diff2`, `Interest_Rate_Diff2`

This captures interdependencies across all variables and allows **Impulse Response Analysis** to measure how shocks in one variable affect others.

---

## 🧩 Key Visualizations
All plots saved under the `/charts` folder:

| Visualization | File |
|----------------|------|
| Macro Trends (2015–2024) | `charts/macro_trends.jpeg` |
| Correlation Heatmap | `charts/correlation_heatmap.jpeg` |
| ACF/PACF per Variable | `charts/acf_pacf_*.jpeg` |
| VAR Impulse Responses | `charts/irf_*.jpeg` |

---

## 💡 Insights & Findings

- **Interest Rate hikes** show a strong **negative relationship** with equity performance.  
- **Unemployment** is inversely correlated with **S&P 500** levels — improving labor markets align with stronger markets.  
- **Inflation and Interest Rate** exhibit a positive correlation reflecting Fed policy responses.  
- The **post-2020** period shows heightened volatility and structural shifts in these relationships.

---

## 🧾 Deliverables
- 📁 Jupyter Notebook: `Macromarketdash.ipynb`
- 🖼️ Visualization Outputs: macromarkets.pdf
- 📜 README.md (this file)

---

## 🧩 Next Steps
- Add global indices (Euro Stoxx 50, Nikkei 225) for cross-region analysis.  
- Integrate **GDP**, **bond yields**, and **consumer sentiment**.  
- Build a **Streamlit dashboard** for interactive visualization.  

---

## 📚 References
- [FRED – Federal Reserve Economic Data](https://fred.stlouisfed.org/)  
- [pandas-datareader Documentation](https://pandas-datareader.readthedocs.io/)  
- [Statsmodels Time-Series Guide](https://www.statsmodels.org/stable/tsa.html)  
- [Investopedia – Macroeconomic Indicators](https://www.investopedia.com/terms/m/macroeconomics.asp)

---

