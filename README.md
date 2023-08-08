# Equi7Grid

[![build ubuntu](https://github.com/TUW-GEO/Equi7Grid/workflows/ubuntu/badge.svg)](https://github.com/TUW-GEO/Equi7Grid/actions/workflows/ubuntu.yml)
[![build windows](https://github.com/TUW-GEO/Equi7Grid/workflows/windows/badge.svg)](https://github.com/TUW-GEO/Equi7Grid/actions/workflows/windows.yml)
[![coverage](https://coveralls.io/repos/github/TUW-GEO/Equi7Grid/badge.svg?branch=master)](https://coveralls.io/github/TUW-GEO/Equi7Grid?branch=master)
[![pypi package](https://badge.fury.io/py/Equi7Grid.svg)](https://badge.fury.io/py/Equi7Grid)
[![documentation](https://readthedocs.org/projects/equi7grid/badge/?version=latest)](https://equi7grid.readthedocs.io/)

A python class for working with Equi7Grid - how to convert to - how to use the tiling system - etc.

It's a python package that handles the geometric and geographic operations of a gridded and tiled projection system.
It was designed for data cubes ingesting satellite imagery and builds the basis for the Equi7Grid (
see https://github.com/TUW-GEO/Equi7Grid).

A detailed documentation on the Equi7Grid definition is at:

`~/docs/doc_files/`

Overlays for visualisation in Google Earth can be found here:

`~/docs/doc_files/google_earth_overlays/`

The 7 projections are completely defined by WKT-strings in the .prj-files at

`~/wkt/`

or simply by following **proj4-strings**:

```
AF: '+proj=aeqd +lat_0=8.5 +lon_0=21.5 +x_0=5621452.01998 +y_0=5990638.42298 +datum=WGS84 +units=m +no_defs'
AN: '+proj=aeqd +lat_0=-90 +lon_0=0 +x_0=3714266.97719 +y_0=3402016.50625 +datum=WGS84 +units=m +no_defs'
AS: '+proj=aeqd +lat_0=47 +lon_0=94 +x_0=4340913.84808 +y_0=4812712.92347 +datum=WGS84 +units=m +no_defs'
EU: '+proj=aeqd +lat_0=53 +lon_0=24 +x_0=5837287.81977 +y_0=2121415.69617 +datum=WGS84 +units=m +no_defs'
NA: '+proj=aeqd +lat_0=52 +lon_0=-97.5 +x_0=8264722.17686 +y_0=4867518.35323 +datum=WGS84 +units=m +no_defs'
OC: '+proj=aeqd +lat_0=-19.5 +lon_0=131.5 +x_0=6988408.5356 +y_0=7654884.53733 +datum=WGS84 +units=m +no_defs'
SA: '+proj=aeqd +lat_0=-14 +lon_0=-60.5 +x_0=7257179.23559 +y_0=5592024.44605 +datum=WGS84 +units=m +no_defs'
```

## Citation

[![citation](https://zenodo.org/badge/DOI/10.5281/zenodo.1048530.svg)](https://doi.org/10.5281/zenodo.1048530)

If you use the software in a publication then please cite it using the Zenodo DOI.
Be aware that this badge links to the latest package version.

Please select your specific version at https://doi.org/10.5281/zenodo.1048530 to get the DOI of that version.
You should normally always use the DOI for the specific version of your record in citations.
This is to ensure that other researchers can access the exact research artefact you used for reproducibility.

You can find additional information regarding DOI versioning at http://help.zenodo.org/#versioning

## Installation

This package can be installed through pip:

```bash
pip install Equi7Grid
```

Installs for `scipy` and `gdal` are required from conda or conda-forge (see below how to set up a fresh environment).

## Examples

The `Equi7Grid` packages allows you to interact with different projections, and query information from the Equi7 raster.

You can retrieve all tiles covering a region of interest defined using lan/lot coordinates using `search_tiles_in_roi`:

snippet: search-tiles-in-lon-lat-roi

## Contribute

We are happy if you want to contribute. Please raise an issue explaining what
is missing or if you find a bug. We will also gladly accept pull requests
against our master branch for new features or bug fixes.

## Development setup

For development, we recommend using the `make` tool to automatically create python environments and install more complex
dependencies i.e. `gdal`.

Instruction on how to set up an environment on systems without proper `make` support, such as Windows, can be found in a
subsequent section.

### Creating python environments with make

#### Conda

Make sure miniconda3 is installed by following
the [official installation instructions](https://conda.io/projects/conda/en/stable/user-guide/install/index.html>).
To create a new development environment using `conda` make the `conda` rule:

```bash
make conda
```

This will create a new conda environment called `equi7grid` and install all necessary dependencies.

#### Virtualenv

Make sure you have installed `virtualenv` and `gdal` on your system.
For instance under Ubuntu you can install gdal using ``apt install libgdal-dev``, and `virtualenv`
using ``apt install python3-venv``.
To set up a virtualenv environment simply make the `venv` rule:

```bash
make venv
```

This will create a `virtualenv` environment within a `venv` folder at the root of the project.
It will install the `gdal` dependency using [pygdal](https://pypi.org/project/pygdal/) which requires `gdal` to be
installed on the system.

#### Installing test dependencies

To create a testing environment you can set the `TEST_ENV=1` parameter:

```bash
make venv TEST_ENV=1
```

After activating the environment you can make the `test` rule to run all unit tests:

```bash
make test
```

### Creating python environments on Windows

First make sure miniconda3 is installed on your system by following
the [installation instructions](https://conda.io/projects/conda/en/stable/user-guide/install/index.html>).

Create the `equi7grid` conda environment from the `environment.yml` provided at the root of the repository.

```
conda env create -f environment.yml
```

See also the official anaconda documentation
for [detailed instructions on environments and environment files](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html>).

Now you should be able to activate the environment:

```
conda activate equi7grid
```

Once activate, you can install the `Equi7Grid` package in development mode using pip by running the following command in
the root directory of the repository:

```
pip install -e .
```

#### Installing test dependencies

To install the test dependencies as well use:

```
pip install -e .[testing]
```

Now you should be able to run all unit tests:

```
pytest tests/
```

You can also have a look at the source of the Makefile for more detailed installation and testing options.

## Guidelines

If you want to contribute please follow these steps:

- Fork the Equi7Grid repository to your account
- Clone the repository
- make a new feature branch from the Equi7Grid master branch
- Add your feature
- Please include tests for your contributions in one of the test directories.
  We use py.test so a simple function called test_my_feature is enough
- submit a pull request to our master branch

