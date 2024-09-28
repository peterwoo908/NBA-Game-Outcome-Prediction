# NBA Game Outcome Prediction
This project is a classification predictive analysis for NBA Game Outcomes (Win/Loss)

## Presentation/Report
[https://docs.google.com/presentation/d/1aYJCqzZprGAV6aEg3wzsKqKHVQ5KXAppZwVB_7i6Sh4/edit?usp=sharing]

## Data
The data used in this analysis came from kaggle and is in the games.csv.zip file. It included data from all NBA games (2003-2022). Variables included team points, assists, rebounds, shooting percentages, etc.

## Methodology
When predicting the outcome of a basketball game, the stats from the game are not available before the game. In a traditional predictive model, you would use stats from the associated outcome to predict the outcome. However, this process is not applicable to sports. Therefore, I decided to use **Rolling Averages** from a team's last **n** number of games to predict the outcome of their next game. There was an extensive amount of data wrangling involved to achieve this format to feed into the machine learning models.

A main focus of this project was to discover how tuning the hyperparameter of **n** affected prediction accuracy. In this project, I experimented on the Random Forest Model using values of 5, 10, 15, and 20 for **n**.

## Variables

Outcome Variable: TARGET_WIN (Outcome of Team's next game: 1 = Win, 0 = Loss)

Predictor Variables:
| Variable Name  | Type        | Description                                                                                             |
| -------------- |:-----------:| --------------------------------------------------------------------------------------------------------|
| PTS_n          | Float       | Average number of points scored in last **n** number of games                                           |
| AST_n          | Float       | Average number of assists in last **n** number of games                                                 |
| REB_n          | Float       | Average number of rebounds in last **n** number of games                                                |
| FG_PCT_n       | Float       | Average field goal percentage in last **n** number of games (Decimal from 0 to 1)                       |
| FT_PCT_n       | Float       | Average free throw percentage in last **n** number of games (Decimal from 0 to 1)                       |
| FG3_PCT_n      | Float       | Average 3 point field goal percentage in last **n** number of games (Decimal from 0 to 1)               |
| WIN_n_x        | Float       | Win percentage in last **n** number of games (Decimal from 0 to 1)                                      |
| diff_n_x       | Float       | Average point differential in last **n** number of games                                                |
| home_next      | Binary      | Is next game being played at home arena (1 = Yes, 0 = No)                                               |
| PTS_opp_n      | Float       | Average number of points scored in **opponent's** last **n** number of games                            |
| AST_opp_n      | Float       | Average number of assists in **opponent's** last **n** number of games                                  |
| REB_opp_n      | Float       | Average number of rebounds in **opponent's** last **n** number of games                                 |
| FG_PCT_opp_n   | Float       | Average field goal percentage in **opponent's** last **n** number of games (Decimal from 0 to 1)        |
| FT_PCT_opp_n   | Float       | Average free throw percentage in **opponent's** last **n** number of games (Decimal from 0 to 1)        |
| FG3_PCT_opp_n  | Float       | Average 3 point field goal percentage in **opponent's** last **n** number of games (Decimal from 0 to 1)|
| WIN_n_y        | Float       | Win percentage in **opponent's** last **n** number of games (Decimal from 0 to 1)                       |
| diff_n_y       | Float       | Average point differential in **opponent's** last **n** number of games                                 |
## Algorithms

**3 Algorithms were implemented:**
F1 Score (Harmonic Mean of Precision and Recall) was used to assess performance
Rankings of Model Performance:
1. Random Forest (F1 = 0.62)
2. Adaptive Boosting (F1 = 0.61)
3. Decision Tree (F1 = 0.60)

**Additionally, Voting Ensembles were implemented:**
Hard Voting Ensemble (F1 = 0.619)
Soft Voting Ensemble (F1 = 0.613)
