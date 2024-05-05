# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv("/content/SAMPLEIDS.csv")
data.head()
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/c3cfdaef-729a-4e01-987f-c07f055b6097)

```
data.isnull().sum()
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/07839fb5-b540-40da-8b00-37f26b1269df)

```
columns_with_null = data.columns[data.isnull().any()]
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/b1edc442-94f5-44c1-80ba-110843e2d764)

```
median = data[column].median()
data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/97e8461a-8aa4-4218-9ca1-cefa64aaed70)

```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris.csv")
ir.head()
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/d166387a-6b8c-4980-bc26-b4f7903473fb)

```
ir.describe()
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/2c53c970-ffe8-4999-adec-cc237c28c104)

```
sns.boxplot(x='sepal_width',data=ir)
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/75e10a75-59c4-4cef-85c7-7806b61f5ac6)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/b8780026-b359-470a-b38a-bf41876132bd)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/a30e69d4-2c6a-4dd4-b5ff-e05cba073877)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/fd3decd6-f88c-4918-804d-47e67ec47413)

```
sns.boxplot(x='sepal_width',data=delid)
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/d87bc370-90e3-496e-8f65-00537e7da6c3)

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/854b68a0-eb20-4888-9e0f-f49b36c829a8)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```

```
iqr = q3-q1
iqr
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/f00e0e01-b651-47de-9ed8-9a829f11ca91)

```
low = q1 - 1.5*iqr
low
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/0982c2b2-066d-4a51-859e-504bbaf9aa90)

```
high = q3 + 1.5*iqr
high
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/46626b10-2a30-4ee4-92d2-ba5180ab1dd1)

```
df.duplicated()
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/55921ef3-d88a-4e42-993b-14f6eb97dd65)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/793e3f4b-c4e7-43e7-bc82-1120d819cb04)

```
z = np.abs(stats.zscore(df['height']))
z
```

![image](https://github.com/swethaselvarajm/exno1/assets/119525603/07ab8105-8d9c-49f7-b8f6-df8d966ba14b)

# Result
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
