```python
#importing pretty much everything I think I might need for this assignment
import csv
import matplotlib as mpl
import plotly
import pandas as pd
import sqlite3
```


```python
dfapi = pd.read_csv("API_SE.PRM.ENRL_DS2_en_csv_v2_4538564.csv", header=2, low_memory=True)
dfapi

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country Name</th>
      <th>Country Code</th>
      <th>Indicator Name</th>
      <th>Indicator Code</th>
      <th>1960</th>
      <th>1961</th>
      <th>1962</th>
      <th>1963</th>
      <th>1964</th>
      <th>1965</th>
      <th>...</th>
      <th>2013</th>
      <th>2014</th>
      <th>2015</th>
      <th>2016</th>
      <th>2017</th>
      <th>2018</th>
      <th>2019</th>
      <th>2020</th>
      <th>2021</th>
      <th>Unnamed: 66</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Aruba</td>
      <td>ABW</td>
      <td>Primary education, pupils</td>
      <td>SE.PRM.ENRL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>9803.0</td>
      <td>9816.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Africa Eastern and Southern</td>
      <td>AFE</td>
      <td>Primary education, pupils</td>
      <td>SE.PRM.ENRL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Afghanistan</td>
      <td>AFG</td>
      <td>Primary education, pupils</td>
      <td>SE.PRM.ENRL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>5986268.0</td>
      <td>6217756.0</td>
      <td>6199329.0</td>
      <td>6265011.0</td>
      <td>6350404.0</td>
      <td>6544906.0</td>
      <td>6777785.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Africa Western and Central</td>
      <td>AFW</td>
      <td>Primary education, pupils</td>
      <td>SE.PRM.ENRL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>AGO</td>
      <td>Primary education, pupils</td>
      <td>SE.PRM.ENRL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5620915.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>261</th>
      <td>Kosovo</td>
      <td>XKX</td>
      <td>Primary education, pupils</td>
      <td>SE.PRM.ENRL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>262</th>
      <td>Yemen, Rep.</td>
      <td>YEM</td>
      <td>Primary education, pupils</td>
      <td>SE.PRM.ENRL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>3874741.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3900134.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>263</th>
      <td>South Africa</td>
      <td>ZAF</td>
      <td>Primary education, pupils</td>
      <td>SE.PRM.ENRL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>7063849.0</td>
      <td>7195183.0</td>
      <td>7555842.0</td>
      <td>7569924.0</td>
      <td>7582154.0</td>
      <td>7568387.0</td>
      <td>7688381.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>264</th>
      <td>Zambia</td>
      <td>ZMB</td>
      <td>Primary education, pupils</td>
      <td>SE.PRM.ENRL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>3075161.0</td>
      <td>3217872.0</td>
      <td>3215723.0</td>
      <td>3203220.0</td>
      <td>3284841.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>265</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Primary education, pupils</td>
      <td>SE.PRM.ENRL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>2663187.0</td>
      <td>NaN</td>
      <td>2658415.0</td>
      <td>2662010.0</td>
      <td>2676485.0</td>
      <td>2725970.0</td>
      <td>2789692.0</td>
      <td>2869735.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>266 rows × 67 columns</p>
</div>




```python
dfwd =  pd.read_csv("WDIData.csv", header=0, low_memory=True)
dfwd

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country Name</th>
      <th>Country Code</th>
      <th>Indicator Name</th>
      <th>Indicator Code</th>
      <th>1960</th>
      <th>1961</th>
      <th>1962</th>
      <th>1963</th>
      <th>1964</th>
      <th>1965</th>
      <th>...</th>
      <th>2013</th>
      <th>2014</th>
      <th>2015</th>
      <th>2016</th>
      <th>2017</th>
      <th>2018</th>
      <th>2019</th>
      <th>2020</th>
      <th>2021</th>
      <th>Unnamed: 66</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Africa Eastern and Southern</td>
      <td>AFE</td>
      <td>Access to clean fuels and technologies for coo...</td>
      <td>EG.CFT.ACCS.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>16.936004</td>
      <td>17.337896</td>
      <td>17.687093</td>
      <td>18.140971</td>
      <td>18.491344</td>
      <td>18.825520</td>
      <td>19.272212</td>
      <td>19.628009</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Africa Eastern and Southern</td>
      <td>AFE</td>
      <td>Access to clean fuels and technologies for coo...</td>
      <td>EG.CFT.ACCS.RU.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>6.499471</td>
      <td>6.680066</td>
      <td>6.859110</td>
      <td>7.016238</td>
      <td>7.180364</td>
      <td>7.322294</td>
      <td>7.517191</td>
      <td>7.651598</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Africa Eastern and Southern</td>
      <td>AFE</td>
      <td>Access to clean fuels and technologies for coo...</td>
      <td>EG.CFT.ACCS.UR.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>37.855399</td>
      <td>38.046781</td>
      <td>38.326255</td>
      <td>38.468426</td>
      <td>38.670044</td>
      <td>38.722783</td>
      <td>38.927016</td>
      <td>39.042839</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Africa Eastern and Southern</td>
      <td>AFE</td>
      <td>Access to electricity (% of population)</td>
      <td>EG.ELC.ACCS.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>31.794160</td>
      <td>32.001027</td>
      <td>33.871910</td>
      <td>38.880173</td>
      <td>40.261358</td>
      <td>43.061877</td>
      <td>44.270860</td>
      <td>45.803485</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Africa Eastern and Southern</td>
      <td>AFE</td>
      <td>Access to electricity, rural (% of rural popul...</td>
      <td>EG.ELC.ACCS.RU.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>18.663502</td>
      <td>17.633986</td>
      <td>16.464681</td>
      <td>24.531436</td>
      <td>25.345111</td>
      <td>27.449908</td>
      <td>29.641760</td>
      <td>30.404935</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>383567</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women who believe a husband is justified in be...</td>
      <td>SG.VAW.REFU.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>14.500000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383568</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women who were first married by age 15 (% of w...</td>
      <td>SP.M15.2024.FE.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.700000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.418352</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383569</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women who were first married by age 18 (% of w...</td>
      <td>SP.M18.2024.FE.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>33.500000</td>
      <td>32.400000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>33.658057</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383570</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women's share of population ages 15+ living wi...</td>
      <td>SH.DYN.AIDS.FE.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>59.100000</td>
      <td>59.400000</td>
      <td>59.500000</td>
      <td>59.700000</td>
      <td>59.900000</td>
      <td>60.100000</td>
      <td>60.300000</td>
      <td>60.500000</td>
      <td>60.7</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383571</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Young people (ages 15-24) newly infected with HIV</td>
      <td>SH.HIV.INCD.YG</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>20000.000000</td>
      <td>19000.000000</td>
      <td>17000.000000</td>
      <td>15000.000000</td>
      <td>13000.000000</td>
      <td>10000.000000</td>
      <td>8600.000000</td>
      <td>7700.000000</td>
      <td>6800.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>383572 rows × 67 columns</p>
</div>




```python
dfapi.shape

```




    (266, 67)




```python
dfwd.shape
```




    (383572, 67)




```python
outer_merged = pd.merge(dfwd, dfapi, how="outer")
outer_merged.shape
```




    (383572, 67)




```python
outer_merged.tail(25)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country Name</th>
      <th>Country Code</th>
      <th>Indicator Name</th>
      <th>Indicator Code</th>
      <th>1960</th>
      <th>1961</th>
      <th>1962</th>
      <th>1963</th>
      <th>1964</th>
      <th>1965</th>
      <th>...</th>
      <th>2013</th>
      <th>2014</th>
      <th>2015</th>
      <th>2016</th>
      <th>2017</th>
      <th>2018</th>
      <th>2019</th>
      <th>2020</th>
      <th>2021</th>
      <th>Unnamed: 66</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>383547</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Use of insecticide-treated bed nets (% of unde...</td>
      <td>SH.MLR.NETS.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>26.800000</td>
      <td>9.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>14.900000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383548</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Value lost due to electrical outages (% of sal...</td>
      <td>IC.FRM.OUTG.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.100000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383549</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Vitamin A supplementation coverage rate (% of ...</td>
      <td>SN.ITK.VITA.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>34.000000</td>
      <td>32.000000</td>
      <td>45.000000</td>
      <td>35.000000</td>
      <td>43.000000</td>
      <td>40.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383550</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Vulnerable employment, female (% of female emp...</td>
      <td>SL.EMP.VULN.FE.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>75.089998</td>
      <td>75.339997</td>
      <td>75.640002</td>
      <td>75.970001</td>
      <td>76.579998</td>
      <td>77.170002</td>
      <td>79.299999</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383551</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Vulnerable employment, male (% of male employm...</td>
      <td>SL.EMP.VULN.MA.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>56.150000</td>
      <td>56.020001</td>
      <td>56.380001</td>
      <td>56.789999</td>
      <td>56.609999</td>
      <td>56.380000</td>
      <td>57.090001</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383552</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Vulnerable employment, total (% of total emplo...</td>
      <td>SL.EMP.VULN.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>65.739999</td>
      <td>65.800001</td>
      <td>66.139999</td>
      <td>66.500002</td>
      <td>66.720000</td>
      <td>66.910002</td>
      <td>68.349998</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383553</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Wage and salaried workers, female (% of female...</td>
      <td>SL.EMP.WORK.FE.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>24.590000</td>
      <td>24.360001</td>
      <td>24.049999</td>
      <td>23.719999</td>
      <td>23.120001</td>
      <td>22.559999</td>
      <td>20.440001</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383554</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Wage and salaried workers, male (% of male emp...</td>
      <td>SL.EMP.WORK.MA.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>43.160000</td>
      <td>43.310001</td>
      <td>42.939999</td>
      <td>42.520000</td>
      <td>42.750000</td>
      <td>43.020000</td>
      <td>42.360001</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383555</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Wage and salaried workers, total (% of total e...</td>
      <td>SL.EMP.WORK.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>33.770000</td>
      <td>33.720001</td>
      <td>33.369999</td>
      <td>33.000000</td>
      <td>32.810001</td>
      <td>32.650002</td>
      <td>31.250000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383556</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Wanted fertility rate (births per woman)</td>
      <td>SP.DYN.WFRT</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.600000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383557</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Water productivity, total (constant 2015 US$ G...</td>
      <td>ER.GDP.FWTL.M3.KD</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.307662</td>
      <td>5.853911</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383558</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Wholesale price index (2010 = 100)</td>
      <td>FP.WPI.TOTL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383559</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women Business and the Law Index Score (scale ...</td>
      <td>SG.LAW.INDX</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>86.875000</td>
      <td>86.875000</td>
      <td>86.875000</td>
      <td>86.875000</td>
      <td>86.875000</td>
      <td>86.875000</td>
      <td>86.875000</td>
      <td>86.875</td>
      <td>86.875</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383560</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women making their own informed decisions rega...</td>
      <td>SG.DMK.SRCR.FN.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>59.900000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383561</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women participating in the three decisions (ow...</td>
      <td>SG.DMK.ALLD.FN.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>72.100000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383562</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women who believe a husband is justified in be...</td>
      <td>SG.VAW.REAS.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>37.400000</td>
      <td>38.700000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383563</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women who believe a husband is justified in be...</td>
      <td>SG.VAW.ARGU.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>16.700000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383564</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women who believe a husband is justified in be...</td>
      <td>SG.VAW.BURN.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8.100000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383565</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women who believe a husband is justified in be...</td>
      <td>SG.VAW.GOES.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>22.800000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383566</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women who believe a husband is justified in be...</td>
      <td>SG.VAW.NEGL.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>21.400000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383567</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women who believe a husband is justified in be...</td>
      <td>SG.VAW.REFU.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>14.500000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383568</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women who were first married by age 15 (% of w...</td>
      <td>SP.M15.2024.FE.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.700000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.418352</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383569</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women who were first married by age 18 (% of w...</td>
      <td>SP.M18.2024.FE.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>33.500000</td>
      <td>32.400000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>33.658057</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383570</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Women's share of population ages 15+ living wi...</td>
      <td>SH.DYN.AIDS.FE.ZS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>59.100000</td>
      <td>59.400000</td>
      <td>59.500000</td>
      <td>59.700000</td>
      <td>59.900000</td>
      <td>60.100000</td>
      <td>60.300000</td>
      <td>60.500</td>
      <td>60.700</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>383571</th>
      <td>Zimbabwe</td>
      <td>ZWE</td>
      <td>Young people (ages 15-24) newly infected with HIV</td>
      <td>SH.HIV.INCD.YG</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>20000.000000</td>
      <td>19000.000000</td>
      <td>17000.000000</td>
      <td>15000.000000</td>
      <td>13000.000000</td>
      <td>10000.000000</td>
      <td>8600.000000</td>
      <td>7700.000</td>
      <td>6800.000</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>25 rows × 67 columns</p>
</div>




```python
outer_merged.to_csv('merged.csv')
```


```python
# Filter out rows where the country is not Argentina
filtered_df = outer_merged[outer_merged['Country Name'] == 'Argentina']
print(filtered_df.head(15))
```

          Country Name Country Code  \
    14420    Argentina          ARG   
    14421    Argentina          ARG   
    14422    Argentina          ARG   
    14423    Argentina          ARG   
    14424    Argentina          ARG   
    14425    Argentina          ARG   
    14426    Argentina          ARG   
    14427    Argentina          ARG   
    14428    Argentina          ARG   
    14429    Argentina          ARG   
    14430    Argentina          ARG   
    14431    Argentina          ARG   
    14432    Argentina          ARG   
    14433    Argentina          ARG   
    14434    Argentina          ARG   
    
                                              Indicator Name     Indicator Code  \
    14420  ARI treatment (% of children under 5 taken to ...     SH.STA.ARIC.ZS   
    14421  Access to clean fuels and technologies for coo...     EG.CFT.ACCS.ZS   
    14422  Access to clean fuels and technologies for coo...  EG.CFT.ACCS.RU.ZS   
    14423  Access to clean fuels and technologies for coo...  EG.CFT.ACCS.UR.ZS   
    14424            Access to electricity (% of population)     EG.ELC.ACCS.ZS   
    14425  Access to electricity, rural (% of rural popul...  EG.ELC.ACCS.RU.ZS   
    14426  Access to electricity, urban (% of urban popul...  EG.ELC.ACCS.UR.ZS   
    14427  Account ownership at a financial institution o...     FX.OWN.TOTL.ZS   
    14428  Account ownership at a financial institution o...  FX.OWN.TOTL.FE.ZS   
    14429  Account ownership at a financial institution o...  FX.OWN.TOTL.MA.ZS   
    14430  Account ownership at a financial institution o...  FX.OWN.TOTL.OL.ZS   
    14431  Account ownership at a financial institution o...  FX.OWN.TOTL.40.ZS   
    14432  Account ownership at a financial institution o...  FX.OWN.TOTL.PL.ZS   
    14433  Account ownership at a financial institution o...  FX.OWN.TOTL.60.ZS   
    14434  Account ownership at a financial institution o...  FX.OWN.TOTL.SO.ZS   
    
           1960  1961  1962  1963  1964  1965  ...       2013    2014       2015  \
    14420   NaN   NaN   NaN   NaN   NaN   NaN  ...        NaN     NaN        NaN   
    14421   NaN   NaN   NaN   NaN   NaN   NaN  ...  99.600000   99.70  99.700000   
    14422   NaN   NaN   NaN   NaN   NaN   NaN  ...  94.300000   95.00  95.500000   
    14423   NaN   NaN   NaN   NaN   NaN   NaN  ...  99.900000   99.90  99.900000   
    14424   NaN   NaN   NaN   NaN   NaN   NaN  ...  99.342674  100.00  99.625389   
    14425   NaN   NaN   NaN   NaN   NaN   NaN  ...  94.687187  100.00  97.091499   
    14426   NaN   NaN   NaN   NaN   NaN   NaN  ...  99.789146  100.00  99.860687   
    14427   NaN   NaN   NaN   NaN   NaN   NaN  ...        NaN   50.20        NaN   
    14428   NaN   NaN   NaN   NaN   NaN   NaN  ...        NaN   50.85        NaN   
    14429   NaN   NaN   NaN   NaN   NaN   NaN  ...        NaN   49.46        NaN   
    14430   NaN   NaN   NaN   NaN   NaN   NaN  ...        NaN   57.50        NaN   
    14431   NaN   NaN   NaN   NaN   NaN   NaN  ...        NaN   44.63        NaN   
    14432   NaN   NaN   NaN   NaN   NaN   NaN  ...        NaN   52.27        NaN   
    14433   NaN   NaN   NaN   NaN   NaN   NaN  ...        NaN   53.90        NaN   
    14434   NaN   NaN   NaN   NaN   NaN   NaN  ...        NaN   48.90        NaN   
    
                2016    2017        2018   2019   2020   2021  Unnamed: 66  
    14420        NaN     NaN         NaN    NaN    NaN    NaN          NaN  
    14421  99.800000   99.80   99.800000   99.9   99.9    NaN          NaN  
    14422  96.000000   96.30   96.600000   97.0   97.2    NaN          NaN  
    14423  99.900000   99.90   99.900000   99.9   99.9    NaN          NaN  
    14424  99.849579  100.00   99.989578  100.0  100.0    NaN          NaN  
    14425  98.836769  100.00   99.871811  100.0  100.0    NaN          NaN  
    14426  99.942131  100.00  100.000000  100.0  100.0    NaN          NaN  
    14427        NaN   48.71         NaN    NaN    NaN  71.63          NaN  
    14428        NaN   50.76         NaN    NaN    NaN  73.75          NaN  
    14429        NaN   46.47         NaN    NaN    NaN  69.56          NaN  
    14430        NaN   53.37         NaN    NaN    NaN  70.62          NaN  
    14431        NaN   38.06         NaN    NaN    NaN  65.23          NaN  
    14432        NaN   43.05         NaN    NaN    NaN  57.10          NaN  
    14433        NaN   55.79         NaN    NaN    NaN  75.82          NaN  
    14434        NaN   52.28         NaN    NaN    NaN  79.69          NaN  
    
    [15 rows x 67 columns]
    


```python
print(filtered_df)
```

          Country Name Country Code  \
    14420    Argentina          ARG   
    14421    Argentina          ARG   
    14422    Argentina          ARG   
    14423    Argentina          ARG   
    14424    Argentina          ARG   
    ...            ...          ...   
    15857    Argentina          ARG   
    15858    Argentina          ARG   
    15859    Argentina          ARG   
    15860    Argentina          ARG   
    15861    Argentina          ARG   
    
                                              Indicator Name     Indicator Code  \
    14420  ARI treatment (% of children under 5 taken to ...     SH.STA.ARIC.ZS   
    14421  Access to clean fuels and technologies for coo...     EG.CFT.ACCS.ZS   
    14422  Access to clean fuels and technologies for coo...  EG.CFT.ACCS.RU.ZS   
    14423  Access to clean fuels and technologies for coo...  EG.CFT.ACCS.UR.ZS   
    14424            Access to electricity (% of population)     EG.ELC.ACCS.ZS   
    ...                                                  ...                ...   
    15857  Women who believe a husband is justified in be...     SG.VAW.REFU.ZS   
    15858  Women who were first married by age 15 (% of w...  SP.M15.2024.FE.ZS   
    15859  Women who were first married by age 18 (% of w...  SP.M18.2024.FE.ZS   
    15860  Women's share of population ages 15+ living wi...  SH.DYN.AIDS.FE.ZS   
    15861  Young people (ages 15-24) newly infected with HIV     SH.HIV.INCD.YG   
    
           1960  1961  1962  1963  1964  1965  ...         2013    2014  \
    14420   NaN   NaN   NaN   NaN   NaN   NaN  ...          NaN     NaN   
    14421   NaN   NaN   NaN   NaN   NaN   NaN  ...    99.600000    99.7   
    14422   NaN   NaN   NaN   NaN   NaN   NaN  ...    94.300000    95.0   
    14423   NaN   NaN   NaN   NaN   NaN   NaN  ...    99.900000    99.9   
    14424   NaN   NaN   NaN   NaN   NaN   NaN  ...    99.342674   100.0   
    ...     ...   ...   ...   ...   ...   ...  ...          ...     ...   
    15857   NaN   NaN   NaN   NaN   NaN   NaN  ...          NaN     NaN   
    15858   NaN   NaN   NaN   NaN   NaN   NaN  ...          NaN     NaN   
    15859   NaN   NaN   NaN   NaN   NaN   NaN  ...          NaN     NaN   
    15860   NaN   NaN   NaN   NaN   NaN   NaN  ...    35.500000    35.5   
    15861   NaN   NaN   NaN   NaN   NaN   NaN  ...  1900.000000  1900.0   
    
                  2015         2016    2017         2018    2019    2020    2021  \
    14420          NaN          NaN     NaN          NaN     NaN     NaN     NaN   
    14421    99.700000    99.800000    99.8    99.800000    99.9    99.9     NaN   
    14422    95.500000    96.000000    96.3    96.600000    97.0    97.2     NaN   
    14423    99.900000    99.900000    99.9    99.900000    99.9    99.9     NaN   
    14424    99.625389    99.849579   100.0    99.989578   100.0   100.0     NaN   
    ...            ...          ...     ...          ...     ...     ...     ...   
    15857          NaN          NaN     NaN          NaN     NaN     NaN     NaN   
    15858          NaN          NaN     NaN          NaN     NaN     NaN     NaN   
    15859          NaN          NaN     NaN          NaN     NaN     NaN     NaN   
    15860    35.600000    35.700000    35.7    35.800000    35.8    35.9    35.9   
    15861  1900.000000  1900.000000  1900.0  1900.000000  1800.0  1800.0  1700.0   
    
           Unnamed: 66  
    14420          NaN  
    14421          NaN  
    14422          NaN  
    14423          NaN  
    14424          NaN  
    ...            ...  
    15857          NaN  
    15858          NaN  
    15859          NaN  
    15860          NaN  
    15861          NaN  
    
    [1442 rows x 67 columns]
    


```python
#Created a CSV so I can open it in Excel and review what I've got and what I need to edit out
filtered_df.to_csv('argentina.csv')
```


```python
#Let's get the general shape
filtered_df.shape
```




    (1442, 67)




```python
#Glad I made a CSV, this display is not at all helpful
print(filtered_df)
```

          Country Name Country Code  \
    14420    Argentina          ARG   
    14421    Argentina          ARG   
    14422    Argentina          ARG   
    14423    Argentina          ARG   
    14424    Argentina          ARG   
    ...            ...          ...   
    15857    Argentina          ARG   
    15858    Argentina          ARG   
    15859    Argentina          ARG   
    15860    Argentina          ARG   
    15861    Argentina          ARG   
    
                                              Indicator Name     Indicator Code  \
    14420  ARI treatment (% of children under 5 taken to ...     SH.STA.ARIC.ZS   
    14421  Access to clean fuels and technologies for coo...     EG.CFT.ACCS.ZS   
    14422  Access to clean fuels and technologies for coo...  EG.CFT.ACCS.RU.ZS   
    14423  Access to clean fuels and technologies for coo...  EG.CFT.ACCS.UR.ZS   
    14424            Access to electricity (% of population)     EG.ELC.ACCS.ZS   
    ...                                                  ...                ...   
    15857  Women who believe a husband is justified in be...     SG.VAW.REFU.ZS   
    15858  Women who were first married by age 15 (% of w...  SP.M15.2024.FE.ZS   
    15859  Women who were first married by age 18 (% of w...  SP.M18.2024.FE.ZS   
    15860  Women's share of population ages 15+ living wi...  SH.DYN.AIDS.FE.ZS   
    15861  Young people (ages 15-24) newly infected with HIV     SH.HIV.INCD.YG   
    
           1960  1961  1962  1963  1964  1965  ...         2013    2014  \
    14420   NaN   NaN   NaN   NaN   NaN   NaN  ...          NaN     NaN   
    14421   NaN   NaN   NaN   NaN   NaN   NaN  ...    99.600000    99.7   
    14422   NaN   NaN   NaN   NaN   NaN   NaN  ...    94.300000    95.0   
    14423   NaN   NaN   NaN   NaN   NaN   NaN  ...    99.900000    99.9   
    14424   NaN   NaN   NaN   NaN   NaN   NaN  ...    99.342674   100.0   
    ...     ...   ...   ...   ...   ...   ...  ...          ...     ...   
    15857   NaN   NaN   NaN   NaN   NaN   NaN  ...          NaN     NaN   
    15858   NaN   NaN   NaN   NaN   NaN   NaN  ...          NaN     NaN   
    15859   NaN   NaN   NaN   NaN   NaN   NaN  ...          NaN     NaN   
    15860   NaN   NaN   NaN   NaN   NaN   NaN  ...    35.500000    35.5   
    15861   NaN   NaN   NaN   NaN   NaN   NaN  ...  1900.000000  1900.0   
    
                  2015         2016    2017         2018    2019    2020    2021  \
    14420          NaN          NaN     NaN          NaN     NaN     NaN     NaN   
    14421    99.700000    99.800000    99.8    99.800000    99.9    99.9     NaN   
    14422    95.500000    96.000000    96.3    96.600000    97.0    97.2     NaN   
    14423    99.900000    99.900000    99.9    99.900000    99.9    99.9     NaN   
    14424    99.625389    99.849579   100.0    99.989578   100.0   100.0     NaN   
    ...            ...          ...     ...          ...     ...     ...     ...   
    15857          NaN          NaN     NaN          NaN     NaN     NaN     NaN   
    15858          NaN          NaN     NaN          NaN     NaN     NaN     NaN   
    15859          NaN          NaN     NaN          NaN     NaN     NaN     NaN   
    15860    35.600000    35.700000    35.7    35.800000    35.8    35.9    35.9   
    15861  1900.000000  1900.000000  1900.0  1900.000000  1800.0  1800.0  1700.0   
    
           Unnamed: 66  
    14420          NaN  
    14421          NaN  
    14422          NaN  
    14423          NaN  
    14424          NaN  
    ...            ...  
    15857          NaN  
    15858          NaN  
    15859          NaN  
    15860          NaN  
    15861          NaN  
    
    [1442 rows x 67 columns]
    


```python
#drop all rows but the four I'm interested in, the GDP numbers and the school enrollment
justtwo = filtered_df[ (filtered_df['Indicator Name'] != 'GDP (current US$)') & (filtered_df['Indicator Name'] != 'School enrollment, primary (% gross)')].index
filtered_df.drop(justtwo , inplace=True)
filtered_df.head(15)

```

    C:\Users\sfugal\AppData\Local\Temp\ipykernel_17168\3087900971.py:3: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      filtered_df.drop(justtwo , inplace=True)
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country Name</th>
      <th>Country Code</th>
      <th>Indicator Name</th>
      <th>Indicator Code</th>
      <th>1960</th>
      <th>1961</th>
      <th>1962</th>
      <th>1963</th>
      <th>1964</th>
      <th>1965</th>
      <th>...</th>
      <th>2013</th>
      <th>2014</th>
      <th>2015</th>
      <th>2016</th>
      <th>2017</th>
      <th>2018</th>
      <th>2019</th>
      <th>2020</th>
      <th>2021</th>
      <th>Unnamed: 66</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>14887</th>
      <td>Argentina</td>
      <td>ARG</td>
      <td>GDP (current US$)</td>
      <td>NY.GDP.MKTP.CD</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2.445060e+10</td>
      <td>1.827212e+10</td>
      <td>2.560525e+10</td>
      <td>2.834471e+10</td>
      <td>...</td>
      <td>5.520251e+11</td>
      <td>5.263197e+11</td>
      <td>5.947493e+11</td>
      <td>5.575314e+11</td>
      <td>6.436287e+11</td>
      <td>5.248197e+11</td>
      <td>4.528184e+11</td>
      <td>3.895910e+11</td>
      <td>4.914927e+11</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15622</th>
      <td>Argentina</td>
      <td>ARG</td>
      <td>School enrollment, primary (% gross)</td>
      <td>SE.PRM.ENRR</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>1.120119e+02</td>
      <td>1.114597e+02</td>
      <td>1.113034e+02</td>
      <td>1.107392e+02</td>
      <td>1.097415e+02</td>
      <td>1.096592e+02</td>
      <td>1.095163e+02</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>2 rows × 67 columns</p>
</div>




```python
#Check thge shape to make sure that it's 67, 2)
filtered_df.shape
```




    (2, 67)




```python
#Use transpose feature to turn the whole thing 90 degrees)
turned = filtered_df.transpose()
```


```python
#We have a turn!
print(turned)
```

                                  14887                                 15622
    Country Name              Argentina                             Argentina
    Country Code                    ARG                                   ARG
    Indicator Name    GDP (current US$)  School enrollment, primary (% gross)
    Indicator Code       NY.GDP.MKTP.CD                           SE.PRM.ENRR
    1960                            NaN                                   NaN
    ...                             ...                                   ...
    2018            524819742918.669006                            109.659172
    2019             452818426182.65802                            109.516296
    2020            389591035520.674988                                   NaN
    2021            491492700657.012024                                   NaN
    Unnamed: 66                     NaN                                   NaN
    
    [67 rows x 2 columns]
    


```python
#We need some changes to make it match the example, lets remove the rows that aren't useful: Country Name, Country Code, Indicator Name, Indicator Code, and that top row with the numbers of the rows in the original dataframe
turned.drop(["Country Name", "Country Code", "Indicator Name", "Indicator Code"], inplace = True)
```


```python
print(turned)
```

                               14887       15622
    1960                         NaN         NaN
    1961                         NaN         NaN
    1962          24450604877.493401         NaN
    1963          18272123664.399399         NaN
    1964          25605249381.759701         NaN
    ...                          ...         ...
    2018         524819742918.669006  109.659172
    2019          452818426182.65802  109.516296
    2020         389591035520.674988         NaN
    2021         491492700657.012024         NaN
    Unnamed: 66                  NaN         NaN
    
    [63 rows x 2 columns]
    


```python
turned.to_csv('turned.csv')
```


```python
turned.columns
```




    Index([14887, 15622], dtype='int64')




```python
#Create a new index
turned.reset_index(inplace=True)
```


```python
#Rename the columns
turned.columns = ["Year", "Primary Enrollment", "GDP"]
```


```python
print(turned)
```

               Year   Primary Enrollment         GDP
    0          1960                  NaN         NaN
    1          1961                  NaN         NaN
    2          1962   24450604877.493401         NaN
    3          1963   18272123664.399399         NaN
    4          1964   25605249381.759701         NaN
    ..          ...                  ...         ...
    58         2018  524819742918.669006  109.659172
    59         2019   452818426182.65802  109.516296
    60         2020  389591035520.674988         NaN
    61         2021  491492700657.012024         NaN
    62  Unnamed: 66                  NaN         NaN
    
    [63 rows x 3 columns]
    


```python
#Remove bottom row so that I can change data type of Year column to numeric
turned = turned.drop(turned.index[-1])
```


```python
#change data type of Year column to numeric so I can filter by years less than 2020
turned["Year"] = pd.to_numeric(turned["Year"])
```


```python
#Remove all the years before 2000
theyear2000 = turned[turned["Year"] >= 2000]
```


```python
print(theyear2000)
```

        Year   Primary Enrollment         GDP
    40  2000       284203750000.0   115.69413
    41  2001       268696750000.0  116.250168
    42  2002   97724004251.860199  116.798431
    43  2003  127586973492.177002  114.494667
    44  2004  164657930452.786987  115.806053
    45  2005  198737095012.282013  115.299149
    46  2006  232557260817.308014    117.2033
    47  2007  287530508430.567993  118.051109
    48  2008  361558037110.419006   118.59346
    49  2009  332976484577.619019  117.905983
    50  2010   423627422092.48999  116.975761
    51  2011   530163281574.65802  115.614731
    52  2012  545982375701.127991  114.227173
    53  2013  552025140252.245972  112.011948
    54  2014     526319673731.638  111.459671
    55  2015  594749285413.212036  111.303413
    56  2016  557531376217.967041  110.739182
    57  2017  643628665302.155029  109.741463
    58  2018  524819742918.669006  109.659172
    59  2019   452818426182.65802  109.516296
    60  2020  389591035520.674988         NaN
    61  2021  491492700657.012024         NaN
    


```python


```


```python
#reindex to make rows match the example
theyear2000.reset_index(inplace=True)
```


```python
#drop current index
theyear2000 = theyear2000.drop(columns="index")
```


```python
print(theyear2000)
```

        Year   Primary Enrollment         GDP
    0   2000       284203750000.0   115.69413
    1   2001       268696750000.0  116.250168
    2   2002   97724004251.860199  116.798431
    3   2003  127586973492.177002  114.494667
    4   2004  164657930452.786987  115.806053
    5   2005  198737095012.282013  115.299149
    6   2006  232557260817.308014    117.2033
    7   2007  287530508430.567993  118.051109
    8   2008  361558037110.419006   118.59346
    9   2009  332976484577.619019  117.905983
    10  2010   423627422092.48999  116.975761
    11  2011   530163281574.65802  115.614731
    12  2012  545982375701.127991  114.227173
    13  2013  552025140252.245972  112.011948
    14  2014     526319673731.638  111.459671
    15  2015  594749285413.212036  111.303413
    16  2016  557531376217.967041  110.739182
    17  2017  643628665302.155029  109.741463
    18  2018  524819742918.669006  109.659172
    19  2019   452818426182.65802  109.516296
    20  2020  389591035520.674988         NaN
    21  2021  491492700657.012024         NaN
    


```python
theyear2000.to_csv('argentinademo.csv')
```


```python
print(theyear2000)
```

        Year   Primary Enrollment         GDP
    0   2000       284203750000.0   115.69413
    1   2001       268696750000.0  116.250168
    2   2002   97724004251.860199  116.798431
    3   2003  127586973492.177002  114.494667
    4   2004  164657930452.786987  115.806053
    5   2005  198737095012.282013  115.299149
    6   2006  232557260817.308014    117.2033
    7   2007  287530508430.567993  118.051109
    8   2008  361558037110.419006   118.59346
    9   2009  332976484577.619019  117.905983
    10  2010   423627422092.48999  116.975761
    11  2011   530163281574.65802  115.614731
    12  2012  545982375701.127991  114.227173
    13  2013  552025140252.245972  112.011948
    14  2014     526319673731.638  111.459671
    15  2015  594749285413.212036  111.303413
    16  2016  557531376217.967041  110.739182
    17  2017  643628665302.155029  109.741463
    18  2018  524819742918.669006  109.659172
    19  2019   452818426182.65802  109.516296
    20  2020  389591035520.674988         NaN
    21  2021  491492700657.012024         NaN
    


```python
#Create the database from the dataframe
connection = sqlite3.connect("argentina.db")
# Create a cursor object to execute SQL commands
cursor = connection.cursor()
```


```python
#Turn dataframe into database
theyear2000.to_sql("argentina", connection, if_exists="replace", index=False)
```




    22




```python
#Display to make sure it worked
with sqlite3.connect("argentina.db") as conn:
    cursor = conn.cursor()
    rows = cursor.execute("SELECT * FROM argentina")
    for row in rows:
        print(row)
```

    (2000, 284203750000.0, 115.694129943848)
    (2001, 268696750000.0, 116.25016784668)
    (2002, 97724004251.8602, 116.798431396484)
    (2003, 127586973492.177, 114.494667053223)
    (2004, 164657930452.787, 115.806053161621)
    (2005, 198737095012.282, 115.29914855957)
    (2006, 232557260817.308, 117.203300476074)
    (2007, 287530508430.568, 118.051109313965)
    (2008, 361558037110.419, 118.593460083008)
    (2009, 332976484577.619, 117.905982971191)
    (2010, 423627422092.49, 116.975761413574)
    (2011, 530163281574.658, 115.614730834961)
    (2012, 545982375701.128, 114.227172851563)
    (2013, 552025140252.246, 112.011947631836)
    (2014, 526319673731.638, 111.459671020508)
    (2015, 594749285413.212, 111.303413391113)
    (2016, 557531376217.967, 110.739181518555)
    (2017, 643628665302.155, 109.74146270752)
    (2018, 524819742918.669, 109.659172058105)
    (2019, 452818426182.658, 109.516296386719)
    (2020, 389591035520.675, None)
    (2021, 491492700657.012, None)
    


```python

```
