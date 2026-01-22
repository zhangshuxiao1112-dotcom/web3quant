# 📈 Web3 Quant Trading Bot

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![Hackathon](https://img.shields.io/badge/HK%20Web3%20Quant-Top%2013-22C55E?style=flat-square)](https://github.com/zhangshuxiao1112-dotcom/web3quant)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

## 📖 Overview

A **real-time algorithmic cryptocurrency trading system** with hybrid multi-factor strategies. This project was developed for the HK Web3 Quant Hackathon, achieving **Top 13 out of 100+ teams**.

## 🎯 Achievement

**🏆 HK Web3 Quant Hackathon - Top 13** - Developed and deployed a real-time algorithmic trading bot using a hybrid multi-factor strategy.

## ✨ Features

- **Multiple Trading Strategies**:
  - **SMA Crossover**: Simple Moving Average crossover strategy
  - **Momentum (MOM)**: Momentum-based trend following
  - **Mean Reversion (MR)**: Statistical arbitrage using Bollinger Bands

- **Automatic Strategy Selection**: Dynamically selects the best-performing strategy based on historical data
- **Real-time Data Integration**: Fetches live price data from HORUS API
- **Transaction Cost Modeling**: Includes realistic trading costs in backtesting
- **Multi-timeframe Analysis**: Supports 15-minute and daily data intervals

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| Python 3.8+ | Core programming language |
| Pandas | Data manipulation and time series analysis |
| NumPy | Numerical computations and signal processing |
| Requests | API communication |

## 📁 Project Structure

```
web3quant/
├── final.py              # Main strategy implementation
├── get_data_HORUS.py     # HORUS API data fetcher
├── get_date_Roostoo.py   # Alternative data source
├── python_demo.py        # Basic demo script
├── partner_python_demo.py # Partner API demo
├── run.py                # Execution script
└── README.md             # This file
```

## 🚀 Getting Started

### Prerequisites

```bash
pip install requests pandas numpy
```

### Usage

```python
from final import decide_strategy, run_strategy
import get_data_HORUS

# Get historical data
data = get_data_HORUS.get_price_15m('BTC', '2025-01-01 00:00', '2025-01-15 00:00')

# Decide best strategy based on historical performance
best_strategy = decide_strategy(data)
print(f"Best Strategy: {best_strategy}")

# Get trading signal
signal = run_strategy(data, best_strategy)
print(f"Current Position: {signal}")  # 1 = Long, 0 = Flat, -1 = Short
```

## 📊 Strategy Details

### SMA Crossover
```python
# Buy when short-term SMA crosses above long-term SMA
position = 1 if SMA_short > SMA_long else 0
```

### Momentum
```python
# Buy when rolling returns are positive
position = 1 if rolling_returns.mean() > 0 else 0
```

### Mean Reversion
```python
# Buy when price is 2 std below mean, sell when 2 std above
if price < mean - 2*std: position = 1   # Long
if price > mean + 2*std: position = -1  # Short
```

## 📈 Performance

- **Backtested Period**: Multiple months of cryptocurrency data
- **Strategy Selection**: Automatic based on recent performance scoring
- **Risk Management**: Position sizing and stop-loss integration

## 👤 Author

**Zhang Shuxiao**
- GitHub: [@zhangshuxiao1112-dotcom](https://github.com/zhangshuxiao1112-dotcom)
- Email: szhangfr@connect.ust.hk

## 📄 License

This project is licensed under the MIT License.

---

<p align="center">
  <i>Built with ❤️ for algorithmic trading research</i>
</p>
