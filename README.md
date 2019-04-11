# segment_and_map
This repo includes scripts for segmenting spacetx data sets and mapping the results to a reference RNA-seq data set.


## Scripts

Currently there are two available scripts (which can be found in the `scripts` folder).  The data required to run these scripts is found elsewhere (as indicated within each script).

1. [**Watershed segmentation** (link)](http://htmlpreview.github.io/?https://github.com/spacetx/segment_and_map/blob/master/scripts/smFISH_segmentation.nb.html) (Note: this is slow to load in the browser) -  This script assigns cell ids to each spot from a spatial transcriptomics data set. More specifically, it reads in all spot data in the [starfish](https://spacetx-starfish.readthedocs.io/en/latest/) `IntensityTable` format (each row is a spot, columns are locations and gene IDs), performs a modified watershed segmentation on all of the spot locations to assign each spot to a cell, and then appends a cell id column to the `IntensityTable`. It also compiles an intensity matrix (cell x gene matrix with each value corresponding to spots per cell) and a meta-data matrix (e.g., spot location and area) for use with the [mfishtools r library](https://github.com/AllenInstitute/mfishtools) or other mapping (or clustering) strategies. In this case the example data is and smFISH experiment from the Allen Institute, which is available for download from the `wg5-mapping` channel in the spacetx slack space.  
2. [**Mapping cells to reference RNA-seq types.** (link)](http://htmlpreview.github.io/?https://github.com/spacetx/segment_and_map/blob/master/scripts/smFISH_mapping.nb.html) - This script assigns cell types to each cell by mapping to RNA-seq cell types.  Specifically, it reads in data from a spatial transcriptomics experiment (a cell x gene matrix as in #1 above) and compares it agains a reference RNA-seq data set by scaling the data sets to match and then running Pearson correlation to find the top match.  In this case a 22 gene panel run on mouse VISp tissue using smFISH at the Allen Institute is compared against ~100 reference cell types from the ~12,000 cell FACs data set [available from the Allen Institute website](http://celltypes.brain-map.org/rnaseq).  *Note: this method is under active development.  Please review results carefully and any suggestions would be appreciated!*  

## Housekeeping

* If you want me to respond, tag me in relevant `Issues` or [e-mail me directly](mailto:jeremym@alleninstitute.org).
* Please respect [the license](https://github.com/spacetx/segment_and_map/blob/master/LICENSE) and [Contribution Agreement](https://github.com/spacetx/segment_and_map/blob/master/CONTRIBUTION) files as appropriate.
