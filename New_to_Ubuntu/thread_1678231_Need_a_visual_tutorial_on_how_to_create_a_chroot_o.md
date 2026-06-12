---
title: "Need a visual tutorial on how to create a chroot of ubuntu 32 10.10"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by PacmanStopper on 2011-01-30
I have ubuntu 10.10 64 how do I create ubuntu 32 bit 10.10 chroot or is it possible to have 2 ubuntus on one computer. I tried to install 2 ubuntus but only the newest one had the username displayed. Is there a picture guide for this.

---

### Post by PacmanStopper on 2011-01-30
Also need a visual guide which has a picture with every step.

---

### Post by oldfred on 2011-01-30
You should only need to do chroot to repair one install from another or from a liveCD. Is that what you want?

These do not have pictures as you just copy in command lines.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)
kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

With pictures on installs, just repeat for second install:
Some examples of installs and issues:
Issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

with two installs you do need to plan partitions:
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

