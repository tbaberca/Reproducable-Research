<<<<<<< HEAD
Activity Monitoring
================

GitHub Documents
----------------

This is an R Markdown format used for publishing markdown documents to GitHub. When you click the **Knit** button all R code chunks are run and a markdown file (.md) suitable for publishing to GitHub is generated.

Including Code
--------------

You can include R code in the document as follows:
--------------------------------------------------

total\_steps\_by\_date &lt;- aggregate(list(total\_steps = activity\(steps),  by=list(date = activity\)date), FUN=sum, na.rm=TRUE)

mean(total\_steps\_by\_date\(total_steps) median(total_steps_by_date\)total\_steps,na.rm=T)

What is the average daily activity pattern?
===========================================

average\_steps\_by\_time &lt;- aggregate(list(average\_steps = activity\(steps),  by=list(time = activity\)time, interval = activity\(interval),  FUN=mean,  na.rm=TRUE) average_steps_by_time[which.max(average_steps_by_time\)average\_steps),\]

Imputing missing values
=======================

sum(is.na(activity\[,"steps"\])) \# "join" the two data frames using merge() activity\_imputed &lt;- merge(activity,average\_steps\_by\_time,by="interval") \# correct the NA steps with average steps for the interval activity\_imputed &lt;- within(activity\_imputed, steps &lt;- ifelse(is.na(activity\_imputed\(steps),  activity_imputed\)average\_steps, activity\_imputed$steps))

total\_steps\_by\_date\_imputed &lt;- aggregate(list(total\_steps = activity\_imputed\(steps),  by=list(date = activity_imputed\)date), FUN=sum, na.rm=FALSE) \#Are there differences in activity patterns between weekdays and weekends? \# first add a character column for day of the week activity\_imputed\(weekday <- weekdays(activity_imputed\)date) \# now populate a new factor column using day of the week and a simple function activity\_imputed$weekend\_indicator &lt;- as.factor(apply(activity\_imputed\["weekday"\], 1, function(x) { switch(x, "Sunday" = "weekend", "Saturday" = "weekend", "weekday") })) \# confirm that we have the character and factor types we expect str(activity\_imputed) \#\# Including Plots

frequencies
===========

hist(total\_steps\_by\_date\(total_steps,  breaks=30,  xlab="Total Steps",  main="Total Steps Per Day",  col="lightblue") # desnsity plot(density(total_steps_by_date\)total\_steps, na.rm=TRUE), xlab="Total Steps", ylab="Density", main="Total Steps Per Day",
 col="purple", lwd=3) par(mfrow=c(1,1))

Daily activity pattern
======================

plot(average\_steps ~ time, data=average\_steps\_by\_time, xlab="Time interval", ylab="Mean steps", main="Mean Steps By Time Interval", type="l", col="blue", lwd=2) \#Imputed values par(mfrow=c(1,2)) \# frequencies hist(total\_steps\_by\_date\_imputed\(total_steps,  breaks=30,  xlab="Total Steps",  main="Total Steps Per Day",  col="lightblue") ##Imputed values par(mfrow=c(1,2)) # frequencies hist(total_steps_by_date_imputed\)total\_steps, breaks=30, xlab="Total Steps", main="Total Steps Per Day", col="lightblue") \# desnsity plot(density(total\_steps\_by\_date\_imputed$total\_steps, na.rm=TRUE), xlab="Total Steps", ylab="Density", main="Total Steps Per Day",
 col="purple", lwd=3) par(mfrow=c(1,1))

Now draw a panel plot using ggplot2, comparing activity patterns on weekdays and weekends.
------------------------------------------------------------------------------------------

average\_steps\_by\_time\_weekend &lt;- aggregate(list(average\_steps = activity\_imputed\(steps),  by=list(time = activity_imputed\)time.x, daytype = activity\_imputed$weekend\_indicator), FUN=mean) library(ggplot2) qplot(x = time, y = average\_steps, geom="path", data = average\_steps\_by\_time\_weekend, xlab="Time interval", ylab="Average steps", main="Activity Patternsvs. Weekends", facets = daytype ~ .)
=======
Activity Monitoring
================

