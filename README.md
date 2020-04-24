# ElSayed_Capston
---
title: "2020 Capstone Assignment"
author: "Retta El Sayed"
date: "4/23/2020"
output: html_document
---

## R Markdown
Statistically Design an Experiment. Write it in an R markdown and submit knitted html. You can collaborate in so far as giving and receiving feedback from colleagues. (5 pts per item!)
For a rubric on how to write this, see Chapter 10 in JABSTB. Follow that multi-step format!!!

## Question 1

Provide a brief background and significance about a specific research problem that interests you. It could be project you’re involved with now, or a rotation project, or something you’d like to work on. The reader will need to understand enough background to make sense of the experiment you propose below. Keep it brief. In one short paragraph.

**Strokes and heart attacks are responsible of up to 60% of the deaths in the first world countries. It usually occurs due to atherosclerosis though a cholesterol plaque. However, up to 37% of patients with cryptogenic stroke have a condition called Carotid webs (CaW), which is not made of cholesterol accumulation. CaW are is a shelf-like connective tissue projections into the internal carotid artery (ICA) lumen. In a normal carotid bulb, the divergent geometry creates a recirculation zone with low flow, high Particle residence time (PRT), and altered Wall shear stress. PRT is the time that takes for a fluid particle to clear off a specific area in the vessel. In patients with CaW, the geometric factors lead to recirculation zone and complex flow region susceptible to platelet aggregation and thrombus formation. High PRT is the main variable in the vasular hemodynamics that has been shown to be predictive of platelet aggregation and thrombus formation in both in-vitro and in-vivo studies. The high PRT in CaW produces an environment for the development of thrombus, which can then result in strokes. The project consists of quantifying the ICA hemodynamics using Magnetic Resonance Imaging with 4D Phase contrast scan protocol. These measurements will be done in patients with CaW and in healthy, age-matched control. We are hypothesising that CaW will result in higher particle residence time, higher shear stress, and higher acceleration in comparison to healthy control subjects.The main aim of this project is to understand the correlation of these factors to thrombus formation, and the leading to stroke.**

## Question 2

Briefly state something that is unknown about this system that can be discovered through, and leads to, an experiment. For example, "It is not known whether....."

**There have been no studies to date show blood flow patterns and thrombus formations in CaW patients. Moreover, it is not known whether carotid webs introduced complex flow patterns results in thrombus and eventually leads to strokes. This can be tested through a comparison through patients with CaW and healthly controls, while quantifying CaW vascular hemodynamics.**

## Question 3

Make an “if” “then” prediction that is related to item #2. It should be of the general form, “if X is true, then Y should happen”.
**If CaW is related to higher particle residence time in comparison to healthy controls, then CaW will result in change of the vascular hemodynamics in the ICA, therefore, thrombus formation.**

## Question 4

What dependent variable will be observed to test this prediction in item #3? What predictor variable will be used to manipulate the system experimentally? Define the inherent properties of these variables (eg, are they sorted, ordered or measured).

**In this experiment, our predictor variable (Independent) is the  two groups the healthy control group and the CaW patients, which is sorted. Our response variable (dependent variable) is the particle residence time measurements, which is measured.**

## Question 5

Write a statistical hypothesis.  There should be a null and alternate. These should be explicitly consistent with the prediction in item #3 and the response variable in #4. In other words, make sure the statistical hypotheses that you write here serves as a test of the prediction made in item #3.

**Null: The mean difference of particle residence time measurements between the healthy controls and the CaW patients will equal to 0.**
**H0**: $\mu_{control}$ **=** $\mu_{CaW}$ 

**Alternate: The mean difference of particle residence time measurements between the healthy controls and the CaW patients will not be equal to 0.**
**H1**: $\mu_{control}$ **=/=** $\mu_{CaW}$ 

## Question 6

What is the statistical test you would use to test the hypothesis in item #5? Briefly defend what makes this appropriate for the hypothesis and the experimental variables. If there are alternatives, why is this approach chosen instead? Points will not be awarded if the justification involves something like "because everybody does it this way".

**Two way randomized ANOVA will be used as a statistical analysis test. This analysis was chosen since the experinment has two different independent variables (factors) the control healthy patients and the patients with CaW, moreover, the particle residence index (dependent variable with 4 levels) is measured in 4 different time steps (0.13, 1, 3, 5 mintues). This experinment is completely randomized since each different subject is assigned to one of the groups and measured at different time steps. All our measurements are independent from each other. We have divided our study subject into two main categories patients with CaW and age-matched gender volunteers without CaW.**

## Question 7

List the procedures and decision rules you have for executing and interpreting the experiment. These procedures range from selection of experimental units, to randomization to primary endpoint to threshold decisions. Define (and defend) what you believe will be the independent replicate.

