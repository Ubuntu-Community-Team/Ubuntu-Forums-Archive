---
title: "Ubutu freezes often."
date: 2010-11-14
forum: New to Ubuntu
---

### Post by elejele on 2010-11-14
Hey guys, I'm started encountering frequent freezes. The hard disk light keeps flashing and the system eventually becomes unresponsive leading me to. When this happens, I'm unable access xkill or reach top to try to terminate processes and end up rebooting (alt sysRq RSUB). Not that i'm using any weird programs just fairly common stuff like openoffice, and firefox and maybe a media player.

I read that you can look at the log file to figure things out, but I'm I don't really know what all that stuff means. Does anyone have anyone have any helpful suggestions on how I might go about diagnosing the problem? It would be much appreciated.

---

### Post by Hippytaff on 2010-11-15
Log files can be found here
```

cd /var/logs

```
```

ls

```
 
How much RAM do you have?
 
Also Wubi can get a bit dodgy after while. It is only intended to try Ubuntu, so if you plan on using ubuntu regularly it's usally advisable to do a 'real' partition.

---

### Post by kaldor on 2010-11-15
Shot in the dark... turn Compiz off completely if it is on.

My entire system locked up quite often when I used Compiz.

---

### Post by mastablasta on 2010-11-15
Not much informaiton here to work with... so i will direct you to this thread first:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
computer freezing could be a number of things. from failing motherboard, failing ram or poor PSU to software issues such as install bad drivers, bad install, bad upgrade or something like that.
 
so for starters have a look at those log files and also at the thread i posted and provide people here wiht more informaiton. the more informaiton you provide the faster and more accurate help you will get.

---

### Post by caeroe on 2010-11-15
> **mastablasta said:**
> Not much informaiton here to work with... so i will direct you to this thread first:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
computer freezing could be a number of things. from failing motherboard, failing ram or poor PSU to software issues such as install bad drivers, bad install, bad upgrade or something like that.
 
so for starters have a look at those log files and also at the thread i posted and provide people here wiht more informaiton. the more informaiton you provide the faster and more accurate help you will get.

Only started with 10.10 with me, and Win7 still works fine.  So that eliminates hardware.

---

### Post by elejele on 2010-11-15
>  Shot in the dark... turn Compiz off completely if it is on You know what, after I turning  compiz off, everything runs much more smoothly and nothing's frozen yet. Compiz is real nifty but the point of getting Ubuntu going was to have something lighter running on my system. 

I have 1Gb of ram, and 750Mb of swap which usually doesn't get used, so I didn't think space was an issue but I'm not really sure. I will do more research on what log files can do for me when I have more time on my hands. I probably have some hardware issues, at least according to windows.

Also, I have been noticing a windows-like slow down over time with Wubi, I was hoping to move to partition eventually considering I'm very pleased with ubuntu overall. Maybe then I'll be able to use compiz again.

Thanks for all the help guys, I must say I'm very pleased with how easy it is to get it with ubuntu.

---

