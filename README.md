# F1-elo
## An ELO system for my career playthrough of F123.

### What is meant by the term "ELO"?
Elo is a form of rating system that enables the relative strength of a player to be measured in comparison to other players in a given game.

### Implementing ELO system in Formula 1?
The implementation of the ELO system in Formula 1 is a challenging endeavour. The ELO system functions effectively when there are two competitors engaged in a contest, with a clear winner and loser (or, in some instances, a draw). However, Formula 1 is a team sport, with each team comprising two players competing *against* each other. Additionally, numerous other factors influence the accurate assessment of an individual's skill, including the ranking of the vehicle, the occurrence of a DNF due to a racing incident, and so forth.

### Roundabout way to go about it?
There are multiple avenues through which the ELO system can be integrated into Formula 1. My inspiration stems from this video from [Mr. V's Garage](https://youtu.be/U16a8tdrbII?si=7ovFY9ZekjeoWY6S).

### How did I go about it?
Firstly, determining the factors that should define your ELO is a challenging task. Given that I am creating this ELO ranking for my career mode of my F123 playthrough, it is even more difficult as there is a paucity of data to work with. I was only able to consider the finishing positions, which made it an easy choice to use as a factor. However, this does not accurately reflect one's skill level, as the finishing position is largely determined by the car rather than the driver. Therefore, I also considered the comparison between teammates as a factor. The final factor I considered was the extent to which one driver outperformed their teammate. The greater the gap in their finishing position, the more points are awarded, and vice versa.

### Now what?
Having obtained all three requisite factors for calculating the ELO, I have developed a Python code to perform this calculation. The code accepts a .csv file containing the drivers and their finishing positions and returns a second .csv file containing the drivers' final ELO.

### What formula did you use?
This is a challenging question to answer, as I am uncertain about the accuracy of the formula. I am unsure if the formula accurately depicts the desired outcome or if there are any flaws in the formula itself. Nevertheless, I will proceed with the analysis. If you wish to derive the formula and assess its efficacy, you are welcome to do so.

$$ Score_{expected}=\frac{1}{1+10^{\frac{ELO_{opponent}-ELO_{player}}{400}}} $$
$$ ELO_{new}=ELO_{player}+k\times Score_{expected}+k\times (Diff-Score_{expected}) $$
