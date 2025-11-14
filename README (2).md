# Photovoice Processing Pipeline

A complete automated workflow for renaming, sorting, analyzing, and mapping geotagged photos collected through Photovoice sessions.

## Overview

This notebook transforms raw participant uploads into structured datasets, visual grids, emotion histograms, geolocation maps, and exported metadata.

Main steps:
1. Mount Google Drive
2. Import libraries and configure paths
3. Rename photos based on user-defined labels from JotForm Excel
4. Add numeric prefixes and separate into positive/negative folders
5. Generate non-rotating photo grids
6. Create emotion histograms
7. Build interactive GPS maps with Folium
8. Export map screenshots and metadata (CSV/XLSX)

## Directory Structure

```
CONIFER/
    input/
        raw_photos/
        CONIFER_Photo_Upload_Form.xlsx
    output/
        positive_photos/
        negative_photos/
        grids/
        maps/
        histograms/
```

## Pipeline Flow Diagram

```
                          ┌───────────────────────────┐
                          │   JotForm Excel Export     │
                          └───────────────┬────────────┘
                                          │
                                          ▼
                           ┌─────────────────────────┐
                           │     Renaming Engine      │
                           └───────────────┬──────────┘
                                           │
                                           ▼
                     ┌───────────────────────────────────────────┐
                     │     Numbering + Sentiment Sorting          │
                     └──────────────────┬─────────────────────────┘
                                        │
                                        ▼
                       ┌────────────────────────────────┐
                       │         Photo Grids            │
                       └────────────────┬───────────────┘
                                        │
                                        ▼
                         ┌──────────────────────────────┐
                         │       Emotion Histograms      │
                         └─────────────┬────────────────┘
                                       │
                                       ▼
               ┌────────────────────────────────────────────────────┐
               │               GPS EXIF Map Builder                 │
               └──────────────────────────┬─────────────────────────┘
                                          │
                                          ▼
                         ┌────────────────────────────────┐
                         │        Final Outputs            │
                         └────────────────────────────────┘
```

## License

MIT License.
