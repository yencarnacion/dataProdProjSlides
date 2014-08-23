---
title       : Twitter-When
subtitle    : 
author      : yencarnacion
job         : Coursera Developing Data Products Project
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---
<!-- Limit image width and height -->
<style type='text/css'>
img {
    max-height: 560px;
    max-width: 964px;
}
</style>

<!-- Center image on slide -->
<script src="http://ajax.aspnetcdn.com/ajax/jQuery/jquery-1.7.min.js"></script>
<script type='text/javascript'>
$(function() {
    $("p:has(img)").addClass('centered');
});
</script>

## Why Twitter-When

1. Twitter-When is useful for knowing when Twitter users that have tweeted about a particular topic are most active and, therefore, likely to see other tweets on the subject.

## Where to Find Twitter-When

1.  Currently hosted at http://yencarnacion.shinyapps.io/mine/
2.  The Github repo is located at https://github.com/yencarnacion/dataProdProj

---

## An Image is Worth a Thousand Words


<img style = 'text-align: center' src = "assets/img/screenShot.png" height="240" width="677" />

---

## How does it work

1. Enter a word or phrase to be searched on Twitter.
2. Adjust the number of Tweets to be retrieved using the slider. The minimum is 25 and the maximum is 100.
3. Click the "Twitter, when was that tweeted?" button.
4. Twitter-When uses the TwitteR R package to connect to Twitter
5. It searches for a tweeted term
6. It converts the results from the search result "created" variable to a vector with numbers 1 to 24 where each number represents a time intervarl in UTC.  The end result of the vector is like the interval vector shown in the R code in the next slide.
7. Obtain your results. It plots the calculated time interval vector using a histogram plot.  The histogram shows how many tweets there were per hour interval where each hour interval corresponds to a time using a range from 1 to 24 in UTC (Coordinated Universal Time)

---

## R Magic behind the scenes


```r
interval<-c(1, 1, 1, 1, 13, 13, 24, 24, 24, 24, 24, 24, 24)
hist(interval, breaks=c(1:24), xaxt="n", 
        main = "Histogram of Tweets per hour", 
        xlab= "Hour (1 being 12:00 AM UTC, 24 being 11:00 PM UTC)")
    axis(1, at=seq(1,24, by=2), labels=seq(1,24, by=2))
```

<img src="assets/fig/unnamed-chunk-1.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" style="display: block; margin: auto;" />



