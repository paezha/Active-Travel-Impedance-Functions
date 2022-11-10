---
output:
  pdf_document: default
  html_document: default
---

# creating an integrated data frame from 1992 to 2015


```{r}
trip_w_f <- rbind(walking_2015,walking_2010, walking_2005, walking_1998 ,walking_1992,  walking_1986) 
trip_c_f <- rbind(cycling_2015,cycling_2010, cycling_2005, cycling_1998 ,cycling_1992)
trip_f <-  rbind(walking_2015,walking_2010, walking_2005, walking_1998 ,walking_1992,  walking_1986, cycling_2015,cycling_2010, cycling_2005, cycling_1998 ,cycling_1992)
```

```{r}
ggplot(data = trip_w_f, aes(x = DURATION, y = f)) + 
geom_line(linetype = "solid") +
  facet_grid(. ~ YEAR) +
  scale_x_continuous("Time in minutes") +
  scale_y_continuous("Cumulative Percentage of Trips") +
  labs(title = "Impedance function for walking trip from 1986 - 2015")
```
```{r}
summary(trip_c_f)
print(summary)
```


```{r}
ggplot(data = trip_c_f, aes(x = DURATION, y = f)) + 
geom_line(linetype = "solid", na.rm=TRUE) +
  facet_grid(. ~ YEAR) +
  scale_x_continuous("Time in minutes") +
  scale_y_continuous("Cumulative Percentage of Trips")
```

```{r}
ggplot(data = cycling_2005, aes(x = DURATION, y = f)) + 
geom_line(linetype = "solid") +
  scale_x_continuous("Time in minutes") +
  scale_y_continuous("Cumulative Percentage of Trips")
```
```{r}
ggplot(data = cycling_1992, aes(x = DURATION, y = f)) + 
geom_line(linetype = "solid") +
  scale_x_continuous("Time in minutes") +
  scale_y_continuous("Cumulative Percentage of Trips")
```




```{r}
ggplot(data = cycling_1998, aes(x = DURATION, y = f)) + 
geom_line(linetype = "solid") +
  scale_x_continuous("Time in minutes") +
  scale_y_continuous("Cumulative Percentage of Trips")
```





** Impedance function for different destination **

```{r}
 
ggplot(data = walking_2015, aes(x = DURATION, y = f)) + 
geom_line() +
facet_wrap(facets = vars(dest_label)) 
```

```{r}
 
ggplot(data = walking_2010, aes(x = DURATION, y = f)) + 
geom_line() +
facet_wrap(facets = vars(dest_label)) 
```
```{r}
filter(trip_f, YEAR == 2015)
ggplot(data = trip_f, aes(x = DURATION, y = f, color = MODE)) + 
geom_line() +
facet_wrap(facets = vars(dest_label))
```


```{r}
ggplot(data = trip_f, aes(x = DURATION, y = f, color = MODE)) + 
geom_line() +
facet_wrap(dest_label ~ YEAR)
```
