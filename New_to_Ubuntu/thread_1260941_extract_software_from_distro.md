---
title: "extract software from distro"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by ave2 on 2009-09-08
I have the ultimate gamers edition on dvd. It contains the ubuntu software, as well as a lot of pre installed programs and games, and I was wondering if there would be a way to extract some of that software, to install on my current version of ubuntu without having to actually install ubuntu ultimate edition

---

### Post by MelDJ on 2009-09-08
try add the cd to software sources and do sudo apt-get update

---

### Post by corncob on 2009-09-08
System > Administration > Software Sources.  Click on the Third-Party Software tab, then on the Add CD-ROM button at the bottom and follow instructions.  I don't remember if this updates your packages automatically but, if not, you can click on "Reload" in Synaptic and your packages should be there ready for installation.

---

### Post by ave2 on 2009-09-08
I tried both of these suggestions- just tells me the following:

Error scanning the CD

E:Unable to locate any package files, perhaps this is not a Debian Disc

---

### Post by corncob on 2009-09-08
Can you boot from the disk?  If so, can you select check disk for errors from the menu?  The disk or the drive might be damaged or dirty.  Do you have other ones?  And you're not trying to read a DVD in a CD drive?  Most DVD drives are ±RW these days but if you have an older one your disk might be the wrong medium for it.  Its just that I'm running out of things to say

---

