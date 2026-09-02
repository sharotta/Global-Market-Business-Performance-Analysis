# Global Market & Business Performance Analysis
This project looks at sales, customer feedback, product performance, and marketing activity across different markets to understand what is driving business performance and where there may be opportunities to improve.

The goal was not simply to report what happened, but to use the available data to identify patterns, questions worth investigating, and areas where management could focus its attention.

## Business Context
A global business is operating across different regions, product categories, customer segments, and marketing channels. Management needs a clearer view of how these areas are performing and where the business may have opportunities or areas that need attention.

This project brings together sales, customer, product, marketing, and feedback data to understand differences in performance across markets and identify patterns that can help guide business decisions. 

## Business Problem
Management needs a clearer view of what is driving differences in sales performance across **markets, products, customers, and marketing channels** so that resources can be directed toward the areas with the greatest opportunity.

## Questions I wanted to answer
1. Which markets and regions are contributing most to revenue?
2. Which products and categories are performing well or underperforming?
3. Which customer segments contribute most to sales?
4. What does customer feedback tell us about the customer experience?
5. How are marketing channels performing?
6. Are there noticeable changes in performance over time?
7. Where should management investigate further?

## Key Takeaways
* **Regional performance varies significantly:** North America is the strongest revenue-generating region, while Europe records the lowest revenue contribution.
* **Performance differs across product categories:** Electronics and Home Appliances are the strongest contributors, while Clothing records the lowest revenue.
* **Customer and marketing performance are uneven:** Adults contribute the highest revenue among customer segments, while Social Media and Organic Search generate stronger revenue than Paid Ads.
* **There are opportunities beyond revenue growth:** The low repeat-purchase rate, engagement-to-conversion drop-off, and negative sentiment in Beauty highlight areas where improving the customer journey could create additional value.

## Data
The analysis uses sales, customer, product, marketing, and customer feedback data across different regions and product categories.

The data includes information such as revenue, customer segments, acquisition sources, engagement and conversion activity, product categories, customer ratings, sentiment, and repeat purchases. Together, these datasets provide different views of business performance and customer behaviour.

## Analytical Approach
I approached the analysis in four stages:

1. Review the data: Reviewed the available sales, customer, product, marketing, and feedback data to see what each dataset could tell us about the business.

2. Prepare the data: Cleaned the data, checked for inconsistencies, and prepared the different datasets for analysis.

3. Analyse business performance: Compared performance across regions, products, customer segments, marketing channels, and customer feedback to identify meaningful patterns and differences.

4. Connect findings to business decisions: Looked beyond the numbers to consider what the findings could mean for the business, where further investigation may be needed, and what areas management could consider when making decisions.

## Data Preparation & Modelling
### Data Cleaning & Preparation
1. Sales Data
- Removed blank rows and verified data types
- Date column was changed to a proper dd/mm/yyyy format
- Standardized Product Category entries using PROPER() and TRIM() functions
- Created reference table for countries and regions, and misclassified country and regions were fixed with a mapping table XLOOKUP
- Missing Revenue was replaced with average revenue for that product category using AVERAGEIFS
- Missing Brand was replaced with mode using helper table and INDEX-MATCH
- Standardized "Usa" to "USA" using UPPER function
- Check for Duplicate Order IDs using =COUNTIF(A:A, A2) → Filter for results > 1

2. Feedback Data
- Cleaned rating values and ensured all are numeric.
- Mapped Product Category from Product Dimension using INDEX-MATCH on Product ID.
- Trimmed and formatted textual data fields like Review Text Created a sentiment score.

3. Customer Dimension Table
- Cleaned Segment, Age Group, and Gender fields
- Removed duplicate Customer IDs
- Verified uniqueness of Customer ID for relationship creation
- Added to Power Pivot and linked to Sales_Data and Feedback_Data

4. Product Dimension Table
- Cleaned Product Category names, standardize categorical values (e.g., strip white spaces in "Product Category")
- Verified Product ID as unique (primary key)
- Used as a lookup table to enrich Feedback_Data
- Product Category mismatch- Cleaned with TRIM, PROPER, I also removed Duplicates.

### Data Modelling in Excel (Power Pivot)
The datasets were connected through shared customer and product information so that sales, customer behaviour, product performance, and feedback could be analysed together rather than as separate datasets.
<img width="1294" height="660" alt="Modelling" src="https://github.com/user-attachments/assets/53d7e3fb-6d17-4e92-83a1-28ccbd719316" />
The following relationships were successfully created: 
- Feedback_Data ↔ Product_Dim → via Product ID 
- Feedback_Data ↔ Customer_Dim → via Customer ID 
- Sales_Data ↔ Customer_Dim → via Customer ID

## Analysis
### Regional Performance
North America generated the highest revenue at $90,020, while Europe recorded the lowest at $11,100. The gap highlights a clear difference in regional performance and raises an important business question: what is driving the stronger performance in North America and the weaker results in Europe?
<img width="1077" height="488" alt="Dashboard 1" src="https://github.com/user-attachments/assets/607a837b-85cb-420e-b866-c25757695bd4" />
This provides a starting point for investigating differences in customer behaviour, product mix, marketing activity, pricing, and other market factors.

### Product Performance
Electronics generated the highest revenue at $34,735, followed by Home Appliances at $33,096. Clothing recorded the lowest revenue at $27,995, creating a noticeable gap between the stronger and weaker-performing categories.
<img width="1077" height="488" alt="Dashboard 1" src="https://github.com/user-attachments/assets/607a837b-85cb-420e-b866-c25757695bd4" />
The difference is worth investigating further to understand whether it is related to customer demand, product mix, pricing, visibility, or marketing performance. This would help determine whether Clothing needs a change in strategy or simply requires a different approach to reaching its target customers.

