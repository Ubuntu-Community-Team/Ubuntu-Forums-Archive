---
title: "is thier a set by step guid to partioning my hard drive"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by blake7 on 2009-05-08
yea i have a 160gb hard drive and would like to Partition 
1 to 2 GB of swap
20 GB of /root (but that depends on what you want to install in the end)
Rest is /home

can you help ps is that a good way to partition the hard drive

thank you

---

### Post by Titan8990 on 2009-05-08
No, that set up won't even give you a working system. Instead of /root you want /. /root should never contain very many files and in no way can justify its own partition.

---

### Post by aeiah on 2009-05-08
that seems fine. ive only got 12GB root. 20GB should be fine. linux software tends to be smaller than windows because they share libraries much more, and also any saved data and config files go in your home anyway.

id make sure if you want to hibernate your computer that your swap partition is at least the size of your ram. a lot of old guides will say you need swap space twice the size of your ram but this isnt really the case any more because everyone has so much ram. if you've got 1GB or more ram id say just go with 2GB (or equal to however much ram you have).

as for guides, i guess psychocats will have one but i shouldnt worry if you have an empty drive. whats the worst that could happen?

download and burn a copy of the gparted livecd and fire it up. its basically a stripped down version of linux and the only thing it has is gparted, a gui partition editor. you shouldnt have a problem creating your partitions. you can partition when installing ubuntu instead but i find it simpler to use a gparted livecd.

ps: make sure you're partitioning the right drive. it could be confusing if you have two 160GB hard drives in there. if this is the case i suggest unplugging the one with important data on first.

---

### Post by aeiah on 2009-05-08
ha, didnt even see the /root thing. yea. its /, not /root.

---

### Post by Varg_Gorgon on 2009-05-08
Hi, I asked the same basic question a few days ago here. I got it resolved here: [http://ubuntuforums.org/showthread.php?t=1150076](http://ubuntuforums.org/showthread.php?t=1150076) See if it works.

---

