# Chart Selection Justification

## Overview

The dashboard uses chart types based on the business question being answered. The goal was to avoid decorative visuals and use charts that support executive decision-making.

## 1. Regional Performance

Business question:

Which region contributes the most sales, and how does regional profitability compare?

Chart type used:

Horizontal bar chart.

Why this chart type is appropriate:

Regions are categorical values, and a bar chart makes it easy to compare sales across regions. Horizontal bars also make labels easier to read.

Fields used:

| Visual Element | Field |
|---|---|
| Rows | `region` |
| Columns | `SUM(sales)` |
| Color | `Profit Margin` |
| Tooltip | Sales, Profit Margin, Region |
| Filter action | Order date, Category, Customer segment, Region(selection filters other dashboard views) |

Design principle applied:

The chart uses length for sales comparison and color for profitability. This creates a clear executive view of both scale and quality of performance.

Mistake avoided:

A map was not used as the primary chart because region-level comparison is clearer and more compact as a bar chart. The chart also avoids stacked blocks that could confuse sales comparison.

## 2. Sales Trend

Business question:

How are sales changing over time, and which categories drive the trend?

Chart type used:

Line chart.

Why this chart type is appropriate:

Time-series data is best shown with a line chart because it helps users see movement, peaks, dips, and trend patterns across months.

Fields used:

| Visual Element | Field |
|---|---|
| Columns | `MONTH(order_date)` |
| Rows | `SUM(sales)` |
| Color | `category` |
| Tooltip | Sales, Profit, Profit Margin, Category, Month of order date |
| Filter | Order Date, Category, Customer Segment, Region |

Design principle applied:

Consistent category colors are used so the viewer can follow each product category over time.

Mistake avoided:

A bar chart was not used for the trend because monthly bars for multiple categories would create more clutter and make the time pattern harder to read.

## 3. Discount vs Profit

Business question:

How does discount level relate to profit?

Chart type used:

Scatter plot using circle marks.

Why this chart type is appropriate:

The relationship between two numeric measures is best shown with a scatter plot. `AVG(discount)` is placed on the x-axis and `SUM(profit)` is placed on the y-axis.

Fields used:

| Visual Element | Field |
|---|---|
| Columns | `AVG(discount)` |
| Rows | `SUM(profit)` |
| Mark type | Circle |
| Color | `Discount Band` |
| Size | `SUM(sales)` |
| Detail | `sub_category` |
| Filter | Order Date, Category, Customer Segment, Region |
| Tooltip | Sales, Profit, Profit Margin, Discount Band, Sub-category, Avg discount |

Design principle applied:

Position is used to show the discount-profit relationship, while color communicates discount band risk.

Mistake avoided:

`SUM(discount)` was avoided because discount is a rate and summing it would distort interpretation. The chart uses average discount instead.

## 4. Category Profitability

Business question:

Which categories and sub-categories drive profit?

Chart type used:

Horizontal bar chart.

Why this chart type is appropriate:

Sub-categories are categorical values, and profit ranking is easiest to compare using bar length. The horizontal layout supports readable sub-category names.

Fields used:

| Visual Element | Field |
|---|---|
| Rows | `category`, `sub_category` |
| Columns | `SUM(profit)` |
| Color | `SUM(profit)` |
| Tooltip | Sales, Profit, Profit Margin, Category, Sub-category |
| Filter | Category, Customer Segment, Region, Order Date |

Design principle applied:

The chart uses ordered bars to make high-profit and low-profit sub-categories easy to identify.

Mistake avoided:

A pie chart was avoided because it would not show sub-category ranking clearly. The chart also avoids unnecessary decoration.

## 5. Return Analysis

Business question:

Which category and customer segment combinations have higher return risk?

Chart type used:

Highlight table.

Why this chart type is appropriate:

Return rate is a risk metric, and a highlight table allows leadership to scan category-segment combinations quickly.

Fields used:

| Visual Element | Field |
|---|---|
| Rows | `category` |
| Columns | `customer_segment` |
| Color | `Return Rate` |
| Label | `Return Rate` |
| Tooltip | Returned Orders, Total Orders, Return Rate, Category, Customer segment |
| Filter | Category, Customer Segment, Region, Order Date |

Design principle applied:

Color intensity is used to show higher return risk. Labels are included because return percentages need precise interpretation.

Mistake avoided:

A complex chart was avoided because return-risk comparison is clearer as a compact matrix.

## 6. KPI Cards

Business question:

What is the overall business performance at a glance?

Chart type used:

KPI text cards.

Why this chart type is appropriate:

Executives need immediate summary metrics before reading detailed charts.

Fields used:

| KPI | Field |
|---|---|
| Total Sales | `SUM(sales)` |
| Total Profit | `SUM(profit)` |
| Profit Margin | `Profit Margin` |
| Return Rate | `Return Rate` |

Design principle applied:

The KPI cards are placed in the left control panel under the filters, so users can change filters and immediately see updated business results.

Mistake avoided:

The dashboard avoids hiding key performance metrics inside tooltips only. The most important metrics are visible at all times.

## 7. Supporting Views

The workbook also includes supporting views for customer segment and shipping performance.

Customer Segment View:

1. Compares performance across Consumer, Corporate, and Home Office.
2. Uses bar charts because customer segments are categorical.
3. Supports understanding of segment sales, profit, and return differences.

Shipping Performance View:

1. Shows shipping mode and delivery delay impact.
2. Uses a bar chart because shipping modes are categorical.
3. Supports operational analysis of delivery days and shipping-related risk.

These views are included in the workbook as supporting analysis, even though the final executive dashboard focuses on five core dashboard charts for readability.

## Dashboard Design Principles Applied

1. Correct chart selection:
   - Each chart type matches the business question.

2. Clear hierarchy:
   - Filters and KPIs are placed on the left.
   - Main analytical views are placed in the main dashboard area.

3. Minimal clutter:
   - The final dashboard uses five main charts instead of showing every worksheet.

4. Consistent color meaning:
   - Green indicates stronger profit or healthier performance.
   - Red/orange indicates weaker performance or risk.

5. Readability:
   - Horizontal bars are used where category labels need space.
   - KPI cards use large readable numbers.

6. Avoidance of misleading visuals:
   - No 3D charts are used.
   - Pie charts are avoided.
   - Discount is averaged rather than summed.

