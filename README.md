### Business Understanding

### For car dealers, we provide overall understanding of what makes car value change. This is very important to handle the car stock and to sell cars communicating with customers. In this report we will share the analaysis results in terms of coefficiency of each attribute as much as possible.

### Data Understanding
##### 1. Overall data: Check how many data and columns are in the data set to see if we can handle them all in a reasonable process time
##### 2. Column data type: Check numerical or categorical. As needed change the data type to the appropriate ones
##### 3. Data contents: Check null data existence and decide either to remove them or fill them out with alternate data
##### 4. Column price dependency: Identify no price dependency columns and eliminate them
##### 5. Column selection: Check how many columns are in the data set and what columns we should keep or drop
##### 6. Data review: Check price distribution and counts by each column
##### 7. Data integrity: Remove unreasonable outliners so the data analysis result will not be distorted

### Data Preparation
#####  - Overall data: 426K data in the data set. This could be a little bit large number to handle with a limited PC processing speed.
#####  - Eliminate obvious non price dependant columns. ("id", "VIN")
#####  - Confimred some of the columns such as size have so many missing data. If we eliminate all the data with null, only 79K data remains.
#####  - Keep null data by filling out with missing. (421K data)
#####  - Cut off potential outliers, just in case and keep the data with odometer < 300000, price<100000, and year>1990


### Modeling
#### Price Modeling using only Odmeter and Year.
#### Price Modeling using all calumns as much as possible

### Evaluation
##### In this type of data the simple liner regression makes sense. We do not want to drop clumns by using LASSO. Ridge requires essentially scaler standardization, which makes the result difficult to understand for dealer peopole. Also linear regresstion without higher order does not makes sense since we have so many factors we need to handle already adding the higher order makes it higher cost in terms of computing.

### Deployment

#### Based on the data, here are the findings

Year: +$900 value per year

Odometer: -$700 (negative) value every 10K miles

Condition: Based on the data analysis result, it does not seem the result gives us a reasonable price difference between new and others. But this looks effect is in the range of +/-$700 depending on the condition.

Drive     : +$3,000 value for 4WD and -4,000 value for fwd

Fuel      : +$11,000 value for diesel, - 4,000 value for Gas

Color     : +/-$1,000 range price difference depending on the color

Size      : +$200 value for full size followed by smaller size

Title     : +/-$5,000 range influence depending on the item

Transmission: +$400 value for manual, which is a little bit surprising, but maybe this is caused by a potential correlation between a manual and a specialty sports car. In this data analysis, we did not use the "model" or "manufacturer" due to too much complexity, so that could affect this result.

Type      : +/-5000 range difference depending on the type.

In detail, please check the coefficient tables above for more insight. When dealing the car trading, please use this as a reference for the price estimation. Below is the formula from the model to find the quick price estimation using year and odometer only. Based on this quick formula you can just adjust based on the differences of each category value from the list above.

##### Base Price = (892.524269 * year) - (0.068467 * odometer) - (1771726)