activity &lt;- read.csv("activity.csv", header=TRUE) \#\#\# convert character date to POSIX date activity\(date <- as.POSIXct(strptime(activity\)date, "%Y-%m-%d"),tz="") \#\#\#\# first convert integer time to character and pad with leading zeros... activity\(time <- sprintf("%04d", activity\)interval) \#\#\#\# fill in leading zeros \#\#\#\# ...then convert to the date type activity\(time <- as.POSIXct(activity\)time, "%H%M",tz="") head(activity) str(activity)

GitHub Documents
----------------

This is an R Markdown format used for publishing markdown documents to GitHub. When you click the **Knit** button all R code chunks are run and a markdown file (.md) suitable for publishing to GitHub is generated.

### Including Code

total\_steps\_by\_date &lt;- aggregate(list(total\_steps = activity\(steps),  by=list(date = activity\)date), FUN=sum, na.rm=TRUE)

mean(total\_steps\_by\_date\(total_steps) median(total_steps_by_date\)total\_steps,na.rm=T)

### What is the average daily activity pattern?

average\_steps\_by\_time &lt;- aggregate(list(average\_steps = activity\(steps),  by=list(time = activity\)time, interval = activity$interval), FUN=mean, na.rm=TRUE)

average\_steps\_by\_time\[which.max(average\_steps\_by\_time$average\_steps),\]

#### Imputing missing values

sum(is.na(activity\[,"steps"\])) \# "join" the two data frames using merge() activity\_imputed &lt;- merge(activity,average\_steps\_by\_time,by="interval") \#\#\#\# correct the NA steps with average steps for the interval activity\_imputed &lt;- within(activity\_imputed, steps &lt;- ifelse(is.na(activity\_imputed\(steps),  activity_imputed\)average\_steps, activity\_imputed$steps))

total\_steps\_by\_date\_imputed &lt;- aggregate(list(total\_steps = activity\_imputed\(steps),  by=list(date = activity_imputed\)date), FUN=sum, na.rm=FALSE) \#\#\#Are there differences in activity patterns between weekdays and weekends?

#### first add a character column for day of the week

activity\_imputed\(weekday <- weekdays(activity_imputed\)date)

activity\_imputed$weekend\_indicator &lt;- as.factor(apply(activity\_imputed\["weekday"\], 1, function(x) { switch(x, "Sunday" = "weekend", "Saturday" = "weekend", "weekday") }))

#### confirm that we have the character and factor types we expect

str(activity\_imputed) \#\#\# Including Plots

#### frequencies

hist(total\_steps\_by\_date\(total_steps,  breaks=30,  xlab="Total Steps",  main="Total Steps Per Day",  col="lightblue") #### desnsity plot(density(total_steps_by_date\)total\_steps, na.rm=TRUE), xlab="Total Steps", ylab="Density", main="Total Steps Per Day",
 col="purple", lwd=3) par(mfrow=c(1,1))

### Daily activity pattern

plot(average\_steps ~ time, data=average\_steps\_by\_time, xlab="Time interval", ylab="Mean steps", main="Mean Steps By Time Interval", type="l", col="blue", lwd=2)

### Imputed values

par(mfrow=c(1,2))

#### frequencies

hist(total\_steps\_by\_date\_imputed$total\_steps, breaks=30, xlab="Total Steps", main="Total Steps Per Day", col="lightblue")

#### desnsity

plot(density(total\_steps\_by\_date\_imputed$total\_steps, na.rm=TRUE), xlab="Total Steps", ylab="Density", main="Total Steps Per Day",
 col="purple", lwd=3) par(mfrow=c(1,1))

#### Now draw a panel plot using ggplot2, comparing activity patterns on weekdays and weekends.

average\_steps\_by\_time\_weekend &lt;- aggregate(list(average\_steps = activity\_imputed\(steps),  by=list(time = activity_imputed\)time.x, daytype = activity\_imputed$weekend\_indicator), FUN=mean) library(ggplot2) qplot(x = time, y = average\_steps, geom="path", data = average\_steps\_by\_time\_weekend, xlab="Time interval", ylab="Average steps", main="Activity Patternsvs. Weekends", facets = daytype ~ .)
>>>>>>> origin/master
