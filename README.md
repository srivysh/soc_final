# soc_final
# PPO-Based Stock Trading Agent with FinBERT Sentiment

This project builds a stock trading agent using reinforcement learning. I have used the PPO algorithm to train the agent to decide whether to buy, sell, or hold a stock based on technical indicators and sentiment analysis using FinBERT. The agent is trained using a custom environment, and its performance is evaluated using QuantStats. I also created a Streamlit dashboard to visualize the results.

---

## Main Features

- Calculates technical indicators like Moving Average (MA), RSI, and daily returns.
- Uses FinBERT to extract sentiment scores from news headlines.
- A custom Gym environment is used for training the PPO agent.
- The trained agent's performance is evaluated using QuantStats.
- A Streamlit dashboard is available to visualize stock trends and portfolio value.

---

## How the Code Works

### 1. Data Collection and Preprocessing

- Stock data is downloaded using yfinance (for example, AAPL).
- Indicators like MA_18 (18-day moving average), RSI_15 (15-day RSI), and Daily_Return are calculated.
- A dummy headline like "The stock market is stable." is added for each day.
- FinBERT is used to compute a sentiment score from the headline.

### 2. Trading Environment

- A Gym environment called `StockSentimentEnv` is created.
- The state includes the closing price, MA, RSI, cash, number of shares held, and sentiment score.
- The action space has three options: 0 for hold, 1 for buy, and 2 for sell.
- The reward is based on how much the total net worth changes.

### 3. PPO Agent Training

- The PPO agent is trained using stable-baselines3 for 10,000 timesteps.
- After training, the model is saved for reuse.

### 4. Testing and Evaluation

- The trained agent is tested on the same environment.
- The portfolio value is recorded at each step.
- QuantStats is used to generate a performance report with metrics like Sharpe ratio and drawdown.

### 5. Streamlit Dashboard

- A separate script (`my_dashboard.py`) is created to display the results using Streamlit.
- It shows stock prices, indicators, portfolio value, and other summaries in a clean interface.

---

## How to Run

### Install the Required Libraries

Use the following command in your terminal:

```bash
pip install yfinance pandas numpy matplotlib transformers torch gymnasium stable-baselines3 quantstats streamlit
