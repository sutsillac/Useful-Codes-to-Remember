# Useful-Codes-to-Remember

##To make a count plot show values and percentages on the bars

## Showing values on the count bars:
plt.figure(figsize=(7,4),dpi=100)
ax = sns.countplot( x='colume name',
        data=df)
for i in ax.containers:
    ax.bar_label(i,)
    
## Showing Perccentages on the bars:
total = float(len(df))
ax = sns.histplot(x='colume name', hue='', data=emp_data, bins=20,binwidth=0.09) ##or sns.countplot
plt.title('', fontsize=20)
for p in ax.patches:
    percentage = '{:.1f}%'.format(100 * p.get_height()/total)
    x = p.get_x() + p.get_width()
    y = p.get_height()
    ax.annotate(percentage, (x, y),ha='right') ##'left','center'

## pie plots
fig, ax = plt.subplots(figsize=(7,15),dpi=80)
explode = [0, 0.1]
palette_color = sns.color_palette('dark')
ax.set_title('', fontsize=20, fontname="Dejavu Sans")
ax = df['colume'].value_counts(normalize=True).plot.pie(autopct='%1.0f%%', colors=palette_color, explode=explode)
ax.set_ylabel("")
plt.show()
