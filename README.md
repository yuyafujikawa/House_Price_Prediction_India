# House_Price_Prediction_India
House Price Prediction - Classic regression problem.

Data Source: https://www.kaggle.com/datasets/iamsouravbanerjee/house-rent-prediction-dataset

### Possible future endeavour

#### Consider other alternatives for feature selections. In this case I have simply retained features with correlation value > 0.2
```
cor = col_all_int.corr()
cor_target = abs(cor["Rent"])
relevant_cor = cor[cor_target>0.2]
relevant_cor = relevant_cor[relevant_cor.index]
```
#### Consider other alternatives for outliers removal. In this case, I have simply employed the 1.5 * IQR method. As for col_int_final['Rent']<600000, this value was chosen visually after a displaying a scatterplot.

```
for x in ['Size']:
    q75,q25 = np.percentile(col_int_final.loc[:,x],[75,25])
    intr_qr = q75-q25
 
    max_val = q75+(1.5*intr_qr)
    min_val = q25-(1.5*intr_qr)
    
col_int_final = col_int_final[(col_int_final['Size']>min_val) & (col_int_final['Size']<max_val) & (col_int_final['Rent']<600000)]

```

