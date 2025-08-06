 Satellite Image Narrator
This project provides a simple Python-based tool to:

Process satellite .tif images.

Compute the NDVI (Normalized Difference Vegetation Index).

Visualize NDVI values using a heatmap.

Extract NDVI statistics.

Generate a textual explanation (narrative) of vegetation health across the image.

 Project Structure
nginx
Copy
Edit
Satellite Image Narrator/
├── explain_satellite.py         # Main code file
├── ndvi_change_amazon.tif       # Input satellite image (GeoTIFF)
├── output_heatmap.png           # NDVI heatmap generated
├── explanation.txt              # Textual explanation output
├── README.md                    # Project instructions
 Requirements
Install the required packages using pip:

bash
Copy
Edit
pip install rasterio matplotlib numpy
 What is NDVI?
NDVI = (NIR - Red) / (NIR + Red)

It measures vegetation health:

 High NDVI (~1.0): Dense, healthy vegetation

 Low NDVI (~0.0): Sparse or stressed vegetation

 Negative NDVI (< 0): Non-vegetation (e.g., water, urban areas)

 How to Run
Place your .tif satellite image (with at least NIR and Red bands) in the same directory.

Update the image_path variable in the script with your file path.

Run the script:

bash
Copy
Edit
python explain_satellite.py
 Output
output_heatmap.png: Visual NDVI heatmap of the image.

explanation.txt: Summary of vegetation condition in plain language.

Example snippet from explanation.txt:

csharp
Copy
Edit
The area shows signs of moderate vegetation health. The average NDVI is 0.42, which suggests partial vegetation cover...
 Troubleshooting
 Error: band index 3 out of range

Ensure the .tif file has at least 4 bands:

Band 3 (Red)

Band 4 (NIR)

You can inspect band count using:

python
Copy
Edit
import rasterio
with rasterio.open("your_image.tif") as src:
    print(src.count)
If Red is band 1 and NIR is band 2, modify:

python
Copy
Edit
red = src.read(1)
nir = src.read(2)
 Notes
NDVI values are normalized between -1 and 1.

This project works best with multi-band satellite images (e.g., from Landsat, Sentinel).

Not all .tif files contain Red and NIR bands—ensure proper pre-processing.

 Example Output
Heatmap:
![Output Screenshot](Screenshot%202025-08-06%20151205.png)

 License
Sagnik Patra
