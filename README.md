# Call Center Report



### Table Content 

- [Project Overview](project-overview)
- [Data Source](data-source)
- [Tools](tools)
- [Data Cleaning and Transformation](data-cleaning-and-transformation)
- [Exploratory Analysis](exploratory-analysis)
- [Recommendations](recommendations)
- [References](references)

### Project Overview
This projects shows the analysis of a Call Center for October, 2020. In full details of the necessary KPIs needed to drive 
the growth and relevant Decision Making.

![Sales data with MJ_page-0001](https://github.com/user-attachments/assets/6e6514d0-0196-41b0-8080-9b7d4d321eae)

### Data Source
The primary source for the data is [Download Here](https://github.com/toyinyayu/Call_Center-Analysis/edit/main/README.md#exploratory-data-analysis) files, containing the day to day details of aall customers calls for the month of October 2020.

### Tools
- Excel - Data Cleaning and Dashboard
- SQL Server - Data Analysis

### Data Cleaning and Transformation

In the initial data preparation stage, I perform the following:

- Data Loading and Inspection
- Handling Missing Values
- Data Cleaning and Analysis

### Exploratory Data Analysis

- What is the total number of calls?
- What is the Average Satisfactory Calls?
- What is the Average Call Duration in Mins?
- What is the Call trends for the whole month?
- What is the Call Channel by total Call Center?
- How many Call Center By City?
- What are the highest reason for Customers Calls?
- What is the timeframe for Customers call?

## Total Calls

~~~ sql
SELECT COUNT(id) AS Total_calls
  FROM [call_center].[dbo].[call_center]
~~~

## Average Satisfactory Score

~~~ sql
SELECT 
	ROUND(AVG(CAST(csat_score AS DECIMAL(10, 2))), 2) AS Avg_Satisfactory_Call
 FROM call_center.dbo.call_center
 WHERE csat_score IS NOT NULL AND csat_score <> 0 ;
~~~

## Average Call Duration by MIn

~~~ sql
SELECT 
	ROUND(AVG(CAST(call_duration AS DECIMAL(10, 2))), 2) AS Avg_Call_Duration_by_Mins
  FROM
	call_center.dbo.call_center;
~~~

## Call Trend
~~~ sql
SELECT call_timestamp, COUNT(call_center) AS COUNT_OF_CALL_CENTER
	FROM 
		call_center.dbo.call_center
	GROUP BY
	call_timestamp
	ORDER BY
	call_timestamp ASC;
~~~

## Call Channels by Call Center

~~~ sql
SELECT channel, COUNT(call_center) AS call_channel_by_call_center
  FROM [call_center].[dbo].[call_center]
  GROUP BY channel 
  ORDER BY call_channel_by_call_center DESC
~~~

## State by Call Center

~~~ sql
SELECT state, COUNT(call_center) AS Call_Center_by_City
FROM
call_center.dbo.call_center
GROUP BY 
state
ORDER BY
state ASC;
~~~

## Reason for Calling

~~~ sql
SELECT reason, COUNT(call_center) As Call_Reason
FROM 
call_center.dbo.call_center
GROUP BY reason
ORDER BY reason ASC;
~~~

Response Time by Call Center

~~~ sql
SELECT 
response_time, COUNT(call_center) As Call_Response_Time
FROM 
call_center.dbo.call_center
GROUP BY response_time
ORDER BY response_time DESC;

~~~

## Recommendations

- To open more centers in some states
- To reduce the call duration by promoting other channels
- To send emails as often
  



