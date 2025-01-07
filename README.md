# FIFA26-World-Cup-Predictor: Project Overview

This project aims to predict the results of the QATAR 2022 World Cup from the international matches held since the 90s, the qualifications of the teams in their last matches, and the potential of each team.

## Resources Used

* Python Version: 3.7
* Packages: Pandas, NumPy, Sklearn, Tensorflow, and Seaborn.
* Data: 
  * [international_matches.csv](https://www.kaggle.com/datasets/brenda89/fifa-world-cup-2022) - This dataset provides a complete overview of all international soccer matches played since the 90s. On top of that, the strength of each team is provided by incorporating actual FIFA rankings as well as player strengths based on the EA Sport FIFA video game.
  * [players_22.csv](https://www.kaggle.com/datasets/stefanoleone992/fifa-22-complete-player-dataset) - The datasets provided include the player data for FIFA 22 Career Mode.

## Data preparation and dataset creation

* Both datasets [international_matches.csv] and [players_22.csv] were prepared for analysis and the creation of the training dataset of the Machine learning model. The preparation consists of fixing the na's values and removing the information of the teams that will not participate in the cup.

* From dataset [international_matches.csv], create training dataset [training.csv] and inference dataset [last_team_scores.csv]. [training.csv] contains the names of the teams facing each other, the FIFA ranking of each team, and the rating of both teams' defense, midfield, and offense. On the other hand, the inference dataset contains the qualification of each team on its last FIFA date.

## EDA

From datasets [international_matches.csv] and [players_22.csv], the notebooks [FIFA26_DATA_PREP.ipynb] and [Getting_Squads_Stats.ipynb] answer the questions listed below. These questions allow us to get an idea of the favorites to win the cup according to statistics.

* Which National soccer teams have the best offence?

* Which National soccer teams have the best defence?

* Which National soccer team have the best midfield?

* Which teams have the highest winning percentage?

* Who are the best players in Qatar 2022?

* What are the most promising teams?

* Does it have any advantage to be the local team?

This question is fundamental. Home teams win more than 50% of the home games. This is due to different reasons, e.g., the familiarity with the field of play, the movement that the visiting teams must make, the feeling of territoriality, the support of the public, and innumerable factors. When the Colombian National Team visits the Maracana stadium to play against Brazil, they tend to lose the match or draw. However, they tend to tie or win when Colombia is local in the Metropolitano stadium. For this reason, to predict the result of the matches from a Machine Learning model, I must define the home team and the visiting team.

## Modeling and Tuning

The [Modeling+Tuning.ipynb] notebook aims to train the Machine learning model that will predict the outcome of the World Cup matches. This notebook chooses one ML model to predict the group stage matches and another for the knockout stage. the difference is that the result of the group stage matches can be a loss, a draw, or a win. On the other hand, in the direct elimination stage, there is only defeat or victory. The best model for each stage is chosen among the algorithms:

* Random Forest
* Ada Boost Classifier
* XGB Boost
* Neural Networks

The XGB Boost model presents the best performance in both stages. Therefore it is tuned, validated, and exported as a pipeline to perform easy inferences.

* Confusion matrix of the group stage model tuned and validated

* Confusion matrix of the knockout stage model tuned and validated

## Predictions

Finally, notebook [Predictions.ipynb] uses the inference datasets and the trained models to predict the World Cup matches and thus find the winner of the World Cup. It is essential to mention that to choose who is the home team in each World Cup match, use dataset [squad_stats.csv], which provides the potential of each team; therefore, the team with more significant potential will be the home team.