**The Study will include participants age >18 years and CaW diagnosed on a prior digitalsubtraction angiography or CTA after a consensus read by neuroradiologist or neurointerventionalist.**
**15 patients will be recruited with CaW and 15 control subjects. Demographic and stroke risk data will be recorded from all subjects using a questionnaire that includes age, gender, and ethnicity as well as history of prior cerebral infarction or TIA, hypertension, hyperlipidemia, diabetes mellitus, smoking, and drug use.**
**All studies will be performed on a research-dedicated 3T Prisma MRI Siemens scanner. Quantifing the vascular hemodynamics in the carotid artery bifurcation will be done using 4D flow MRI protocol. A combination of commercial software and custom-written Matlab code will be used for analysis of the 4D flow data and characterization of the flow metrics.**
**PRT will be evaluated using the virtual ink technique, whereby a continuous wavefront (virtual ink) is released upstream and propagated by the velocity field as governed by the 3D advection equation. The use of the Eulerian advection framework rather than traditional Lagrangian individual particle tracking reduces errors that are inevitable due to spatial and temporal resolution in the 4D MRI velocity field. We will calculate the PRT for all voxels and pixels in the flow field. In this technique, patches the size of pixels but warped to lie on the surface of the wall are evaluated for PRT. We will use the previously determined threshold of 7.7 seconds to separate regions where PRT is high where threshold will be summed for each subject all pixels. The PRT for the entire flow field will be compared between the CaW patients and the healthy controls. The comparison will directly answer the hypothesis that carotid arteries with CaW will demonstrate higher particle residence time in comparison to control subjects.**
**To interpret the experiment, a type1 error threshold of 5% (α = 0.05) and a type2 error threshold of 20% (β = 0.2). A sample size of n = 15 will be used for this experiment in order to achieve high desired power value.**

## Question 8

Produce a graph of a simulation for the expected results. Create a dataMaker-like function in R to create and plot the data. Label and scale any axis. The graph should illustrate the magnitude of the expected response, or the level of response that you expect to see and would be minimally scientifically relevant. Be sure to illustrate any variation that is expected.

**The Figure below shows expected results; patients with CaW will demonstrate altered hemodynamics in comparison to normal subjects including high particle residence time due to high fluid shear gradients and development of flow vortices  near the web.**
```{r}
#libraries needed
library(tidyverse)
library(ez)
library(viridis)

# Study parameters
n <- 20
sd <- 5
means <- c(90, 90, 70, 20, 60, 5, 40, 0)

# Creating a Flydata Maker function to generate our data 
flydatamaker <- function(n, means, sd) {
  params <- data.frame(n, means, sd)
  data <- as.tibble(apply(params, 1, function (x) rnorm(x[1], x[2], x[3])))
# Changing the first row (labels of the columns) 
  oldnames <- c("V1", "V2", "V3", "V4","V5", "V6","V7","V8")
  newnames <- c("CaW_0.13 minutes", "Control_0.13 minutes",
                "CaW_1 minutes", "Control_1 minutes", 
                "CaW_3 minutes", "Control_3 minutes", 
                "CaW_5 minutes", "Control_5 minutes")
  data <- data %>% rename_at(vars(oldnames), ~newnames)
# Munging the data 
  data <- pivot_longer(data, everything(), 
                         names_to =c("Patient", "Time"),
                         names_pattern= "(.*)_(.*)",
                         values_to="Particle_Index") %>% 
           mutate(id=as.factor(paste(
             rep(rep(c("a","b"), times=2), n), 
             rep(1:n, each=8), 
             sep="")),
             Patient=as.factor(Patient),
             Time=as.factor(Time))
data}
data <- flydatamaker(n, means, sd)
# Creating the plot
ggplot(data, aes(Time, Particle_Index, group=id))+
  geom_point()+
  geom_line()+
  scale_x_discrete(limits=c("0.13 minutes", "1 minutes", "3 minutes", "5 minutes"), labels=c("0.13","1", "3", "5"))+
  labs(title="Particle Resident Time in Carotid Web Patients and Healthy Volunteers", x="Time (mintues)", y="Particle Residence Index")+ theme(plot.title = element_text(hjust = 0.5)) +scale_color_viridis(discrete=T)+ facet_grid(~Patient)
```

## Question 9

Write and perform a Monte Carlo analysis to calculate a sample size necessary to test the hypothesis. This Monte Carlo must test the primary endpoint.
```{r}
AnovaTest<-ezANOVA(data=data, dv=Particle_Index, wid=id, within=Time, between=Patient, detailed=F)
AnovaTest
```

```{r}
# since the experinment passes the ANOVA test, we preform Monte Carlo as post hoc analysis:
sims=100
pval <- replicate(
  sims, {
    data <- flydatamaker(3, means, sd)
   sim.pwt <- pairwise.t.test(data$Particle_Index, interaction(data$Time,data$Patient), p.adjust="none")
   padj<- p.adjust(sim.pwt$p.value[1,1], method="BH", n=6)})
pwr.pct <- sum(pval<0.05)/sims*100
paste(pwr.pct, sep="", "% power")
```


## Question 10

Write up it all in RMarkdown. Code chunks to illustrate specific points are welcome other than for the Monte Carlo code. Knit and submit and upload the html document by the due data. If it is readable to your best friend, it is readable to us.

## EXTRA CREDIT

Github is an important resource for sharing data/analyses and collaborating.  In fact, 3 different Github repositories were used for the material in this course. We encourage you to submit your capstone as a Github page, as a gentle way to play with Github. See the directions Jessie wrote up: GitHub_pages_IBS538.pdfPreview the document

If you submit your capstone on Github, we'll need you to knit and submit a different document on Canvas. For that, just open up a blank Rmd. Only put the link to your github page in it. Knit and submit its html on canvas. The markdown code for a link is like this:

Thanks for such an exciting semester Austin, Jess, Lauren & even you, TJ! [Please click here to see my capstone project on Github.](https://url_of_my_capstone (Links to an external site.))
