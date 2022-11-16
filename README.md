##Predict and search framework for ICLR2022 paper #4228

##Requirements

Linux

–python 3.8.13

–pytorch 1.10.2

–cudatoolkit 11.3

–pyscipopt 4.2

–gurobipy  9.5.2

–pyg 2.0.4

## Installation

Create a new environment with [Conda](https://docs.conda.io/en/latest/)

```
conda env create -f py38.yaml

conda activate pytest
```



## Repository structure

–dataset  //training data, generated by gurobi.py(data generate scripts)

–instance

​	–train //training and evaluation instances 

​	–test  //test instances

–logs    //all test logs

--models  //trained model,  used to test model performance

–pretrain // training model folder will be saved here

## Data generation

the Independent Set (IS) instance  and the Combinatorial Auction (CA) instance  use [Ecole](https://www.ecole.ai/) library to generate.

the Balanced Item Placement (denoted by IP) instance and the Workload Appointment (denoted by WA) instance come from the ML4CO 2021 competition [generator](https://github.com/ds4dm/ml4co-competition-hidden). 

Place the generated instances in the instance folder

```
python gurobi.py
```

The corresponding bipartite graph(BG) and solution will be automatically generated in the dataset folder.

## Train 

Select the parameter TaskName in trainPredictModel.py, and then

```
python trainPredictModel.py
```

## Test

Put the trained model into the models folder, then

```
python PredictAndSearch_SCIP.py

python PredictAndSearch_GRB.py

python FixingStrategy_SCIP.py
```

all solver logs will be saved in logs folder.

