#  Optimal Betting Using the Kelly Criterion

This project calculates the **optimal betting fraction** for a binary (Bernoulli) bet using the **Kelly Criterion**, and compares different betting strategies such as **Full Kelly**, **Fractional Kelly**, and **Fixed Percentage** betting.

The notebook includes **simulations**, **sensitivity analysis**, and **performance comparisons** to illustrate how different strategies affect long-term bankroll growth and risk.

---

##  The Kelly Criterion Formula

\[
f^* = \frac{bp - q}{b}
\]

where:  
- \( f^* \): optimal fraction of capital to wager  
- \( b \): payout ratio (odds received per €1 bet)  
- \( p \): probability of winning  
- \( q = 1 - p \): probability of losing  

This formula maximizes the **long-term growth rate** of your bankroll, assuming repeated betting with reinvested profits.

---

##  Input Parameters

Set the **probability of winning** and **payout ratio**:

```python
p = 0.55  # Probability of winning
b = 1.0   # Payout ratio (1.0 = even odds)
q = 1 - p

print(f"Probability of winning (p): {p}")
print(f"Probability of losing (q): {q:.2f}")
print(f"Payout ratio (b): {b}")
````

Example Output:

```
Probability of winning (p): 0.55
Probability of losing (q): 0.45
Payout ratio (b): 1.0
```

---

##  Kelly Criterion Calculation

```python
def kelly_criterion(p, b):
    q = 1 - p
    kelly_fraction = (b * p - q) / b
    return max(0, kelly_fraction)
```

Example:

```
Optimal betting fraction: 0.1000
Optimal betting percentage: 10.00%
```

If the Kelly fraction is negative → the bet has a **negative expected value**, so **no bet should be placed**.

---

## Expected Value (EV)

[
EV = p \times b - (1 - p)
]

* **EV > 0:** Favorable bet (profitable long-term)
* **EV = 0:** Fair odds (break-even)
* **EV < 0:** Unfavorable bet (expected loss)

---

## Sensitivity Analysis

Explore how the optimal betting fraction changes with different probabilities (holding payout ratio constant).

Visualizes:

* Kelly fraction vs probability
* Your specific probability and optimal point

---

##  Strategy Comparison

The notebook compares:

* **Full Kelly** – maximizes long-term growth
* **Fractional Kelly** – reduces volatility
* **Fixed Betting** – simple constant-percentage approach

Simulations show the evolution of bankrolls across different strategies.

---

## Monte Carlo Simulation

Runs multiple simulations to analyze:

* Mean and median bankrolls
* Volatility
* Probability of profit and ruin
* Sharpe ratios
* Maximum drawdowns

Visualizations:

*  Distribution of final bankrolls
*  Risk vs Return scatter plots

---

## Example Insights

| Strategy      | Mean Return % | Median Return % | Sharpe Ratio | Prob. of Profit | Prob. of Ruin |
| ------------- | ------------- | --------------- | ------------ | --------------- | ------------- |
| Full Kelly    | 177.8%        | 65.0%           | 0.56         | 68.9%           | 0.0%          |
| Half Kelly    | 63.5%         | 45.5%           | 0.71         | 75.4%           | 0.0%          |
| Quarter Kelly | 27.7%         | 24.5%           | **0.82**     | 79.4%           | 0.0%          |
| Fixed 7.5%    | 115.3%        | 59.9%           | 0.58         | 74.7%           | 0.0%          |
| Fixed 20%     | 277.0%        | 59.9%           | 0.41         | 63.9%           | 0.0%          |

 **Best Sharpe ratio:** Quarter Kelly (balanced growth and risk)

---

## Requirements

To run the notebook, install dependencies:

```bash
pip install numpy pandas matplotlib seaborn ipython
```

Optional (to suppress warnings):

```bash
pip install warnings
```

---

##  Usage

1. Clone the repository:

   ```bash
   git clone https://github.com/pieterrotteveel/Optimal-Betting-Kelly-Criterion.git
   cd Optimal-Betting-Kelly-Criterion
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Open the Jupyter notebook:

   ```bash
   jupyter notebook kelly_criterion_calculator.ipynb
   ```

---

##  Key Insights

* **Full Kelly** maximizes growth but is volatile.
* **Fractional Kelly** smooths results and often improves real-world Sharpe ratios.
* **Fixed betting** can outperform when your probability estimates are uncertain.

>  *In practice, fractional Kelly (25–50%) provides the best balance between growth and stability.*

---

## Disclaimer

This project is for **educational and research purposes only**.
Betting and investing involve financial risk.
Always manage your exposure and never bet money you cannot afford to lose.

