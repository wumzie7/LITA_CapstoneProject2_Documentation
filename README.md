# LITA_CapstoneProject2_Documentation

### Project Title:  Customer Segmentation for a Subscription Service 


[Project Overview](#project-overview)

[Data Sources](#data-sources)

[Tools Used](#tools-used)

[Data Cleaning and Preparations](#data-leaning-and-preparations)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)

### Project Overview

```
This project involves analyzing customer data for a subscription service to identify segments and trends. 
The Data Analysis goal is to understand customer behavior, track subscription types, and identify key trends in cancellations and renewals. 
```

### Data Sources
```
The primary source of Data used here is Data Sale.csv and this is an open source data that can be freely downloaded from an open source online such as Capstone or kaggle or FRED or any other repository site.
```

### Tools Used

```
- Microsoft Excel 
    1. For Data Cleaning [Download Here](https://www.microsoft.com)
    2. For Data Analysis
    3. For Data Visualization
       
- SQL - Structured Query language for Quering of Data
- Microsoft Power Bi Desktop
- GitHub for Portifolio Building
```

### Data Cleaning and Preparations

```
In the initial phase of the data cleaning and preparations, I perform the following actions;
1. Data Loading and Inspection
2. Handling missing variables
3. Removing duplicates
4. Data cleaning and formatting
```

### Exploratory Data Analysis

```
EDA involved the exploring of the Data to answer some questions about the Data such as;
- What is the subscription patterns?
- What is average subscription duration? 
- Which subscription type is the most popular? 
```

  ### Data Analysis

  Microsoft Excel
```

[LitaCustomerData_Solution.xlsx](https://github.com/user-attachments/files/17654304/LitaCustomerData_Solution.xlsx)

```


SQL

This is where we include some basic lines of code or queries during analysis;
  
  This is where we include some basic lines of code or queries or even som of the DAX expressions used during analysis;


``` SQL
  create database LISAPROJECT1
  select * from [dbo].[LitaCustomerData]

--- Total number of customers from each region---
    select Region, sum(CustomerId) as TotalNumberOfCustomers from [dbo].[LitaCustomerData]
    group by Region

--- The most popular subscription type by the number of customers---
    select top 1 SubscriptionType, max(CustomerId) as NumberOfCustomer, 
    sum(CustomerId) as MostPopularSubscription from [dbo].[LitaCustomerData]
    group by SubscriptionType

--- Customers who canceled their subscription within 6 months---
    select top 11 CustomerId, CustomerName, Canceled  from [dbo].[LitaCustomerData]
    where Canceled = 0 and datediff(month, SubscriptionEnd, SubscriptionStart)<=6 

--- Average subscription duration for all customers---
    select CustomerId, AVG(SubscriptionDuration) as AverageSubscriptionDuration
    from [dbo].[LitaCustomerData]
    group by CustomerId

--- Customers with subscriptions longer than 12 months---
    select CustomerId, CustomerName, SubscriptionDuration from [dbo].[LitaCustomerData]
    where Canceled = 1 and datediff(month, SubscriptionEnd, SubscriptionStart)>12 


--- Total revenue by subscription type---
    select SubscriptionType, sum(Revenue) as TotalRevenue
    from [dbo].[LitaCustomerData]
    group by SubscriptionType

--- The top 3 regions by subscription cancellations---
    select top 3 Region from [dbo].[LitaCustomerData]
    where Canceled = 0
    group by Region


--- Total number of active and canceled subscriptions---
    select count(canceled) as TotalActive from [dbo].[LitaCustomerData]
    where Canceled = 1 
    select count(canceled) as TotalCanceled from [dbo].[LitaCustomerData]
    where Canceled = 0
```

### Data Visualization 

Here I build a Power BI dashboard that visualizes key customer segments, cancellations, and subscription trends. Include slicers for interactive analysis. 

![LitaCustomerData](https://github.com/user-attachments/assets/51831912-6e68-4903-b99d-0d10349839e6)

![LitaCustomerData](https://github.com/user-attachments/assets/643ce033-aae4-4d10-9a5b-8e09306433ea)




