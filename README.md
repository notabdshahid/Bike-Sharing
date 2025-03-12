# Pricing Analysis Project

![image](https://github.com/user-attachments/assets/61307b2a-53fb-4616-8310-da8e7d3b1741)


## Overview
This project analyzes pricing changes between 2021 and 2022 to determine whether further price increases are advisable. Using data from three tables—2021 data, 2022 data, and a service cost table—a query was used to extract relevant information, followed by a Power BI dashboard for visualization and insights.

## Data Sources
- **2021 Dataset**: Contains data for the year 2021.
- **2022 Dataset**: Contains similar data for 2022.
- **Cost Table**: Lists the service costs used in profitability calculations.

## SQL Query

```sql
with cte as (
select * from bike_share_yr_0
union 
select * from bike_share_yr_1
) 
select 
dteday, season, cte.yr, mnth, hr, weekday, rider_type, riders, price, COGS, riders*price as revenue, riders*price - COGS*riders as profit
from cte 
left join cost_table
on cte.yr = cost_table.yr;
```

## Power BI Dashboard
The Power BI dashboard provides a visual representation of the data, sliced by year (2021 and 2022) for comparative analysis.

![image](https://github.com/user-attachments/assets/b1be2cd2-70fa-49af-96de-50f602226814)

![image](https://github.com/user-attachments/assets/449e6f2c-c187-4346-83c4-95552033bcce)


## Key Insights & Recommendations

### Insight: Profitability Increase
Increasing the price from 2021 to 2022 resulted in a significant increase in profit. This suggests that customers were willing to pay higher prices with demand increasing as well.

### Recommendation: Conservative Price Increase
- **Substantial Prior Increase**: The price saw a significant jump from 2021 to 2022. To avoid reaching a price ceiling where demand might start declining, a **more conservative** price increase for the next year is recommended.
- **Suggested Range**: A **10-15% price increase** could be tested to gauge customer response while maintaining profitability.

### Recommended Strategy
- **Market Analysis**: Conduct further research into customer satisfaction, competitive pricing trends, and broader economic conditions.
- **Price Sensitivity Testing**: Consider A/B testing price adjustments in select markets before rolling out a universal increase.

## How to Use This Repository
1. Run the SQL query to extract data.
2. Load the data into Power BI.
3. Analyze insights from the dashboard.
4. Use findings to inform pricing strategy decisions.

## Future Improvements
- Integrate real-time market data for dynamic pricing recommendations.
- Incorporate customer sentiment analysis from reviews and surveys.
- Automate data updates and dashboard refreshes for continuous monitoring.

---

This project provides a data-driven approach to pricing decisions, ensuring profitability while balancing customer retention.

