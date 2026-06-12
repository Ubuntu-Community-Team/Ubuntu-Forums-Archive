---
title: "Broadcomm Installation issue"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by daveritah on 2010-03-06
I am attempting to activate my wireless on my ubuntu 9.10. I have a Dell Wireless 1490 with a Dual Band WLAN Mini-Card with BCM4312/BCM 2050 chipset. I have the b43-fwcutter installed, when I attempted to install the "bcmwl-kernel-source_5.10.91.9+bdcom-oubuntu 4_I386.deb" file, I recieved the following error message "Error dependency is not satisfiable:dkms". I am new to Linux and Ubuntu, so what does this mean? How do I resolve this? And is there anything else I need to do, to activate my wireless. Please note, the only internet I presently have, is on my XP side (I have a dual boot).

---

### Post by ptn107 on 2010-03-06
```
sudo aptitude install dkms
```

---

### Post by admiralspark on 2010-03-06
Hello! Use [this]("http://ubuntuforums.org/showthread.php?t=766560") link to solve your issues. If you have any questions, pm me, I have scripts put together that can do it for you, almost animated. :p

PS That uses an alternative to the b43-fwcutter, called Ndiswrapper. I use it on my 4318, it works perfectly.

---

### Post by daveritah on 2010-03-07
I applied the dkms procedure "No Sucess". I went to the link suggested,  the link spoke about Hardy, will this work for Karmic, or do changes need to be made in coding to make it work?
Thanks for the input - Dave

---

### Post by crf on 2010-03-08
There is another thread too
[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

---

### Post by daveritah on 2010-03-12
Problem Solved:
I resolved this issue by blacklisting the current B43 drivers, installed ndiswrapper according the instructions found in a Ubuntu Thread and several other ndiswrapper sources. Thanks everyone for your help in this issue, it is nice to have such a rich resource of information available when you have a problem. - Dave

---

### Post by achase79 on 2010-03-12
you can also use [keryx]("http://keryxproject.org") to download packages and their dependencies on your windows (or any other os) computer and bring them to your ubuntu computer.

---

