# Wikipedia-Editors

The aim of this project is to use time series analysis to analyze the monthly number of unique editors for Wikipedia.

### Data Source
https://stats.wikimedia.org/#/metrics/en.wikipedia.org
I used the editors, total views, and legacy views (for data earlier than 2016) metrics and selected monthly data (daily is also available).
The editors include all contributors of at least 1 change (Wikipedia also tracks the number of active editors with at least 5 edits. The two series have similar trends, although more than 90% of editors are not active). The page views include all agent types, although most of the hits reflect human traffic.

### Summary
I trained the model on all available data starting in 2001 and trained it on the last 2 years of data. The baseline model had a mean absolute error of 31,300.
The best performing model was a Holt Winters model with multiplicative trend and seasonal factors, scoring a mean absolute error of 15,500. The next best model was a SARIMA(0,1,0)x(1, 0, 0, 12) with mean absolut error of 17,100.
I also tried using a SARIMAX model with page views and monthly difference of page views as exogenous predictors. This worsened performance to a mean absolute error of 24,900. I hypothesize this is reflecting the increase in readership during the pandemic that did not correspond to an increase in the number of editors.