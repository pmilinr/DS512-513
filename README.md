# DS512-513
# Analyzing Factors Influencing Hotel Booking Cancellations to Enhance Sales Strategy

## Overview
   The hotel industry is rapidly transforming as digital platforms make booking easier and more convenient for guests. While this brings new opportunities, it also creates challenges, especially for hotels that want to reduce reliance on third-party platforms and manage bookings more efficiently. 

   One major issue is the rising rate of booking cancellations, which impacts revenue and room planning. This project analyzes hotel booking data to uncover the key factors driving cancellations and provide insights that help hotels improve forecasting, operations, and profitability.
   
---
## Problem Statement & Key Questions
 1. Which countries have the highest and lowest cancellation rates among the Top 10 booking countries?
 2. How do customer type, market segment, deposit type, and distribution channel influence the likelihood of booking cancellations, and which groups exhibit the  highest cancellation risk?
 3. Which features (lead time, ADR, room type, customer type, etc.) show the strongest relationship with cancellation?
   - Does longer lead time significantly increase the likelihood of cancellation?
   - Are price-sensitive customers (high ADR or discounts) more likely to cancel?
   - Does longer stay increase cancellation rate?
     

                                  The chart shows the revenue impact caused by booking cancellations.
![booking and revenue](https://github.com/user-attachments/assets/ee53147b-242e-43e1-99e1-ffd6d6b1a16f)


---
## Value Propositions
   Our analysis identifies the key factors that most strongly influence booking cancellations, such as lead time and ADR, enabling hotel owners to optimize revenue planning, allocate staff efficiently, and reduce operational uncertainty.

With data-driven strategies informed by the cancellation model, the hotel is expected to increase revenue by up to 30% within 6 months.

---
## Dataset Description
   This dataset contains 119390 observations for a City Hotel and a Resort Hotel. Each observation represents a hotel booking between the 1st of July 2015 and 31st of August 2017, including booking that effectively arrived and booking that were canceled.

---
## Data Dictionary

<img width="1001" height="1801" alt="datadic" src="https://github.com/user-attachments/assets/232618aa-c663-454a-af2b-5b6a9e709dcc" />


---
# Exploratory Data Analysis (EDA)
---
## Data Cleaning & Preparation
- Remove:
     - Duplicate records
     - Rows with missing / NULL values (where appropriate)
     - Outliers (extreme ADR values)
- Adjust column types to appropriate dtypes (e.g., dates, integers, categories).
- Creating Total Guests (Adult + Children + Babies)
- Result after cleaning:
     - **87,108 rows**
     - **30 columns**

---
# Data Analysis & Key Findings

---
**1. Top 10 Countries by Cancellation Rates**

Map of top booking countries
Stacked bar chart: Canceled vs Not Canceled for Top 10 countries

![Top_10_Booking_and_cancel_2](https://github.com/user-attachments/assets/4a9f0cae-cc77-4eea-bd25-155c4f42e63e)

**Key Findings:**
1. Brazil, Italy, and Portugal show the highest cancellation ratios (≥30%).
2. High booking volume ≠ high cancellation rate.
3. Countries like France, UK, Germany have high total bookings but lower cancellation percentages (<25%).
4. Western Europe remains the hotel’s core market, but targeted strategies may be required for countries with unstable booking behavior.
5. Countries with high cancellation propensity should be flagged as High-Risk Market Segments for more controlled booking policies.

**Summarize:**
Italy, Brazil, and Portugal show the highest cancellation rates despite high booking volumes, while Germany, the UK, and the Netherlands remain the most stable markets.

---
**2. Customer Type, Market Segment, Deposit Type, and Distribution Channel**

Visualization: Multiple stacked bar charts

![Cancellation Factors-1](https://github.com/user-attachments/assets/70a1192f-e770-4afb-9c5a-d24528666768)


**Key Findings:**
1. Customer Type: Transient customers have the highest cancellation rate (≈30%).
2. Market Segment: Online TA (Online Travel Agencies) shows the highest cancellation rate (≈35%).
3. Deposit Type:No-Refund bookings have extremely high cancellation rates (>95%).
4. Distribution Channel:TA/TO (Travel Agents / Tour Operators) shows high cancellation rates (>30%).

**Summarize:**
- Cancellation tendency depends heavily on: who books (customer type), how they book (distribution channel), payment conditions (deposit type)
- The riskiest groups are: Online TA, TA/TO, Transient customers and No-refund deposit bookings.

---
**3.Correlation**

Visualization: Pearson correlation table

![Correl](https://github.com/user-attachments/assets/77f897ab-c158-47f4-ab84-f3b1eab7063a)


**Key Findings:** 
  Most relevant factors associated with cancellation :
   1. Lead Time
   2. ADR
   3. Stay in week night 

Arrival Year was excluded from the analysis due to significant data imbalance. Since only the year 2016 contains complete observations, including this feature would introduce bias and reduce the validity of the results.
      
**Summarize:**
Lead time and ADR are the most influential positive predictors of cancellation in this dataset

---
**4. Lead Time vs Cancellation**

Visualization: Histogram + Boxplot comparing Lead Time for Canceled vs Not Canceled bookings.

![Lead_time](https://github.com/user-attachments/assets/35d4e9cf-bef5-47d2-a66c-ce139711d547)

**Key Findings:**
1. Canceled bookings have substantially higher Lead Time compared to non-canceled bookings.
2. The median Lead Time for canceled bookings is around 55–60 days, which is higher than the median for non-canceled bookings (approximately 35–40 days).
3. Guests who book far in advance tend to cancel more frequently.
4. Long lead times may indicate uncertainty or flexible travel plans, increasing likelihood of cancellation.

**Summarize:**
Guests who book far in advance tend to cancel more frequently.

---
**5. ADR (Average Daily Rate) vs Cancellation**

Visualization: Bar chart showing average ADR for each cancellation group
Boxplot + histogram for ADR distribution

![ADR_cancel](https://github.com/user-attachments/assets/84dbebb9-853b-46c4-86ba-0b7d0f33f61e)

**Key Findings:**
1. Canceled bookings also peak around 70–150, but show more bookings in higher ADR ranges compared to non-canceled.
2. Canceled bookings have ~18% higher ADR.
3. High-value bookings (ADR > 400) appear mostly in the canceled group.
4. Suggests price sensitivity increases cancellation likelihood.

**Summarize:**
Higher ADR bookings show a higher cancellation tendency, with canceled reservations having ~18% higher ADR on average and a wider distribution, indicating high-priced bookings are more likely to be canceled.

---
**6. Length of Stay (Week Nights) vs Cancellation**

Visualization: Boxplot comparing week-night stays and Histogram of stay durations

![stay_in_week_night](https://github.com/user-attachments/assets/bbc85aec-98e9-401f-bcad-a5dff7cd8698)

**Key Findings:**
1. Canceled bookings also peak around 1–4 nights, similar to non-canceled.However, the distribution shows more bookings in higher night counts (5–7 nights) compared to non-canceled.
2. Medians are similar for both groups, but overall, cancellation likelihood increases as week-night stays increase.
3. Long-stay bookings exhibit higher risk.

**Summarize:**
Cancellation rates rise as week-night stays increase. Long-stay bookings show the highest cancellation risk, while short stays remain more stable.

---
**7. Forecast of Monthly Booking Cancellations**

Visualization: Line chart with forecast shading
- Shows upward trend of cancellations.
- Peak cancellations during July–August.

![forecast](https://github.com/user-attachments/assets/a9680ab1-178b-4ddd-a62c-01ac6e44745c)


**Key Findings:**
1. Cancellations rise steadily across the years, especially through 2018.
2. Cancellation rates start rising in March–May.
3. They reach their highest levels in July–August every year,athough Portugal’s tourist high season = June–August, cancellations peak before the actual travel period.
4. Customers may shop around during early months and cancel early bookings.
5. Hotels should adjust deposit or lead-time policies in high-risk months.

---
## **Summarize**

**Key behavioral patterns identified:**
1. It was found that as the lead time increases, the likelihood of a booking being canceled also rises.
2. A higher Average Daily Rate (ADR) also tends to increase the chance that customers will cancel their reservations.
3. Countries with the highest cancellation rates include Italy, Brazil, and Portugal.
4. Online Travel Agencies and non-refundable bookings have the highest cancellation risks.
5. Seasonal patterns show cancellation clusters during March–May and peak during July–August, showing a clear seasonal pattern where guests typically cancel 1–3 months before the high tourism season..
6. Long-stay reservations are disproportionately represented among canceled bookings.

---
## **Recommendation/Action**

1. Reduce the maximum advance booking period to no more than 360 days (from two years to one year).
2. Adjust booking strategies by requiring a 30% deposit at the time of reservation or shortening the payment deadline, especially for high-risk segments such as OTA bookings, long lead-time reservations, high-ADR bookings, and guests fr
3. Provide flexible pricing or perks for high-ADR bookings to reduce price sensitivity.
4. Apply stricter cancellation or deposit policies to countries with historically high cancellation rates.
5. Negotiate terms with OTAs for stricter cancellation rules.
6. Offer direct-booking benefits to shift customers from OTA channels.
7. Require partial prepayment for reservations > 7 nights.
8. Provide stay packages or discounts to lock in longer stays.
9. March–August is a critical risk window for revenue loss.
    - Shortening payment deadlines
    - Implementing stricter deposit requirements
    - Offering price incentives to secure bookings earlier
11. Improve customer communication by implementing automated reminders and pre-stay confirmations.
12. Develop a machine learning model to predict booking cancellations.

---
## **Impact**
1. Reduces revenue loss from customers who cancel "early-booked rooms."
2. Increases retention among high-value bookings.
3. Reduction in cancellations from markets with unstable booking behavior.
4. Lower cancellations from the highest-risk booking channel.
5. Protects potential revenue lost from canceled long-duration stays.
6. Reduce unintentional cancellations and decrease the incidence of no-shows
