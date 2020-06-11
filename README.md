# Regression ReSampling 
[![Downloads](https://pepy.tech/badge/reg-resampler/week)](https://pepy.tech/project/reg-resampler/week)
An interface to apply your favourite resampler on regression tasks. Currently supports all resampling techniques present in **imblearn**

## Why does this exist?
While we were working on a regression task, we realized that the target variable was skewed, i.e., most samples were present in a particular range. One can easily solve the skew problem for classification tasks via a slew of resampling techniques (either under or over sampling) but this luxury is unavailable for regression tasks. We therefore decided to create an interface that can repurpose all resampling techniques for classification problems to regression problems! 

## How to install?
```pip install reg_resampler```

## How to use it?
### Parameters
- **X** - Either a pandas dataframe or numpy matrix. Data to be resampled
- **target** - Either string (for pandas) or index (for numpy). The target variable to be resampled
- **bins=3** - The number of classes that the user wants to generate (Default: 3)
- **balanced_binning=False** - Decides whether samples are to be distributed roughly equally across all classes (Default: False)
- **sampler_obj** - Resampling object. Currently, it supports all resampling techniques present in **imblearn**.

### Functions
- **fit** - Adds classes to each sample and returns an augmented dataframe/numpy matrix (based on input type)
- **resample** - Performs resampling and returns the resampled dataframe/numpy matrix. It also merges classes when required

**Important Note:** All functions return the same data type as provided in input

### How to import?
```python
from reg_resampler import resampler
```

### How to use?
```python
# Initialize the resampler object
rs = resampler()

# Returned dataframe contains a new column called "classes"
# The function also prints the class distribution
# This is for analysis purpose
df_train_ = resample.fit(df_train, target, bins=7)

# Create a smote (over-sampling) object from imblearn
smote = SMOTE(random_state=27)

# Now resample
# You might recieve warning about class merger for low sample classes
df_train_ = rs.resample(smote)
df_train_.head()
```

## Future Ideas
- Support for more resampling techniques

## Feature Request
Drop us an email at **atif.hit.hassan@gmail.com** or **pvsaikrithik@gmail.com** if you want any particular feature

