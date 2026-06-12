---
title: "Error with Hotmail Calendar &quot;XML Parsing Error&quot;"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by sokam on 2009-12-09
When I click on calendar in Hotmail using firefox 3.5.7, the following error occurred:

> XML Parsing Error: not well-formed
Location: [http://calendar.live.com/calendar/calendar.aspx?rru=legacy](http://calendar.live.com/calendar/calendar.aspx?rru=legacy)
Line Number 29, Column 88:    webWatsonTargetParamter : "http://watson.live.com/err.gif?rt=633959053175762609&mkt=en-US&pv=15.01.0170&pn=Live.Calendar&pd=&sc=0",
---------------------------------------------------------------------------------------^

Since I am using dual-boot, I tried in window with Firefox 3.0 and found no error.  So I suspect its my Firefox (and/or some other related extension needed for this) newer version that caused it.  When I upgraded to Karmic Koala, I followed this guide (except #9).  [http://blog.taragana.com/index.php/archive/10-things-you-must-do-after-installing-ubuntu-910/#more-16931](http://blog.taragana.com/index.php/archive/10-things-you-must-do-after-installing-ubuntu-910/#more-16931)

Question:
1) Anyone have the same issue?  
2) Do anyone know what is the cause for this XML error?
3) How do I roll back to the previous version of firefox in Ubuntu if that is the problem?

-----------------------------------------
Unbuntu 9.10 dual-boot with Window Vista
AMD Athlon 64x2
4GB DDR2

---

### Post by sokam on 2009-12-09
Am I the only one has this problem?

---

### Post by sokam on 2009-12-10
Since no one able to help, i completely uninstalled and installed firefox to find that I need to take out the repository related to 

deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

before it will let me install firefox 3.5.5

After that, my problem went away.

---

