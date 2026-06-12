---
title: "Dual boot Ubuntu and Windows problem"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by Jobbo256 on 2011-08-10
I am fairly new to dual booting and I am needing help with putting windows along side my ubuntu. I am currently using 10.04, and I have found no help with dual booting windows after installing ubuntu, it is always the other way around. Is there any way to make a pertition for windows in GParted? Like i said, i am new to dual booting. Help is greatly appreciated.




[IMG]http://img269.imageshack.us/img269/4567/screenshot1xx.png[/IMG]

---

### Post by Basher101 on 2011-08-10
Please make a screenshot of Gparted so i can give better advice. Its pretty easy to install it as long as you manage the partitions correctly.

---

### Post by Arijit_Kundu on 2011-08-10
windows does not like to show linux on its boot screen. so, its a bit problematic (but quite simple) to install windows after ubuntu. Every thing is explained [here]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by Mark Phelps on 2011-08-10
Some corrections are needed ...

Regarding Windows not liking to show Linux ... I think the Wubi-installed folks who regularly see both Ubuntu and Windows on their boot screen would disagree.

Regarding the instructions for dual-boot, please note that NeoSmart is NOT offering Win7 repair CD images anymore.  So, when you get into Win7,  you should consider using the Backup feature to create and burn your own Win7 Repair CD.  You will need that later if you ever have to repair Windows or their Boot Loader.

Regarding partitioning, after you have shrunk the Linux filesystem to make room for Win7, do NOT format the new space; instead, let the Win7 Installer format the space.  Win7 is picky about the details of its filesystem and Linux-formatted NTFS partitions can give it problems later on.

---

### Post by amjjawad on 2011-08-10
> **Jobbo256 said:**
> I am fairly new to dual booting and I am needing help with putting windows along side my ubuntu. I am currently using 10.04, and I have found no help with dual booting windows after installing ubuntu, it is always the other way around. Is there any way to make a pertition for windows in GParted? Like i said, i am new to dual booting. Help is greatly appreciated.




[IMG]http://img269.imageshack.us/img269/4567/screenshot1xx.png[/IMG]



Check the 2nd link in my signature.
[http://ubuntuforums.org/showthread.php?p=10257675](http://ubuntuforums.org/showthread.php?p=10257675)

---

