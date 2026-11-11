# Sales Data Analysis
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# 1. Create Dataset (10000 sales)
np.random.seed(42)
months = ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec']
products = ['Laptop', 'Mobile', 'Headphone', 'Keyboard', 'Mouse']

df = pd.DataFrame({
    'Month': np.random.choice(months, 10000),
    'Product': np.random.choice(products, 10000),
    'Sales': np.random.randint(1000, 50000, 10000)
})

print(df.head())

# 2. Monthly Sales
monthly = df.groupby('Month')['Sales'].sum()
print(monthly)

monthly.plot(kind='bar', color='skyblue')
plt.title('Monthly Sales Trend')
plt.ylabel('Total Sales')
plt.show()

# 3. Best Selling Product
best = df.groupby('Product')['Sales'].sum().sort_values(ascending=False)
print("Best Selling Product:")
print(best)

best.plot(kind='bar', color='orange')
plt.title('Product-wise Sales')
plt.show()
