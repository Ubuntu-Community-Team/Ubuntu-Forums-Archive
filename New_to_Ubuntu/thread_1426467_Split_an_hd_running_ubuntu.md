---
title: "Split an hd running ubuntu"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by siretfel on 2010-03-10
Hi all,
I am running ubuntu and i have an 80 GB hd. I want to split this hd and a part of it make it ntfs or fat32. 
What is the process to do that without losing my data?
Currently I use 3,3 gb for swap, 3,3 extended and 77gb is linuxt ext4.
I would appreciate any help on this.
Thanks to all:D

---

### Post by undecim on 2010-03-10
You will need to use GParted from an Ubuntu livecd (System -> Administration -> GParted in the livecd). 

GParted is very user-friendly, but post back here if you need help with anything specific.

Make sure you take a backup of anything important though. If something goes wrong during partitioning (power outages, hardware hiccups, etc), it can result in loss of data.

EDIT: also, in the unlikely even that GParted gives you an error when partitioning, make sure you save the report somewhere (not on the livecd and not on the possibly broken HDD; A thumb drive would be ideal), because with the information from that report, there is little anyone could do to help you.

---

### Post by siretfel on 2010-03-10
I would like to thank you for your help.I will get right on it.
Many many thanks! :D:D:D

---

### Post by elliotn on 2010-03-10
Yep gparted is the best.

---

