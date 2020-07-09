# DeCALS_south_images
Jupyter Notebook used to download and test DeCALS_south images for Galaxy Zoo and do some simple consistency checks. 

To get the catalogue, the following query was used on https://datalab.noao.edu/query.php?name=ls_dr8.tractor_primary_s, using TAP in TOPCAT:

SELECT * FROM ls_dr8.tractor_primary_s WHERE (mag_r<19 and dec<0 and type!='PSF')

The Jupyter Notebook is based on https://github.com/zooniverse/decals/blob/master/decals/a_download_decals/get_images/download_images_threaded.py:
(1) donwloads fits images from DeCALS
(2) produces colour image, consistent with previous DeCALS images on Galaxy Zoo 
(3) the images are scaled with radius, computed as: radius = fdeV*shapedeVr+(1- fdeV)*shapeexpr
(4) Observations: 2% of images are contaminated by stars (selected with surface brightness, mu<18 mag/arcsec^2) and 4% of galaxies have radius>7.5" (many of which will be wrong size measurements)
