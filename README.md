# Restaurant Orders Analysis — Power BI Dashboard

An end-to-end data analysis project exploring restaurant sales data to uncover insights about order behavior, peak times, menu performance, and cuisine popularity.

---

## Project Overview

This project uses the Restaurant Orders dataset from [Maven Analytics Data Playground](https://mavenanalytics.io/data-playground/restaurant-orders), which contains order history and menu data from a fictional restaurant. The goal was to analyze the data and answer four key business questions that a restaurant owner or manager would care about:

1. **What do the highest spend orders look like?** Which items were bought and how much was spent?
2. **Were there certain times with more or less orders?** What are the peak days and hours?
3. **Which cuisines should we focus on developing more menu items for?**
4. **What were the least and most ordered items, and what categories were they in?**

---

## Dataset

**Source:** [Maven Analytics Data Playground — Restaurant Orders](https://mavenanalytics.io/data-playground/restaurant-orders)

| File | Description |
|---|---|
| `order_details.csv` | Individual order line items with date, time, and item ID |
| `menu_items.csv` | Menu item names, categories, and prices |
| `restaurant_db_data_dictionary.csv` | Field definitions for both tables |

**Dataset Summary:**
- Date range: January 1, 2023 — March 9, 2023
- Total orders: 5,370
- Total items sold: 12,234
- Total revenue: $159,217.90
- Cuisines: American, Asian, Mexican, Italian
- Menu items: 32

---

## Key Insights

### Highest Spend Orders
- Top orders combined multiple high-priced Italian and Asian items
- Italian dishes drove the most revenue despite not being the most frequently ordered category

### Order Timing
- **Monday** was the busiest day by order volume
- **Wednesday** and **Saturday** had the lowest order counts
- Clear lunch and dinner rush peaks visible in hourly breakdown

### Cuisine Performance
| Cuisine | Items Sold | Revenue |
|---|---|---|
| Italian | 2,948 | $49,462 |
| Asian | 3,470 | $46,720 |
| Mexican | 2,945 | $34,796 |
| American | 2,734 | $28,237 |

- **Asian** cuisine is the most popular by volume but underpriced relative to demand — a strong candidate for menu expansion
- **American** underperforms on both revenue and volume despite having multiple items

### Most and Least Ordered Items
**Top 3 Most Ordered:**
1. Hamburger (American) — 622 orders
2. Edamame (Asian) — 620 orders
3. Korean Beef Bowl (Asian) — 588 orders

**Top 3 Least Ordered:**
1. Chicken Tacos (Mexican) — 123 orders
2. Potstickers (Asian) — 205 orders
3. Cheese Lasagna (Italian) — 207 orders

Note: 3 of the 5 least ordered items are Mexican — suggesting this cuisine needs menu redesign or promotion.

---

## Tools Used

- **Power BI Desktop** — data modeling, DAX measures, dashboard building
- **DAX** — calculated columns and measures for order count, revenue, time breakdowns
- **CSV** — raw data source

---

## DAX Measures Used

```dax
-- Count of unique orders
Order Count = DISTINCTCOUNT(order_details[Order Id])

-- Total revenue from orders
Total Order Spend = SUMX(order_details, RELATED(menu_items[price]))

-- Extract hour from order time
Order Hour = HOUR(TIMEVALUE(order_details[Order Time]))

-- Day of week label
Day of Week = FORMAT(order_details[Order Date], "DDD")

-- Month label
Month = FORMAT(order_details[Order Date], "MMM YYYY")
```

---

## Dashboard Pages

| Page | Description |
|---|---|
| Page 1 | High Spend Order Analysis |
| Page 2 | Order Timing — by day and hour |
| Page 3 | Cuisine & Menu Item Performance |

**[View the live report here](#)** *(replace with your Power BI publish-to-web link)*

---

## Recommendations

1. **Expand the Asian menu** — highest order volume signals strong customer demand
2. **Investigate Mexican underperformance** — 3 of 5 least ordered items are Mexican; consider replacing or repositioning them
3. **Promote mid-week traffic** — Wednesday is the slowest day; targeted promotions could balance order load
4. **Leverage Monday momentum** — Monday is the busiest day; ensure staffing and inventory are optimized

---

## How to Run This Project

1. Clone or download this repository
2. Open `restaurant_analysis.pbix` in **Power BI Desktop** (free download at [powerbi.microsoft.com](https://powerbi.microsoft.com))
3. If prompted, re-link the CSV data sources to your local file path via **Transform Data → Data Source Settings**

---

## Author

**[Your Name]**
[LinkedIn](#) • [Portfolio](#) • [GitHub](#)
