---
title: "10 min 'till Ubuntu quits"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by takethatufiend on 2009-02-06
I'm having a problem and I can't wait until next week to get someone to look at it so I thought I would try here. Here goes:


When I turn on my computer everything boots fine and it seems normal. Yet, after about 10-20min, I lose everything. My wallpaper and toolbar icons are gone replaced with the missing graphic "x". If I click on one of these it tells me it can not open whatever I requested because the path does not exist. This happens every time I run my computer. I've had someone else run through a hard drive check/reformat but no problems came up. 


Insights?

---

### Post by Michael.Godawski on 2009-02-06
hi, 

have a look -  during the 10 minutes when you pc is running :) - at System > Administration > System Logs.

Any suspicious entries? What are your specs? Which version of Ubuntu do you use?

---

### Post by Voland on 2009-02-06
Check you partitions with ```
fsck -a
``` command

---

