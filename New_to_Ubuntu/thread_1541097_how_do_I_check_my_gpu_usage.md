---
title: "how do I check my gpu usage"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2010-07-28
how do I check my gpu usage like I do my cpu and memory in system manager?

---

### Post by MrWES on 2010-07-28
From the terminal you can type top, or install htop.

sudo apt-get install htop

bill

---

### Post by LunaticHiatus on 2010-07-28
anything prettier then htop?

---

### Post by clhsharky on 2010-07-28
LunaticHiatus

Most Linux apps are written by geeks for geeks for free.
Anyone interested in writing prettier apps is welcome to do so.
Asking is a good start, who wants to contribute to open source?

Sharky

If you search you'll find some, I myself don't use them so cant recommend any.

---

### Post by MestreLion on 2013-03-02
> **MrWES said:**
> From the terminal you can type top, or install htop.

sudo apt-get install htop

bill

htop does not measure GPU load, only CPU. And for that he already has Gnome's nice System Monitor, along with dozns of other options.

For GPU, it depends on your card (ATI/AMD, NVidia, Intel) and driver (open source or proprietary). Since I use an AMD HD 7770 with its proprietary fglrx driver, I can only answer for that:

For usage % (along with clock speeds):
```
aticonfig --odgc
```

For temperature:
```
aticonfig --odgt
```

For fan speed:
```
aticonfig --pplib-cmd "get fanspeed 0"
```

And you can view them all in a single command:
```
aticonfig --odgc --odgt --pplib-cmd "get fanspeed 0"
```

> **LunaticHiatus said:**
> anything prettier then htop?

Since any ap would depend on proprietary and closed-source drivers, there are not many options out there. But I've found these 2:

AMDOverdriveCtrl
A complete Load/Temp/Fan control panel. I've never used, but looks awesome!
[http://sourceforge.net/projects/amdovdrvctrl/](http://sourceforge.net/projects/amdovdrvctrl/)

pSensor
Can be compiled with AMD GPU support. I use it myself, works great. But currently only Temperature and Fan speed, no GPU load
[http://wpitchoune.net/blog/psensor/](http://wpitchoune.net/blog/psensor/)

Hope this helps!

---

### Post by QIII on 2013-03-02
Thank you for sharing.  Everyone’s questions and answers are valuable.

If a thread has had no activity for about a year or more, it is best to start a new thread of your own. Not only will you be more likely to get a response, but things change so quickly in the software world that an old thread may cause you more trouble than it will help due to outdated information.

Please feel free to add a link to the original thread in your new one if you think it might be helpful.

Best wishes!

***Thread closed.***

---

