# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Changed
- The sample script `plot_HH.py` has been replaced for specific examples on how to plot data post-processed with pyMBE: `plot_branched_polyampholyte.py`, `plot_peptide.py`, and `plot_peptide_mixture_grxmc_ideal.py`. (#95)
- Sample scripts now take the pH as an argparse input instead of looping over several pH values. This enables paralization of the sample scripts and avoids conflicts with the current post-processing pipeline. (#95)
- Switched from `os.makedirs` to `Path().mkdir()` to prevent ocasional failure of the scripts when running them in paralel. (#91)
- `pmb.set_reduced_units()` now redefines the reduced units instead of creating a new instance of `pint.UnitRegistry`. Therefore, the user can do operations between objects defining before and after changing the set of reduced units without getting a `ValueError` (#89)
- `pmb.set_reduced_units()` now checks that the arguments provided by the user have the right dimensionality. (#89)
- The constants stored as attributes in `pyMBE.pymbe_library` are now using their values stabilished in the 2019 SI. The value is taken directly from `scipy.constants` instead of being a hard-coded constant. (#86)
- Switched to Ctest for testing, allowing to run the tests on paralel (#87)

### Added
- New sample script showing how to use the analysis tools in pyMBE for post-processing time series from the sample scripts `analyze_time_series.py` (#95) 
- A new optional argument `ignore_files`  for `lib.analysis.analyze_time_series`, enabling to provide a list of files to be ignored for post-processing of time series. (#95)
- Functional testing for all sample scripts. (#95)
- Unit testing for reaction methods. (#86)

### Fixed
- `lib.analysis.get_dt` now raises a ValueError if the two first two rows of the dataframe have the same values for the time, which break the subsequent code. (#95)
- Removed global state variables, instead they are now created by the constructor of `pyMBE.pymbe_library`. This prevents two instances of the pyMBE library to share the same memory address for their attributes. (#89)
- Required Python dependency versions compatible with ESPResSo 4.2 (#84)
- Fixed several deprecated paths and function names in `tutorials/pyMBE_tutorial.ipynb`. (#77, #78, #79, #80, #81)

## [0.8.0] - 2024-06-18

### Added

* Initial release of pyMBE.
