California Housing Price Predictor
This repository contains a unified Python script that handles both the training and inference phases of a machine learning model designed to predict California housing prices.

Using a classic RandomForestRegressor, the script automatically detects whether a trained model exists. If it doesn't, it trains one; if it does, it immediately switches gears to generate predictions on new data.

🚀 Features
Smart Dual-Mode Execution: Automatically toggles between Training and Inference based on the presence of model.pkl.

Stratified Data Splitting: Uses StratifiedShuffleSplit based on income categories to ensure the test set is perfectly representative of the overall dataset.

Robust Preprocessing Pipeline:

Imputes missing numerical values using the median.

Standardizes numerical features via StandardScaler.

Encodes categorical features (ocean_proximity) using OneHotEncoder.

📦 Prerequisites & Installation
Make sure you have Python installed, then install the required dependencies using pip:

Bash
pip install pandas numpy scikit-learn joblib
Required Dataset
To kick off the training phase, you must have the California housing dataset named housing.csv in the root directory of the project.

🛠️ How It Works
The script operates in two distinct phases depending on your file system state:

Phase 1: Training Mode (First Run)
If model.pkl is not found in the directory, the script will:

Load housing.csv.

Categorize income levels to perform a stratified 80/20 split.

Save the test split to input.csv (simulating future unseen data).

Fit the preprocessing pipeline and train the RandomForestRegressor on the training set.

Serialize and save both the pipeline (pipeline.pkl) and the model (model.pkl).

Phase 2: Inference Mode (Subsequent Runs)
If model.pkl is present, the script skips training entirely and will:

Load the pre-trained model and preprocessing pipeline.

Read the target data from input.csv.

Preprocess the data and predict the median_house_value.

Append the predictions as a new column and export the final dataset to output.csv.

💻 How to Run
Simply execute the script from your terminal:

Bash
python main.py
(Replace main.py with the actual filename of your script).

File Breakdown after Execution:
housing.csv - Your original raw dataset (required for setup).

input.csv - The evaluation data extracted during the split.

model.pkl / pipeline.pkl - Your trained model and preprocessing brains.

output.csv - The final generated results containing your real-estate predictions!
