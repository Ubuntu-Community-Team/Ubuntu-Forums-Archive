---
title: "GParted Partion Question"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by ericstrom on 2010-08-08
Help, I messed up !  Long story...trying to set up several partitons and two hard disk drives and now I'm not sure what I have. I just want to start fresh. Clean of the hard disks and reload ubuntu. Wondering what command in GParted do I use to clean off a partition ? 

Current set up is a 40 GB drive that is dual boot:Win XP on sda1 (about 25GB) and Lucid on  sda2 (about 13 GB). Then I have another 40 GB drive that is sdb which is configured as NTFS and is data only. Somehow the data on sdb got intertwined with sda2 and has filled sda2 up. Also when I boot up I notice that the 25GB from sda1 and sdb both mount automatically. I tried cleaning off most of the data on sdb. I also tried unmounting sda1 and sdb but got the following message:
 
Unable to unmout Data (data is the drive name for sdb) Error mounting : unmount exited with exit code 1: helper failed with:
Unmount: only root can unmount/sdb1 from/media/Data.

So at this point I think the best course is to just start over. Wipe sda2 and sdb clean and reload a fresh copy of Ubuntu. I want to keep sda1 (Win XP) intact though. Can you tell me the command in GParted to wipe these partitons clean. I'm not worried about the data as I have it backed up.

Thanks...sorry for the long explanation.

---

### Post by uRock on 2010-08-08
Using the liveCD, go in the menu to System> Administration> Gparted, you can then unmount the swap and delete any partitions that you want to rebuild.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Sef on 2010-08-08
Another option would be to download [GParted]("http://gparted.sourceforge.net/index.php") itself.

---

