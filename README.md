Link to site: https://zachnguyen.github.io/Exoplanets-Visualization/

# Introduction

Not very long ago, the first people to discover exoplanets and jumpstart the hunt for worlds much like our own has [won the Nobel Prize for Physics](https://www.newscientist.com/article/2218951-nobel-prize-in-physics-for-discovery-of-exoplanet-orbiting-a-star/#:~:text=The%20Nobel%20prize%20in%20physics,Earth's%20place%20in%20the%20cosmos.!). 

Exploring distant worlds not only enhances our scientific knowledge, but also is fascinating in the own sense. It speaks to our common sense of curiosity and adventure into the unknown. In these times of pandemic and divisiveness, perhaps a common fascination of the universe will unite the human race regardless of gender, ethnicity or socio-economic background.

![](https://www.economist.com/sites/default/files/images/2018/10/articles/main/20181006_stp003.jpg)

As a data scientist and an astrophysics enthusiast myself, I want to do these findings justice by sharing two key visualizations. The purpose of this blog is to display the power of data visualization to illumninate some of the coolest things we have figured out while picking up some astrophysics knowledge on the way.

The data was collected through the API of [NASA's exoplanet archive](https://exoplanetarchive.ipac.caltech.edu/). It was modeled through python with the help of excellent open source data-viz engine like Bokeh and Plotly. 

Without further ado, let's arrive at our first visualization, a visualization through space ...

# Coordinate 3D Scatterplot of Stars that contain Exoplanets

*Note: You can play around with the interactive 3D plot by zooming (mouse wheel), looking around (left mouse) or panning (right mouse). Reset camera to go back to default view and hover in for the finer details for each.
<iframe src="/images/Star_Coordinate_Viz_Norm.html" sandbox="allow-same-origin allow-scripts" width="120%" height="700" scrolling="no" seamless="seamless" frameborder="0"> </iframe>

The plot shows a cartesian coordinate of the stars we have encountered which contain exoplanets in its systems. Some interesting points that we can learn from the plot are:
- The stars we've found exoplanets in are not very uniformly dispersed. If we've collected perfect data, this would mean something in the trend. Unfortunately, the non-uniform distribution is due to availability bias (We've only had the ability to look closely on a certain patches of the sky and not everywhere, therefore we didn't find exoplanets everywhere).
- The cluster that formed the clear columns of stars are the field vision of the Kepler Space Telescope (the one designed to find exoplanets among stars). In fact, we can see the sky path that Kepler was in charge of by reseting to default camera position, zooming in to maximum using your mouse wheel (you'll be in Earth's position), then looking around (left mouse). With a bit of luck, you should find a sky patch that looks like this:

![](https://supernovacondensate.files.wordpress.com/2012/07/kepler-set-7.jpg?w=700)

- According to the density of this cluster of the stars that contain exoplanets, we should expect exoplanets to appear as densely (basically everywhere) in every other direction we look. That's a good sign. This science is young and there is much to explore.
- I've coded the size of the marker for the radius of the stars (bigger size means bigger stars). By going to the default camera position, we can see that bigger stars don't appear in the Kepler cluster, but does everywhere else. The most likely reason for that is that we are more likely to find exoplanets in bigger star since we can observe them more closely for light dip (which shows periodic transit by planets) or gravitational anomaly (which shows that the star's path might be influenced by a planet with large gravity).
- I've also coded the color for star temperature with a diverging colorscale and normalize the star temperature to a 0-1 range. In this way, even though we miss out on the absolute temperature data (let's face it, it will be hell on Earth before we can intuit what 12,000K is like), we gain a clear relative comparison in the data (blueish markers are cooler than roughly 50% of all the stars whereas reddish markers are hotter than roughly 50% of all the stars). 
- For instance, we can learn here that larger stars are more likely to be cooler. This is because these stars have lived past their young and dangerous life, burning away their fuel incessantly. Now that they are no longer running fusion, they cool down and cause the gas to expand.
- Feel free to look around more. Perhaps you will catch something that I haven't. The devils are in the detail!

# Tabular Scatterplot of Planet Properties & Characteristics

Now that we've had a look at the stars, we can get down the the planets. This visualization will show a few select exoplanets characteristics plotted against one another. Discovery Methods are color-coded. The 8 solar system planet values will also be included for extra comparison and intuition.
* Note: Some of the axis are in log scale. Click the tab name up to to switch tabs, click on the legend to hide the exoplanet data and see only the solar system planets and hover on the data point to see the planet name, mass in Earth Mass and radius in Earth Radii.
<iframe src="/images/Pair-wise_exoplanet_characteristic.html" sandbox="allow-same-origin allow-scripts" width="100%" height="700" scrolling="no" seamless="seamless" frameborder="0"> </iframe>

Now it's time for the analysis:
- In the Radius to Body Mass scatterplot, we see two clear clusters of planets and a mysterious semi-Z line. The clusters are of planets with high radius & mass (Gas giants), and lower radius & mass (Rocky planets). This data fits very closely with the solar system, as we see the clear distinction between the inner planets (Mercury, Venus, Earth and Mars) and the outer gas giants (Saturn and Jupiter). Neptune and Uranus appears to be in between (Ice giants). What about the mysterious Z line? A closer observation shows that much of the Z-Line observations were exoplanets discovered by the Radial Velocity method. Since this method relies on indirect gravitational influence observations, astrophysicists had to make extrapolations regarding their mass and size, so what we are seeing are human-fitted models. This goes to show that in data science, understanding the domain and how your data is collected is pivotal to making good judgement about it.
- On to the second tab, Semi-Major Axis vs Body Mass. Though not technically correct for planets with strange orbits, you can think of Semi-Major Axis as generally the distance between the planet and its host star. The chart shows three clusters. Two of them we already discussed, the Rocky planets are typically close to their stars and much of their atmosphere are stripped away by the radiation emitted from the star, while Gas giants are far away and retain their bloated atmosphere. However, the third cluster is one which has recently astounded astrophysicists and paved ways for new understanding of planet formation. We see planets will extremely high mass who are very close to their star! These types of planets have been named Hot Jupiter and the nascent [Planetary Migration Theory](https://en.wikipedia.org/wiki/Planetary_migration#:~:text=Planetary%20migration%20occurs%20when%20a,especially%20its%20semi%2Dmajor%20axis.) think that they might have been born outside but migrated to the inner orbits of their star system. This is huge! Imagine the effect Jupiter would have had on the Earth if it migrated close to us. Perhaps we're more lucky than we can appreciate. The take away here is that by taking the time to slice and dice variables in different ways, we can truly make surprising discoveries about our data.
- Another key point about the second graph is the discovery method distribution. We see a clear divide between the two major techniques: Transit and Radial Velocity. Namely, Transit techniques are good with detection planets close to their star, whereas Radial Velocity are better at detecting planets further from their stars. 
- Something else one may have noted is that the solar system planets seem like outliers to the graph that don't belong to any particular clusters. While this maybe the case, it should be noted that we may commit [survivorship bias](https://en.wikipedia.org/wiki/Survivorship_bias#:~:text=Survivorship%20bias%20or%20survival%20bias,a%20form%20of%20selection%20bias.) due to the ease of finding planets closer to their star (easier to see directly) or with high mass (easier to see indirectly). Because of their lack of visibility, exoplanets similar to planets in our solar system may simply have not "survived" our filter though it doesn't mean that they are not there.
- The third graph describes an interesting quality of planets, their eccentricity. Simply put, the more eccentric a planet is, the more eliptical its orbit, causing extreme seasonable patterns (scorching for a few days, then freezing for most of the year). We can view this as an additional criteria from being in the Goldilock Zone to figure out which planets are habitable. The graph shows that most of the solar system planets are non-eccentric. The final graph shows the Equilibrium Temperature (its supposed temperature baring any anomaly) of exoplanets plotted against their Semi-Major Axis. We can confirmed a general trend here that the closer a planet is to its star, the hotter it gets, possibly due to the stars radiation.  

# Conclusion

Exoplanet detection and analysis is a fascinating young science full of implications. Due to the open-source data policy, anyone can help with the hunt, especially data scientists. We've gone through quite a journey with only two visualizations. I hope you had some take aways in both data science and astrophysics. If you would like to see how to create these visualizations for your own use cases, feel free to check out [code](https://github.com/zachnguyen/Exoplanets-Visualization/blob/master/EDA%20notebook/Exoplanet_Visualization.ipynb) I used to create them.
