---
layout: page
title: Research
permalink: /research/
---

# <span style="color:#FF7BA9">Research</span> 

<p>&nbsp;</p>

During my research career, I have been involved in several **astronomy modeling projects**, from dwarf stars to supernovae. I here give an overview of my main research interests. 

[My Google Scholar page](https://scholar.google.se/citations?user=XUz96SUAAAAJ&hl=en) for a list of published articles. 

### Main research interests
* [Machine learning in astronomy](#ml)
* [Chemistry in supernovae](#chemistry_sn)
* [Modelling the winds of red giant stars](#agb)



<p>&nbsp;</p>


<hr style="height:1px;border:none;color:#333;background-color:#333;" />

##  Machine learning in astronomy<a name="ml"></a>

I have recently been playing around with using machine learning methods to expand on first principle modeling for a few different simulations. Historically interpolation in e.g. a model grid would be done linearly in logspace, however, this does not always result in accurate predictions, especially if the underlying physics is complicated. We can do much better with machine learning methods. 

Below are some examples of work in progress. 

### NLTE corrections for stars

I am currently in a collaboration trying to improve the 3D NLTE corrections to Fe1 and Fe2 abundances. Corrections have been calculated for ~20 000 Fe1 lines and ~4000 Fe2 lines, for ~800 stellar parameter combinations. The behavior of these corrections is complex and badly captured by linear fits (right panel of Fig.2). Previously one would fit corrections between grid points by using linear interpolation, however, this also missed some of the complexity. 

Using a deep learning neural network, I constructed a machine learning model to predict the corrections. The Fe2 results for a test set (80-20 split training-test set) are shown in the left panel of Fig. 2. As seen the model is highly accurate and the ml model 3D NLTE corrections are very similar to the first-principle physics model 3D NLTE corrections. In the case of Fe2, shown in the figure, the standard deviation is 0.016, the mean average error is 0.01 and the max error is 0.13, with R2=0.99. For Fe1 (not shown) the behavior of the ml model is similar: the standard deviation is 0.02, the mean average error is 0.012 and the max error is 0.16, with R2=0.99. Consequently, the behavior can be captured well by the ml model, and this model can be easily used by other researchers to quickly calculate NLTE corrections for their spectral data. 



**Fig 2. *Left panel*: The neural network model results, comparing the real first-principle physics model 3D NLTE corrections to the ml model corrections. *Right panel:* Same as left, but instead fitting a linear regression model.**
<p align="center">
  <img src="/img/nltecorr_ml.png" alt="Difference between linear and ml model"/>
</p>


Some technical info about the ml model: a 200x200x200 neural network regression was used. The data was initially split 80-20 training set-test sets. All the hyperparameters were fit using a 5-fold cross-validation method on the training set, and the errors mentioned are from training the ml model on the training set, and then evaluate it on the test set. The preferred size of the neural network was found by increasing the network size until doing so no longer yielded better fits. The other hyperparameters were alpha (regularization) and tolerance (precision of the solution), which were found by a parameter search to maximize the R2 score. 



### AGB star model grid

In this [paper](https://www.aanda.org/articles/aa/abs/2019/06/aa35366-19/aa35366-19.html) we constructed a large grid of AGB stars models, where the inputs are the stellar parameters and the main outputs are wind/no wind, mass-loss rate, wind velocity, and dust properties. One would want to have a scheme for interpolating between the model results or extrapolate outside the grid to use model results in e.g. stellar evolution, however, the behavior of the models can be very non-linear. Using neural networks regression the first principle outputs can be accurately predicted. 

This approach can also be used in categorizing AGB stars, shown below. The border between wind/nowind for the DARWIN models can be predicted with high accuracy. 


**Fig 1. The wind and no wind border of a slice of the model grid. Red/blue color indicates wind/no wind, the filled background colors are the ml model predictions, and the points are the physics model results.**
<p align="center">
  <img src="/img/m1_ml.png" alt="Wind or no wind border of AGB models"/>
</p>




<hr style="height:1px;border:none;color:#333;background-color:#333;" />

## Chemistry in Supernovae <a name="chemistry_sn"></a>

[Github link to the chemical networks](https://github.com/sliljegren/chemical_network)

[New paper!](https://arxiv.org/abs/2203.07021)

[Proof-of-concept paper](https://www.aanda.org/articles/aa/full_html/2020/10/aa38116-20/aa38116-20.html)

To accurately estimate supernovae (SNe) yields from spectra, molecule contribution needs to be accounted for. During my time in Stockholm, I implemented a new chemistry module (which contains molecular formation) in the SN spectral code SUMO. By comparing the new model results with future observations from James Webb Space Telescope (JWST), the hope is to provide unique tools to constrain the chemistry in the supernova and further our understanding of the nucleosynthesis yields of different types of supernovae.

**Fig.3. Example of output spectra from the new mol-SUMO models.**
<p align="center">
  <img src="/img/spectra_ir.png" alt="IR spectra"/>
</p>


<hr style="height:1px;border:none;color:#333;background-color:#333;" />

## Modelling the winds of red giant stars<a name="agb"></a>

[Movies made with 3D models](https://www.astro.uu.se/~bf/movie/AGBmovie.html)

[Thesis](http://uu.diva-portal.org/smash/record.jsf?pid=diva2%3A1196675&dswid=6235)


During my time as Ph.D. I worked on two major projects: 3D models of cool giant stars or AGB stars, to study the pulsations and small-scale structures caused by convections, and 1D wind and dynamical atmosphere models, to calculate the wind properties for large grids of stellar parameters. 

AGB stars are the end-life state of stars with a similar mass to our sun. Stars like our sun develop into luminous cool giants towards the end of their lives. These stars are as large as Earth's orbit, pulsating and non-spherical. They are strongly affected by violent dynamical processes. Giant convection cells reach deeply into the stellar interior and bring newly produced material, such as carbon, to the surface of the star. Stellar winds lead to a runaway mass-loss process, that eventually turns these stars into white dwarfs. The winds are driven by radiation pressure on dust grains, which form in the extended dynamical atmospheres of these stars. Through the winds, the cool giant stars enrich the surrounding interstellar medium with the building blocks of new generations of stars, planets, and life.   


**Fig.4. 3D star-in-a-box models of AGB stars. From left top: temperatre, perssure, luminosity, entropy.**
<p align="center">
  <img src="/img/agb_stars.png" alt="3D models of AGB stars"/>
</p>






