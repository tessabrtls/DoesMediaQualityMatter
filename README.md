# Does Media Quality Matter?

Online Information Search and Policy Support in a High-Choice Media Environment

Analysis code for a master's thesis at the University of Konstanz. The thesis
is a secondary analysis of the seek2judge randomized encouragement experiment
and asks how encouragement to seek policy-relevant information relates to the
online information environment quality (OIEQ) participants realize, and to
subsequent policy-support change.

## What the analysis does

Participants in a German web-tracking panel were assigned to a control
condition, a verbal encouragement to inform themselves online about a policy
proposal, or the same prompt paired with a monetary incentive tied to a
subsequent knowledge test. Three waves covered basic child support, the
renewable-energy transition, and cannabis legalization.

The analysis separates four quantities that are often collapsed into one:
whether a participant searched, how much, whether a characterizable
information environment resulted, and what quality that environment had. It
then tests whether these relationships differ by participants' habitual media
diet.

## Repository structure

```
scripts/
  01a-01e_*.Rmd    Panel and domain preparation, news classification
  02a_*.Rmd        Habitual media diet (30-day pre-treatment window)
  02b_*.Rmd        Experimental-period visits, uptake, effort, encountered OIEQ
  03a_*.Rmd        Analysis dataset assembly
  03b_*.Rmd        Hypothesis tests H1a to H4b, sensitivity, detection limits
  03c_*.Rmd        Descriptives, coverage, balance, moderator validity
  04_*.Rmd         Open-ended responses (exploratory)
output/
  tables/          LaTeX fragments and CSV, one file per table
  figures/         PNG and PDF figures
codebook/          Variable definitions, coding rules, construction steps
```

Scripts run in the order of their prefix. Each writes the objects the next one
reads; none of them can be run in isolation.

## Reproducing the analysis

Requires R 4.3 or later.

```r
# from the repository root
rmarkdown::render("scripts/03b_hypothesis_tests.Rmd")
rmarkdown::render("scripts/03c_descriptives.Rmd")
```

Assertions in the preparation scripts check at each step that joins do not
duplicate rows, that derived indicators agree with their components, and that
the time-window restriction holds, so that a construction error stops the
pipeline rather than propagating into an estimate.

## Data availability

**The raw data and codebooks are not included in this repository.** The survey responses and the
passively recorded browsing data are pseudonymized individual-level data that
could permit re-identification. They are subject to the data-access and
data-protection terms of the original study. Only code and
aggregate output are published here.

Researchers or anybody else who would like to reproduce the analysis, or who have questions
about the construction of any measure, are welcome to get in touch.

## Related repositories

The original experiment and a companion paper are documented separately:

- Attitude Change Paper (Pre-Print): 
    - https://arxiv.org/abs/2501.03097 
    - https://github.com/robertour/s2j_attitude_change
- Knowledge Gap Paper:
    - https://www.tandfonline.com/doi/full/10.1080/10584609.2026.2708131
    - https://github.com/robertour/s2j_kg_polcomm

## Acknowledgments

This thesis is a secondary analysis of data collected by the seek2judge project
at the University of Konstanz. I thank Celina Kacperski, Roberto Ulloa and
Peter Selb as well as Segun Aroyehun for granting access to the data and for their guidance throughout
the project. 



## Funding

The data collection was funded by the Deutsche Forschungsgemeinschaft (DFG –
German Research Foundation) under Germany's Excellence Strategy,
EXC-2035/1 – 390681379. The present secondary analysis received no separate
funding.

## Contact

Tessa Bartels — tessa.bartels@uni-konstanz.de

## License

Code is released under the MIT License. Generated tables are
released under CC BY 4.0.
