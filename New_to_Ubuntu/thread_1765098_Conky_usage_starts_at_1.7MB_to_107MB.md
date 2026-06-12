---
title: "Conky usage starts at 1.7MB to 107MB"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by lifelike27 on 2011-05-22
When I first open conky it takes up only 1.7MB. I left my computer running the whole night and when I got back it showed that it conky was using 100+MB.

A link in case it doesn't seem believable: [http://ubuntuone.com/p/uvU/](http://ubuntuone.com/p/uvU/)

---

### Post by Gone fishing on 2011-05-22
Thats odd, there's a thread on .conkrc files maybe you should take a look [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

---

### Post by lifelike27 on 2011-05-24
The thread contains posts of different people's conkyrc files. How is it supposed to help?

---

### Post by Grenage on 2011-05-24
Probably in allowing you to compare configurations and possible causes.  It could be a conky bug, a conky dependency bug, or a config bug.  The config is the easiest place to start.

Does it happen with an alternative config?

---

### Post by Frogs Hair on 2011-05-24
Check all the read me files included with your configuration , they sometimes contain warnings or special instructions in regards to hardware.

I found one yesterday that will cause a segmentation fault if the conkyrc is not amended prior to use on certain hardware.

---

### Post by lifelike27 on 2011-06-14
There's nothing wrong with the conkyrc file since it happens with all conkyrc files. I've also noticed memory leaks (if it is one) in nm-applet as well. If I leave my PC running overnight nm-applet goes from 50MB to 500MB as well. Might this be a bug in 11.04?

---

### Post by Frogs Hair on 2011-06-14
You could try another Conky theme just as a test to see if that particular .conkyrc is the source of the problem.

---

### Post by lifelike27 on 2011-06-15
I have tried another theme, but if you insist I'll let another one sit for the night.

Will update tomorrow morning.

---

### Post by linux.alucard on 2011-06-20
I have also same problem :(

Conky config: 

[http://gnome-look.org/content/show.php/conky_orange?content=137503&PHPSESSID=10e2bedd140347bde439af5fc42f95bc](http://gnome-look.org/content/show.php/conky_orange?content=137503&PHPSESSID=10e2bedd140347bde439af5fc42f95bc)

Memory usage: ~150 MB

sorry my english is poor

---

### Post by lifelike27 on 2011-06-22
> **linux.alucard said:**
> I have also same problem :(

Conky config: 

[http://gnome-look.org/content/show.php/conky_orange?content=137503&PHPSESSID=10e2bedd140347bde439af5fc42f95bc](http://gnome-look.org/content/show.php/conky_orange?content=137503&PHPSESSID=10e2bedd140347bde439af5fc42f95bc)

Memory usage: ~150 MB

sorry my english is poor

I've used that conky config file and had the same problem as well.

I still haven't tested out conky in a while so I haven't been able to post any info about it.

---

### Post by linux.alucard on 2011-06-22
;-)

Changelog:
[B]21-06-2011
- fix bug memory leak[/B]

thanks, hardball

[http://gnome-look.org/content/show.php/conky_orange?content=137503](http://gnome-look.org/content/show.php/conky_orange?content=137503)

---

