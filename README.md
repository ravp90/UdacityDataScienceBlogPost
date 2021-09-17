# UdacityDataScienceBlogPost
Exploring data to unlock insights

## Table of Contents
1. [Introduction](#intro)
2. [Prerequisites](#prereq)
3. [Repository Structure](#repo)
4. [Results Summary](#results)
5. [Medium Article](#med)
6. [License](#lic)
7. [Acknowledgments](#ack)

<a name="intro"></a>
## Introduction
Three datasets are provided by Starbucks. The first is a list of 10 promotions that were sent to customers, the second is a list of 17,000 customers with limited demographics information and the third is a transcript which details when each customer received, viewed and completed and offer and when they completed a transaction. 

The CRISP-DM framework has been applied to generate 3 business questions from this data:
1. Do individuals spend more in store if they have a higher income?
2. Do older customers spend more than younger customers?
3. What is the difference in average spend between the three genders?

To answer these questions, the data must first be cleaned and processed. The following steps were performed:
For the customer profile (demographics) data:
* Data was checked for nulls and duplicates. The nulls were dropped because null gender and income values cannot be meaningfully imputed from the other data available. 

For transcripts data:
* The value column contains JSON objects which include offer infromation and transactions. This column was converted to a pandas dataframe and merged back into the main table. 
* All data not related to transactions were dropped, and the columns related to offers and rewards were also dropped. 
* The transactions were aggregated by each customer to find the total spend per customer during the 30 day period. 

The transactions data was merged with the demographics data creating one data table with customer ID, amount spent, gender, age and income. This table was then used to answer the questions. 

<a name="prereq"></a>
## Prerequisites
The Jupyter Notebook provided in this repository uses the following:
- Python 3.6
- numpy
- pandas
- matplotlib
- math
- json

<a name="repo"></a>
## Repository Structure
The repository is structured as follows:
- data folder 
  - portfolio.json - list of promotions
  - profile.json - list of customers and their demogrpahics
  - transcript.json - list of customer transactions and interactions with offers
- Data Science Blog Post - Starbucks Data Notebook.ipynb - the notebook containing data cleaning, pre-processing and visualisations  
- README.md - this file

<a name="results"></a>
## Results Summary
The answers to the questions can be summarised as follows: 
1. Do individuals spend more in store if they have a higher income?
For a given income, the mean of the spend was higher than the median, indicating that for each income the spend is skewed high. As income increases there is also a clear increase in the average customer spend. The relationship breaks down at an income over 100,000. 

2. Do older customers spend more than younger customers?
For a given age, there is a higher mean than median which also indicated a spend that is skewed high. From the age of 20 to 50, there appears to be a gradual increase in spend by customers. But customers over 50 appear to spend a similar amount on average. The relationship breaks down at ages over 95, but there are also less than 15 people per age after 95 so the statistics are likely to be skewed by a smaller sample size. 

3. What is the difference in average spend between the three genders?
It appears that females spend 41% more than males on average, with people who identify as the other gender sit somewhere in between. There were almost 6000 females and over 8000 males in the dataset, as compared to just over 200 other, so there is a greater confidence in the prediction that females spend more than males, than to say those who identify as the other gender also conclusively spend more than males. 

<a name="med"></a>
## Medium Article
An article has been published on Medium which is the full report that covers the data exploration through to modelling and conclusions. The article can be found [here](https://medium.com/@r.parekh90/extracting-insights-from-data-starbucks-promotional-dataset-6282ccad98ec).

<a name="lic"></a>
## License
This project is created using some content (data and code) provided by Udacity and Starbucks under the Data Scientist Nanodegree. The code is customised by the author of this repository. The author declares that the customised code is free to use and waives all copyright or related rights to this work.

<a name="ack"></a>
## Acknowledgements
* [Udacity Data Scientist Nanodegree](https://www.udacity.com/course/data-scientist-nanodegree--nd025)
* Starbucks
