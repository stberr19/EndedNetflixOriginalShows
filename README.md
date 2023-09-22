# Ended Netflix Original Shows
![NetflixLogo](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/03c5ec60-3db3-4c47-a1e7-353f5c5b4fe4)

## Project Description
This project focuses on all the Netflix original shows that have concluded their runs, as of August 28th, 2023. Along with this README, the project contains three Excel files: a file of the original data
downloaded from Kaggle, a file of the data after it was cleaned and ready to be used for pivot tables and visualizations, and a dashboard backing up the answers to the questions pertaining to the analysis.

## Dataset Source
The data used for this project was obtained from [https://www.kaggle.com/datasets/aminatl/all-ended-netflix-originals] and was originally scraped by Animat Lawal from [https://en.wikipedia.org/wiki/List_of_ended_Netflix_original_programming].
I acknowledge their efforts in obtaining, scraping, and sharing this data.

## Original Dataset Description
![Screenshot 2023-09-22 145159](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/5837ad17-e444-4f69-987c-11bb5e097343)
In the dataset, there are five columns: the name of each show, the general genre of each show as defined by the Wikipedia page, the date each show premiered, the date each show concluded, and a boolean
determining whether or not each show was cancelled before it got renewed for a second season/release.

## Problems
1. Two very common general genres in this dataset are dramas and comedies. How do dramas compare to comedies in regard to durational success? Is one genre more likely to be better long-term? How do these genres compare to the average genre that isn't a comedy or a drama?
2. Do yearly quarters influence the number of shows premiering and/or the number of shows concluding?
3. How do children's shows perform compared to shows that aren't primarily intended for children? (this question was created during data cleaning when there were more children's shows than the initial data suggested)

## Data Cleaning
During my cleaning process, one of the first things I noticed was that the data scraped included lots of genres where two words were combined into one when they shouldn't be. Below are just three cases
where this occurred.
![Screenshot 2023-09-22 143104](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/09808dec-a8ba-43e3-b675-3cc552754e74)
To fix this, I filtered out all of the genres that needed spaces and manually added them where needed.

I also noticed a considerable number of shows that didn't have a genre listed. Below are a few examples where this happened.
![Screenshot 2023-09-22 143454](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/ddf19bc6-d85e-4212-bcbd-e80fa6997646)
However, I looked into the Wikipedia page, where the data was scraped, and I found that all of the shows where this was the case were categorized under children's shows. As such, I replaced the blank cells
in the genre column with "Children's" to indicate that they're a kids show. However, this made kids shows one of the largest genres of shows within the dataset. Because of this, I added problem 3 to my
list of general overarching questions I wanted answered as part of my analysis.

The final step of my cleaning was changing the cancellation boolean so that all entries with "1" were true and all entries with "0" were false. This was done not just to make it easier for myself to
understand the data in that column, but also to make it easier for the stakeholders later on when the dashboard would be created. The image below displays how the column originally appeared.
![Screenshot 2023-09-22 143721](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/f522f800-d1fb-418a-b0ff-fca87ebace25)


## Analysis
With dramas and comedies being very prevalent, I used a nested if function to see if a show was a comedy drama, a comedy, a drama, or neither. I did this by searching each genre to see if
"comedy" and/or "genre" appeared anywhere within the genre name. It's worth noting that there were several instances where instead of "comedy drama", the genre was "dramedy". As such, I also accounted for
those cases such that their overarching genre was "comedy drama". This column was made to simplify problem 1 instead of going through every individual genre.
![Screenshot 2023-09-22 143905](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/c849263a-4c07-4829-9c2e-eabc6aed8ed9)
Similarly, I made a column based on an if statement where a show with "children's" as the genre was listed as a children's show, while all other genres were listed as "other". This was made to simplify
problem 4 to distinguish shows that are and aren't kids shows.
![Screenshot 2023-09-22 144047](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/997c3253-ff02-4e1b-8a67-c8c8577230c7)
For both the premiere and finale dates, I extracted the month from each date and used the months to ultimately create a quarter column based on nested if statements. I also extracted the year from each of
the dates.
![Screenshot 2023-09-22 144146](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/14b7f867-7fd8-4225-ba7e-c2b117e9925d)
This was done to ultimately solve problem 2.

## Dashboard Description and Takeaways
![Visual1](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/2cd8b1f9-60e8-47d8-99a4-2d3dadc1b9e7)
This is a donut chart that focuses on how comedies compare to dramas and is made up of four smaller donuts. The innermost donut focuses on shows that are comedies, the secondmost
inner donut focuses on comedy dramas and dramedies, the secondmost outer donut focuses on dramas, and the outermost donut focuses on shows that are neither comedies nor dramas. We notice that both comedies
and dramas on their own tend to have a higher likelihood of being renewed for more seasons, and likely perform better, than shows that don't fall in either category. However, they don't perform as well
as shows that incorporate both drama and comedy into their overall show. Along with that, comedy dramas that **do** get renewed have a higher likelihood of having a longer "life expectancy" than shows
that aren't comedy dramas. In other words, the potential for a show to last for 4, 5, 6, or even 7 seasons is much higher if the show is a comedy drama. This may be something Netflix may want to consider
going forward with their television shows as a way to increase customer engagement through the shows they create. The graph also makes another fact apparent: most shows do not get renewed for a second
season. This will be an important fact to consider when we look over upcoming visuals.
![Picture2](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/06e9b2a3-597e-437c-9457-5bd32b7a1db2)
This is another donut chart comparing the duration of children's shows, represented by the inner donut, compared to other Netflix originals, represented by the outer donut. Immediately, a
new trend emerges with children's shows that cannot be said about dramas, comedies, or even comedy dramas: most of the shows are renewed and last for at least two seasons. This would indicate
that not only are children's shows likely faring better than many other Netflix shows, but also that Netflix is a reliable platform that customers with children can use to easily navigate to original
Netflix content targeted for children. With Netflix having a child account option for those wanting to only access kid-friendly content, Netflix makes it very easy for customers with children to navigate
their service and bringing both themselves and their children back to the platform, ensuring that children's shows will continue to succeed with the steps being implemented.
![Picture6NoFilter](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/29d3f2e1-0c8b-48e4-b689-19c7daf6898e)
This bar graph shows in which natural seasons the shows that have now concluded premiered. This chart displays any series that has ended by now, regardless of whether or not it was renewed. Overall, we can
see that fall has, so far, been the most likely time for a show to premiere if it's ended by now.
![Picture6](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/f21eb4e4-9c77-4d7a-b79f-c0a7bb2f7854)
The image above represents same bar graph, but only if we consider series that were renewed for at least a second season. There is a significant increase in shows that premiere in winter and spring. This would
indicate that if a show premieres in the winter or the spring, the show has better odds of getting renewed for another season than a show that premiered in the fall. It is important, however, to note that
regardless of the season, it is still more likely that a show doesn't get renewed for another season. This means that a producer working on a Netflix original series that's debuting in winter may have
better odds of the series surviving than if it debuted in the fall, but the odds are still against them. This may indicate that audiences tend to prefer shows that air in the winter or the spring. However,
this could also mean there's more competition for shows that end in the fall, making it more difficult for them to survive against competitors.
![Picture7](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/5cdcb0d7-1cae-410f-a168-575cfa4dab54)
This bar graph shows the natural seasons shows concluded. Similar to the premiere bar graph, fall is the most popular time for shows to have their finales, and this comes as no surprise because again, most
shows do not get renewed for another season.
![Picture7](https://github.com/stberr19/EndedNetflixOriginalShows/assets/144372443/e6d8858e-602f-409a-aa78-cd363b157c02)
If we just look at long-term series, the biggest increase in long-term finales takes place in the spring. Overall, the spring, summer, and fall seem to be the main seasons when most shows have their final
season. This would seem to indicate that having a season air in the winter would make it more likely to be renewed again compared to the spring, summer, and fall, and to an extent, that indication is
correct. If a show is long-term and it airs a season in the spring, summer, or fall, there is a 25% increase in the possibility that the season being aired will be its last. In terms of long-term stability,
shows that air in the winter have the best likelihood of surviving in the long run, both because there is an increased possibility that the show will get renewed for a second season and because there is
an increased possibility that the show will not have its finale that season. For Netflix to increase the number of long-term shows it creates, it may want to give new series a random debut season to see
how it stacks against competition, but for serious shows that keep customers coming back, it may be worth it for Netflix to air them in January, February, or March.

## Conclusions
Overall, there are three main takeaways we can make from this analysis:
1. Comedies and dramas tend to do perform better than shows that don't incorporate elements of either, and shows that incorporate elements of **both** tend to perform better than all three groupings.
2. Children's shows tend to have a higher likelihood of getting renewed than shows that aren't, meaning Netflix may want to consider tailoring advertisement towards parents of young children.
3. Winter is the most successful season when it comes to a show's likelihood of continuing, and Netflix may want to use that block for shows that get renewed for the first time and want to lengthen its run for as long as possible.
