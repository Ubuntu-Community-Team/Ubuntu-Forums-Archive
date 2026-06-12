---
title: "Synaptic Has Broken"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by technotika on 2008-02-27
jerry@jerry-desktop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1154 package `xsane':
 value for `status' field not allowed in this context

HI GUYS  - major beef here.

I had compiz fusion running and noticed that there were 2 admin packages for it and
therefore settings werent being saved. 

I favoured the advanced desktop settings panel over the gnome desktop packages.
Since I tried to remove from synaptic , synapic stopped working, the error above seems to be the issue, What shall I do?

PLESE HELP

J-D

---

### Post by Sam Lars on 2008-02-27
Try renaming that file... maybe it will recreate one that works.  If it doesn't, you can rename it back.

---

### Post by technotika on 2008-02-27
Hi

Thanks for your advice I just found the fix before I saw ur post; i suspect its about getting that file "ignored" as you say.


sudo dpkg --clear-avail && sudo apt-get update

all working (sys updates, add remove & synaptic) after that 

orig thread

[http://ubuntuforums.org/showthread.php?t=389997&highlight=parse+error](http://ubuntuforums.org/showthread.php?t=389997&highlight=parse+error)

thx again!!!

---

