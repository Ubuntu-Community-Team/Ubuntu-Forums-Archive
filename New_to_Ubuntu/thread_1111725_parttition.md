---
title: "parttition"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by acid-rain on 2009-03-30
Hi, i'm new to ubuntu linux so pls be patient if i ask some stuped questions.
I used to run win 98 and win XP. What strike me ode is i cant get explained how to manualy partition my larger HD. 
I used to partition under windows:
C: OP= 25G, 
D: documents 10G, 
E: MUSIK % Photo 30G and 
F: MOVIE the rest of the HD.
I want to partition my HD under ubuntu a similar way, HOW DO I DO THAT?
Every answer i get is YOU DONT NEED TO or its explanet regarding dual boot win & ubuntu.
I dont want win on my HD anymore but i also dont want one large partition with all and a litle swap space. 
Is there nobody who can explain to me step by step how to do this.
After all whats the use of having dual boot if you dont want windows.
For a real answer i'm very thankfull. best regards to all.  [EMAIL="reinierreimer@yahoo.co.uk"]reinierreimer@yahoo.co.uk[/EMAIL]
:lolflag:

---

### Post by cariboo on 2009-03-31
You can partition your hard drive during installation. Once you get to the partitioning part of the installation, choose manual partition ans set things up the way you want to. The partitioner will allow you to create fat32, ntfs, ext2 ext3 reiser and xfs partitions.

Linux uses ext2/ext3 partions by default. I wouldn't suggest using reiserfs as ther has been no development sin Hans Reiser went to jail.

Jim

---

### Post by indytim on 2009-03-31
1.  Get a copy of GParted Live and burn the iso to a bootable CD [http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php").
2.  Boot to the GParted Live CD. Adjust your partitions as needed.  Don't forget that if you do something with live data CDs you will probably loose your data.
3.  At the install, when it comes time to make a decision on the partition method, choose "manual" and configure your partitions as you want/need.

Cautionary Note : Make absolutely sure you really want to delete Windows before proceeding.  As in, have you verified that ALL of the apps that you need, use, on a regular basis etc. are equivalent available in Linux.  If not, hold onto Windows until you reach this point of certainty.

IndyTim

---

