# hnh-rcv
Hoof 'N' Horn's ranked-choice voting tallying algorithm! This uses instant runoff voting to run and give results for Hoof 'N' Horn's general body meetings and annual elections.

## How to run an individual vote

Create a Qualtrics survey and add one question with the Rank Order option. When the results are in, download the CSV, and use the filepath as an input for the `main` function in `instant_runoff.ipynb`

## How to run a GBM vote

First, create an absentee ballot Qualtrics form. This should be one form with every vote listed as a Rank Order question. In the sample vote, two questions were present; the first presented three options for favorite show, and the second presented four options for spiciest HnH alum.

In the `run_hnh_election.ipynb` notebook, change the global variable `fold` to the meeting's title (ex: 2023_ELECTION). Then, within the `load_absentee` function, change the `elections` variable to reflect the ballot by having each element be a 2-tuple with the name of the particular vote and how many options there are. For example, if voting for three 3-show ballots and a 4-way president race, `elections` should be `[("fall", 3), ("winter", 3), ("spring", 3), ("president", 4)]. Download the CSV results from the absentee ballot and put its filepath into `load_absentee`, which will create an election folder.

Next, create an individual Qualtrics survey for every race (as in, there should be one survey for the fall show selection, another for the winter show selection, etc). Distribute these at the GBM. When the time comes, download the CSV file and move it into the subfolder for that race (in the example, the spiciest alum results were moved into the 'sample_election/spicy' folder), then run the `main` function in `run_hnh_election` with the election name you created back in `load_absentee`, like `main("spicy") in this example. The results will be output.s