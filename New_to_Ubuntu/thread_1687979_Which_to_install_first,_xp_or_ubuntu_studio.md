---
title: "Which to install first, xp or ubuntu studio"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by alive063 on 2011-02-14
Hi, At the moment I have ubuntu 10,10 on one partition and windows 7 on the other. 
Ideally I want ubuntustudio on one and xp on the other (cant stop win 7 from freezing up and xp runs audio programs well!)
I am ok to do a complete wipe and fresh install but I'm not sure of the order- xp first on full disk then ubuntustudio with partition wizard or ubuntustudio first?
are there any drawbacks to putting xp inside a virtual machine- does it work as well?
Any help would be much appreciated. 

Dell latitude e6400 duo core 8GB ram 120GB solid state hdd

---

### Post by robsoles on 2011-02-14
XP is great in [www.virtualbox.org](www.virtualbox.org) but it does have limits - trickier getting  higher end graphical games to run but not impossible for most.

If you install side by side then install XP to 'about half' (<- your personal preference needs to be applied) the capacity of the drive first and then install Ubuntu Studio second - I advise this because at least the Ubuntu installer will try to leave you with a selectable (and bootable) XP but the XP installer *isn't that smart*...

Rather than installing to an entire disk and then shrinking just kill-all the partitions that are there (using the XP installer) and then make a partition of half the available space and tell the installer to put Windows there - The Ubuntu installer should give you the option of 'side by side' as one of the 'automated' partitioning methods it can use for you.

---

### Post by alive063 on 2011-02-15
Thanks robsoles, I will install side by side like you say for now while I am learning Linux.

---

### Post by oldfred on 2011-02-15
I do not know about studio but the standard Ubuntu does not have a install side by side any more. Manual partitioning & manual install is always the safest way.

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by Rubi1200 on 2011-02-15
+1 to the advice given by oldfred.

Herman's site is the best place to go for dual-boot instructions:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

---

