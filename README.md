# COVID-19 Data Analysis Project

A comprehensive data analysis project for COVID-19 pandemic data, featuring automated data collection, feature engineering, visualization tools, and exploratory analysis notebooks.

## 🔍 Project Overview

This project provides an end-to-end pipeline for COVID-19 data analysis, combining pandemic case data with socioeconomic indicators to enable comprehensive analysis of the pandemic's impact across different countries and continents.

### Key Features

- **Automated Data Collection**: Downloads latest COVID-19 data from Johns Hopkins CSSE, country mapping data, and World Bank socioeconomic indicators
- **Feature Engineering Pipeline**: Processes raw data into analysis-ready datasets including daily changes, mortality rates, and country statistics
- **Interactive Visualizations**: Comprehensive visualization class with methods for time series plots, growth curves, statistical comparisons, and correlation analysis
- **Exploratory Analysis**: Pre-built Jupyter notebooks for different aspects of the pandemic analysis
- **Data Quality Testing**: Unit tests to ensure data integrity and consistency

## 📁 Project Structure

```
covid-19/
├── data/                              # Data management
│   └── download_data.py              # Scripts to download data from multiple sources
├── features/                          # Feature engineering pipeline
│   ├── make_all.py                   # Main pipeline orchestrator
│   ├── make_cases.py                 # Process case data (confirmed, recovered, deaths)
│   ├── make_cases_daily_change.py    # Calculate daily changes in cases
│   ├── make_cases_since_t0.py        # Cases since outbreak threshold
│   ├── make_continents.py            # Continent mappings
│   ├── make_coordinates.py           # Geographic coordinates
│   ├── make_country_stats.py         # Country-level statistics
│   ├── make_country_to_continent.py  # Country-continent relationships
│   ├── make_mortality.py             # Mortality rate calculations
│   ├── make_world_bank.py            # World Bank socioeconomic data integration
│   └── utils.py                      # Utility functions
├── notebooks/                         # Jupyter notebooks for analysis
│   ├── Data-wrangling.ipynb          # Data preprocessing and cleaning
│   ├── Exploratory_analysis_fancy_plot.ipynb    # Advanced visualizations
│   ├── Exploratory_analysis_socioeconomic.ipynb # Socioeconomic analysis
│   ├── Exploratory-analysis-globally.ipynb      # Global pandemic trends
│   └── Exploratory-analysis-mortality.ipynb     # Mortality analysis
├── tests/                            # Unit tests
│   └── test.py                       # Data quality tests
└── visualizations/                   # Visualization tools
    └── covid_data_viz.py             # Main visualization class
```

## 🚀 Getting Started

### Prerequisites

- Python 3.7+
- Git

### Installation

1. **Clone the repository**

   ```bash
   git clone git@github.com:sahu-sakshi/covid-19.git
   cd covid-19
   ```

2. **Install required packages**

   ```bash
   pip install pandas numpy matplotlib scipy requests wbdata gitpython ipython jupyter
   ```

3. **Download the data**

   ```bash
   cd data
   python download_data.py
   ```

4. **Run the feature engineering pipeline**

   ```bash
   cd ../features
   python make_all.py
   ```

5. **Run tests to verify data quality**
   ```bash
   cd ../tests
   python test.py
   ```

## 📊 Usage Examples

### Basic Visualization

```python
from visualizations.covid_data_viz import CovidDataViz

# Initialize the visualization class
viz = CovidDataViz(path='./data/processed')

# Plot world-level cases
viz.plot_world_cases()

# Plot country-specific data
viz.plot_country_cases('United States')

# Plot continent data
viz.plot_continent_cases('North America')

# Show countries with highest mortality
viz.plot_highest_country_stats('Mortality', n=10)
```

### Growth Analysis

```python
# Compare growth curves between countries
countries = ['Italy', 'Spain', 'United States', 'China']
periods = [1, 2, 3, 4, 5]  # Doubling periods in days
viz.plot_growth(countries=countries, periods=periods, save=True)
```

### Socioeconomic Analysis

```python
# Show correlation matrix
viz.show_corr_mat()

# Create scatter plot with regression
viz.plot_with_slope('GDP per capita, PPP (current international $)', 'Cases per million')
```

## 📈 Data Sources

- **COVID-19 Cases**: [Johns Hopkins CSSE COVID-19 Data Repository](https://github.com/CSSEGISandData/COVID-19)
- **Country Mappings**: [DataHub Country and Continent Codes](https://datahub.io/JohnSnowLabs/country-and-continent-codes-list)
- **Socioeconomic Data**: [World Bank Open Data](https://data.worldbank.org/) via `wbdata` API
  - GDP per capita (PPP)
  - Population statistics
  - Urban population percentage
  - Life expectancy
  - Health expenditure

## 🔬 Available Analysis

### Notebooks

1. **Data Wrangling** (`Data-wrangling.ipynb`): Data preprocessing and cleaning steps
2. **Global Analysis** (`Exploratory-analysis-globally.ipynb`): Worldwide pandemic trends and patterns
3. **Mortality Analysis** (`Exploratory-analysis-mortality.ipynb`): Death rate analysis across countries
4. **Socioeconomic Analysis** (`Exploratory_analysis_socioeconomic.ipynb`): Impact correlation with economic factors
5. **Advanced Visualizations** (`Exploratory_analysis_fancy_plot.ipynb`): Complex plotting techniques

### Processed Datasets

The feature engineering pipeline generates:

- `confirmed_cases.csv` - Confirmed cases by country and date
- `recovered_cases.csv` - Recovery data by country and date
- `dead_cases.csv` - Death data by country and date
- `active_cases.csv` - Active cases (confirmed - recovered - deaths)
- `confirmed_cases_daily_change.csv` - Daily new cases
- `confirmed_cases_since_t0.csv` - Cases since outbreak threshold (100 cases)
- `mortality_rate.csv` - Death rate percentages
- `country_stats.csv` - Summary statistics by country
- `coordinates.csv` - Geographic coordinates for mapping
- `continents.csv` - Country-continent mappings
- `world_bank.csv` - Merged socioeconomic indicators

## 🧪 Testing

The project includes unit tests to ensure data quality:

```bash
cd tests
python test.py
```

Tests verify that cruise ships (MS Zaandam, Diamond Princess) are properly excluded from country-level analysis.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📧 Contact

**Sakshi Sahu** - [GitHub Profile](https://github.com/sahu-sakshi)

Project Link: [https://github.com/sahu-sakshi/covid-19](https://github.com/sahu-sakshi/covid-19)

## 🙏 Acknowledgments

- [Johns Hopkins University CSSE](https://github.com/CSSEGISandData/COVID-19) for providing comprehensive COVID-19 data
- [World Bank](https://data.worldbank.org/) for socioeconomic indicators
- [DataHub](https://datahub.io/) for country and continent mapping data.

---

_This project provides comprehensive tools for COVID-19 data analysis and visualization._
