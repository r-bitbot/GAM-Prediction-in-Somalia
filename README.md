# Global Acute Malnutrition (GAM) Prediction in Somalia
This project aims to predict the Global Acute Malnutrition (GAM) prevalence in Somalia using machine learning methods. Leveraging data from Somalia Food Security and Nutrition Analysis Unit (FSNAU) for district level forecasting of global acute malnutrition. The goal is to provide insights for actionable intervention and prepare for rises in GAM.

## Objectives

## To Run Locally
The project is designed for local Jupyter Notebook executiom. To run it locally:
```
git clone https://github.com/r-bitbot/GAM-Prediction-in-Somalia.git
cd GAM-Prediction-in-Somalia
jupyter notebook
```
Ensure you have all the libraries installed (via pip or conda).

## Tools and Libraries Used
* Python 3.7 and above
* Jupyter Notebook
* pandas: For data manipulation and cleaning
* numpy: For numerical operations
* scikit-learn: For machine learning (Random Forest, Gradient Boosting)
* matplotlib and seaborn: For data visualization
* requests and urllib: For data fetching from FSNAU APIs

## Methodology
### Data Collection
From FSNAU, the datasets of [GAM](https://dashboard.fsnau.org/nutrition/gam), [rainfall](https://dashboard.fsnau.org/climate/rainfall), [NDVI](https://dashboard.fsnau.org/climate/ndvi), [incidents](https://dashboard.fsnau.org/insecurity/incidents), [fatalities](https://dashboard.fsnau.org/insecurity/fatalities), and [crops](https://crops.fsnau.org/) were manually taken from the duration of January 2017 to December 2019.

### Data Preprocessing
Missing data was handled and datasets were cleaned up using Pandas. Normalization and feature engineering were also leveraged. 

### Exploratory Data Analysis
Trends were visualized using predictors such as monthly and annual factors of rainfall, NDVI, incidents, fatalities, and crop production. Analysis of each district and region was done by leveraging graphs drawn against monthly and annual GAM to see which factors affected GAM values.

### Feature Selection
Environmental factors like rainfall, NDVI, and crop production was taken into account. Conflicts like incidents and fatalities were included. Previous months' malnutrition trends were also noted, along with lagged variables of all of the above. 

### Models
The XGBoost model was trained based on environmental and food security indicators, and finetuned with every experimental run to produce the best possible results. Lagged Variables were critical for capturing delayed effects of shocks (drought, conflict) on malnutrition. 
The model was used to predict:
* Monthly GAM from concurrent and lagged factors.
* Annual GAM from all annualized factors.

## Results and Insights 
Key predictors in some regions were incidents and fatalities, with 
* Rainfall and NDVI were strong indicators in predicting GAM, and this relation was prevalent in agro-pastural districts.
* Conflict related factors added predictive value, particularly in regions of high conflict.
* Including previous months' GAM and lagged environmental variables imrpoved model accuracy.

### Notes 
In southern and central Somalia, areas of chronic conflict and low rainfall (mainly parts of Bakool, Gedo, Shabelle, and Banadir) suffered the highest trends in GAM. The drivers were:
* Low and highly variable rainfall, poor vegitation, and repeated crop faliures.
* These areas were frequently subjected to explosive violence, and showed higher rates of malnutrition (likely due to health service disruption, food insecurity, and displacement).
* Low crop production areas tend to show a higher GAM level.
* Malnutrition generally peaked in areas with recent droughts and conflict periods, and in lean seasons of crop production.

Additional insights:
* Temporal Lags: Many districts showed a 1-3 month lag between shocks (drought, spike in incidents) and increases in GAM, a factor that could be used to anticipate GAM peaks.
* Spatial Clustering: Persistent high-GAM clusters overlapped with both environmental stress zones and conflict-prone regions, which have multiple factors that enable the region's vulnerability.
* Predictive Limitations: While models perform well overall, districts with changing conflict patterns or rapid environmental shifts displayed more unpredictable GAM changes, highlighting areas needing more granular or real-time data.
  - Districts with changing conflict patterns:
     - Hiraan (Beledweyne, Bulo Burte), house unrest within their region that rise during and following drought periods. Their sudden shifts in conflicts disrupt aid.
     - Galmudug has experienced irregular shifts in local control and conflicts, leading to sharp and rapid changes in nutrition levels.
     - Banadir (Mogadishu) experience rapid migration and unpredictable patterns of violence, both of which cause spikes in malnutrition rates.
  - District with rapid environment shifts:
     - Mudug has the fastest shifting drought and flood conditions in Somalia with extreme weather conditions in recent years.
     - Shabelle riverine districts (Jowhar, Balcad, Afgoye) are prone to both floods and droughts that occur in quick succession, 

## Key Learnings
