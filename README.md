# MSIMLW
Multisource Spectral Indices with Machine Learning for Wetland Extraction
Wetland Classification for Keenjhar Lake using Google Earth Engine
This code performs wetland classification for the Keenjhar Lake area in Sindh, Pakistan, using Landsat 8 imagery and a Random Forest classifier in Google Earth Engine (GEE).
Code Structure and Functionality
1. Area of Interest (AOI) Definition

Defines a rectangular AOI around Keenjhar Lake using coordinates.

2. Data Collection

Filters Landsat 8 Surface Reflectance (SR) imagery for the year 2020 within the AOI.
Applies a cloud cover filter to exclude heavily clouded images.

3. Image Processing Functions
a) scaleImage(image):

Scales the surface reflectance bands to their proper range.

b) addLST(image):

Calculates Land Surface Temperature (LST) from the thermal band.

c) addIndices(image):

Computes various spectral indices:

NDVI (Normalized Difference Vegetation Index)
EVI (Enhanced Vegetation Index)
NDBI (Normalized Difference Built-up Index)
NDMI (Normalized Difference Moisture Index)
NDSI (Normalized Difference Snow Index)
SMI (Soil Moisture Index)
NDWI (Normalized Difference Water Index)
MNDWI (Modified Normalized Difference Water Index)



4. Image Collection Processing

Applies the scaling, LST calculation, and index computation to the entire Landsat collection.
Calculates the median values for all bands and indices over the year 2020.

5. Wetland Mask Creation

Uses the JRC Global Surface Water dataset to create a wetland mask.
Areas with water presence >25% of the time are considered potential wetlands.

6. Training Data Generation

Samples 5000 points from the AOI, including all processed bands, indices, and the wetland mask.
Splits the data into training (70%) and validation (30%) sets.

7. Random Forest Classification

Trains a Random Forest classifier with 100 trees using the training data.
Uses all spectral bands, LST, and calculated indices as input features.

8. Classification and Validation

Applies the trained classifier to the entire image.
Validates the model using the held-out validation set.
Calculates and prints the overall accuracy.

9. Visualization and Export

Displays the classified wetland map on the GEE map interface.
Exports the classification result as a GeoTIFF to Google Drive.

How It Works

The code starts by collecting and processing Landsat 8 imagery for the specified area and time period.
It then calculates various spectral indices and LST, which are useful for distinguishing wetlands from other land cover types.
A wetland mask is created using global surface water data, assuming areas frequently covered by water are potential wetlands.
The Random Forest classifier is trained on a sample of points, learning to distinguish wetlands based on the spectral characteristics and calculated indices.
This trained classifier is then applied to the entire image, producing a binary wetland/non-wetland map.
The accuracy is assessed using a separate validation set, providing an estimate of the classification's reliability.

Customization and Improvements

Adjust the AOI coordinates for more precise coverage of Keenjhar Lake.
Modify the date range to study different time periods or seasonal variations.
Fine-tune the wetland definition threshold in the Global Surface Water dataset.
Add local wetland training data if available for improved accuracy.
Consider incorporating additional relevant environmental variables.
