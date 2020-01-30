##############################################################################
## IMT 572 Final Project, Data Analysis & Visualization 
## Author: "Willie Nakpil"
## Description: Here is the code I used for my Final Project in Intro to Data Science
##              Analyzing Males in the US Workforce from 1980-1987
##############################################################################

#install.packages("data.table")
#install.packages("plm")
#install.packages("ggplot2")
library(plm)
library(data.table)
library(ggplot2)
data(Males)
Males <- data.table(Males)
head(Males)
summary(Males)
?Males
?hist
hist(Males)

#Plot 1 How school impacts wages faceted by ethnicity
ggplot(Males, aes(x=school, y=wage))+
  geom_jitter(aes(color=occupation))+
  facet_grid(ethn~.)+
labs(title="Total Males Years of school vs. wage, faceted by ethnicity",
     x="Years of School",
     y="Hourly Wage")

###Plot 2 Sales Workers Only, facet by married
Sales_Men <- Males[occupation=="Sales_Workers",]
ggplot(Sales_Men, aes(x=school, y=wage))+
  geom_jitter(aes(color=occupation, shape=ethn),size=2)+
  facet_grid(married~.)+
  labs(title="Sales Workers Years of school vs. wage, faceted by marital status",
     x="Years of School",
     y="Hourly Wage")
summary(Sales_Men)

###Plot 3 White Collar Workers Only, facet by married
White_Collar_Men <- Males[occupation=="Professional, Technical_and_kindred",]
ggplot(White_Collar_Men, aes(x=school, y=wage))+
  geom_jitter(aes(color=occupation, shape=ethn),size=2)+
  facet_grid(married~.)+
  labs(title="Professional & Technical Workers Years of school vs. wage, faceted by marital status",
     x="Years of School",
     y="Hourly Wage")
summary(White_Collar_Men)

###Plot 4 Service Workers Only faceted by marital status."
Service_Men <- Males[occupation=="Service_Workers",]
ggplot(Service_Men, aes(x=school, y=wage))+
  geom_jitter(aes(color=occupation, shape=ethn),size=2)+
  facet_grid(married~.)+
  labs(title="Service Workers Years of school vs. wage, faceted by marital status",
     x="Years of School",
     y="Hourly Wage")
summary(Service_Men)
