---
title: "Statistical Inference Course Project"
Author Name: Farren Tang
output: html_document
---

#### Overview
This project is spilt into 2 parts. They will be spilt into simulation and statistical analysis of tooth growth data. In the tooth growth data, we will do a statistical analysis to see if there will be significant differences in the means of using OJ or VC. 




Part 2: Statistical Analysis of Tooth growth data 
```{r, loading data}
datadf <- ToothGrowth
```

Generally, Orange Juice tend to be more effective for the tooth growth as compared to VC, as the length tends to be higher. 
```{r, summary of data}
summary(datadf)
ggplot(datadf) +
  geom_boxplot(aes(x = factor(dose), y = len ))+
  facet_grid(~supp) +
  xlab("Dosage levels") + ylab("Length")
```

We conduct T - test to see if the difference in mean is significant:  
H0: mean of OJ will be equal to the mean of VC  
Ha: mean of OJ will not be equal to mean of VC  
```{r, confidence level}
OJdata <- subset(datadf, supp =="OJ")
VCdata <- subset(datadf, supp =="VC")
t.test(OJdata$len, VCdata$len,var.equal = FALSE, paired =FALSE )
```
Since p is not significant, we do not reject the null hypothesis and the mean is not significant, at the 95th CI. 