### Customer Segments
The Adult customer segment generated the highest revenue at $57,629 and accounted for 592 units purchased, making it the strongest-performing segment in the analysis.
<img width="1077" height="488" alt="Dashboard 1" src="https://github.com/user-attachments/assets/607a837b-85cb-420e-b866-c25757695bd4" />
This makes the segment important to understand from a business perspective. Looking more closely at its purchasing behaviour, product preferences, and engagement patterns could help identify opportunities to strengthen retention and growth without assuming that other customer segments have limited potential.

### Marketing Performance
Social Media and Organic Search generated the highest revenue among the marketing channels analysed, while Paid Ads contributed less by comparison.
<img width="912" height="419" alt="Dashboard 2" src="https://github.com/user-attachments/assets/02055ed4-48bc-4ced-a336-cc9deff9de49" />
The difference in channel performance raises an important question about how efficiently each channel is contributing to the customer journey. Further analysis of acquisition cost, conversion rates, customer quality, and repeat purchasing would help determine where marketing resources are generating the greatest value.

### Customer Feedback
The Beauty category recorded a relatively high level of negative customer sentiment compared with the other categories analysed. This may point to areas of dissatisfaction with the product or customer experience and makes the category worth investigating further.
<img width="912" height="419" alt="Dashboard 2" src="https://github.com/user-attachments/assets/02055ed4-48bc-4ced-a336-cc9deff9de49" />
Reviewing the underlying feedback, returns, complaints, and product-related issues could help identify what is driving the negative sentiment and whether changes to the product or customer experience are needed.

### Trends Over Time
Revenue increased from a low of $13,734 in February to a peak of $17,547 in August, before declining in the months that followed.
<img width="1077" height="488" alt="Dashboard 1" src="https://github.com/user-attachments/assets/607a837b-85cb-420e-b866-c25757695bd4" />
The change in momentum is worth investigating further. Comparing this pattern with previous periods and reviewing factors such as marketing activity, inventory availability, customer demand, and other business conditions could help determine whether the decline reflects a recurring pattern or a change in performance.

## Business Recommendations
Based on the patterns identified in the analysis, the following areas should be prioritised for further investigation and action:
 1. Understand the drivers of regional performance: North America is the strongest revenue-generating region, while Europe records the lowest revenue. Management should examine differences in customer behaviour, product mix, marketing activity, pricing, and market conditions to understand what is driving the gap.
2. Investigate lower-performing product categories: Clothing records the lowest revenue among the categories analysed. Rather than assuming the cause, management should review pricing, product mix, visibility, customer demand, and marketing performance to determine the most appropriate response.
3. Build on strong-performing categories and customer segments: Electronics, Home Appliances, and the Adult customer segment are strong contributors to revenue. Understanding what drives their performance can help inform product, marketing, and customer retention strategies while avoiding over-reliance on a single segment or category.
 4. Review marketing channel performance: Social Media and Organic Search generate stronger revenue than Paid Ads in the analysis. Before reallocating significant marketing spend, management should compare channels using acquisition cost, conversion, customer quality, and repeat purchasing to determine where additional investment is most justified.
5. Investigate conversion and customer retention: The **77.3% drop-off between engagement and conversion** and the **8.89% repeat-purchase rate** highlight areas of the customer journey that deserve closer attention. Reviewing the points where customers disengage and strengthening post-purchase engagement could help identify opportunities to improve conversion and retention.
6. Investigate customer feedback and changes in performance over time: The high level of negative sentiment in Beauty and the decline in revenue after the August peak both warrant further investigation. Reviewing customer feedback, product issues, marketing activity, inventory availability, and other relevant business factors can help determine the underlying causes before making significant changes.

## Limitations
This analysis provides a view of business performance based on the data available, but there are some limitations to consider:
* **Revenue vs. profitability:** The analysis focuses primarily on revenue. Cost and margin data were not available, so the findings do not indicate which areas are most profitable.
  
* **Marketing efficiency:** Channel performance was assessed using available revenue and customer activity data. Without channel-level marketing spend, metrics such as CAC, ROAS, and ROI could not be reliably calculated.

* **Limited time period:** The available data covers a defined period, which limits the ability to determine whether observed revenue patterns are recurring seasonal trends.

* **Underlying drivers:** The analysis identifies differences in performance but does not always explain their underlying causes. Additional information such as inventory availability, pricing, competitor activity, and customer experience would support deeper diagnosis.

These limitations were considered when interpreting the findings and recommendations.

## Tools Used
* **Microsoft Excel** - Data cleaning, analysis, modelling, calculations, and dashboard development
* **Power Query** - Data cleaning, transformation, and preparation
* **Power Pivot** - Data modelling and relationships between datasets
* **PivotTables & PivotCharts** - Exploring performance patterns and building interactive analysis
* **Excel Formulas** - Calculations and supporting analysis

## What I Learned
This project reinforced that good analysis is not just about finding the highest or lowest number. The more important question is what the difference means for the business and what additional information may be needed before making a decision.

I also learned the importance of connecting different parts of a business story. Looking at sales alongside customer segments, marketing channels, product performance, and customer feedback made it easier to see relationships that would have been missed by analysing each area separately.

Most importantly, the project strengthened my ability to distinguish between **what the data shows, what it suggests, and what still needs to be investigated**. That distinction helped me make recommendations that were grounded in the available evidence rather than assumptions.




