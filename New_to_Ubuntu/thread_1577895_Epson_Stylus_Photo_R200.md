---
title: "Epson Stylus Photo R200"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by irunwithscissors on 2010-09-19
I have a brand new installation of ubuntu 10.04.1... having just accomplished getting the Broadcom 4318 card working, on to tackle the next problem...   PRINTING!

ubuntu sees my printer, even identified it all on its own... but nothing prints.... can't even check ink levels or clean print heads, even though those options are available in the printer properties.

anyone have some light to shed on this problem? let me know what you need and i will do my best to get you the information... im relatively new to linux but learning faster than a snail can crawl in a teflon pan...

---

### Post by davidmohammed on 2010-09-19
suggest - download and install the epson driver from [here]("http://avasys.jp/eng/") - I've found that these work better than the generic drivers installed with lucid.

---

### Post by irunwithscissors on 2010-09-20
Thanks!

I will give these a shot this evening when I get home...

---

### Post by Mark Phelps on 2010-09-20
From what I could see, the only packages for the Epson R200 are rpm -- which do NOT work with Ubuntu.  You can try using alien to convert the .rpm to a .deb package -- but that only works some of the time.

The readme file says very little about how to build the driver from the source.  It says to run the rpm -- which, again, will NOT work in Ubuntu.

I have an R200 working under 10.04 and it works fine using the Gutenprint driver.  You could try installing Gutenprint and see if the offered drivers work for you.  That's a LOT less work than struggling with building a driver from source.

You will have to install mtink as well -- to monitor the ink levels in the printer.  The Gutenprint driver does not do that.

---

### Post by Wobblybob on 2010-09-20
Hi I have the same printer and did a fresh install of 10.04.1 and [updates] last week and after using the add printer option it picked up my printer with no problems. have you tried doing a test print from the printer properties box?

p.s Thanks for the tip on mtink Mark I've not come across that and I'll give that a go.

---

