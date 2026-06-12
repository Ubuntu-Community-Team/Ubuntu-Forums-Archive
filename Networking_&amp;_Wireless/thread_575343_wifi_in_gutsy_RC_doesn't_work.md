---
title: "wifi in gutsy RC doesn't work"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by master5o1 on 2007-10-13
I have a pci wireless card from Dick Smith Electronics in NZ, and it used to work in Feisty, but now doesn't in Gutsy RC.

this link: [http://www.dse.co.nz/...XH8343]("http://www.dse.co.nz/cgi-bin/dse.storefront/471189ea006aac0a273fc0a87f3306d6/Export/catalogs/SUPXH8343")

has some info on the card.


I have Ndiswrapper installed but the card isn't receiving any reception. Can apparently see my network ESSID though (with 0% next to it).


Currently I just have it wired up close to my brother's computer, but this isn't what I want to have to do every day.

---

### Post by kevdog on 2007-10-13
If you upgraded from feisty to gutsy, there was a new kernel installed -- hence the old ndiswrapper kernel module needs to be reinstalled or recompiled against the gutsy headers and then reinstalled.

---

### Post by Riccisayer@tiscali.fr on 2008-01-27
Err OK Kevdog. So what does that mean exactly.  Perhaps step by step?

---

### Post by kevdog on 2008-01-27
Your not using the gusty rc correct??

rc - release candidate.  This post is old.  Gutsy's been released now so their is no rc per se.

Basically download and install ndiswrapper, that is all I am saying.  I wrote a guide how to do this, however there are others that are quite good also.

Here is my guide:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

