---
title: "How to increase the size of ext3 partition"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by virgu on 2009-11-05
[SIZE=2]hi[/SIZE]
[SIZE=2]I am using ubuntu 9.04 and winXP SP2 in dual boot. I want to shift to ubuntu gradually but currently i've setup only 20Gb of my HDD for ext3 partition and the rest is NTFS for windows.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I want to allot more space to the ext3 partition. Can it be done without reinstalling ubuntu again? [/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]please help....[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2][/SIZE]

---

### Post by dvlchd3 on 2009-11-05
Boot into the Live CD, go to System -> Administrator -> Partition Editor

First decrease the size of the NTFS partition, then increase your ext3 partition.  Click Apply.  Reboot.  All Done :)

---

### Post by oldfred on 2009-11-05
You cannot resize while anything is mounted. You have to use gparted from the liveCD. I prefer to download the latest gparted livecd to edit partitions as it is usually more up-to-date.

You should backup everything that is important. While most changes will not cause problems we often see users who accidentally delete partitions or make other mistakes that are difficult to recover from. Backup is always safest even for those of us who think we know what we are doing.

If you are taking space from XP, houseclean and defrag at least twice. You should leave about 20% free space in windows or it may not be happy.

Rather than just increasing the ext3 partition, you may want to consider adding partitions for /home and/or a /data partition. If you want to share data between windows and Ubuntu a data partition that is NTFS formated is a possiblity.

---

### Post by Penguin Guy on 2009-11-05
Before making your Windows partition smaller, de-fragment it, if you don't you might loose some of your data. As mentioned in previous posts, the actual operation can be done using GParted which you can find on the live CD under [COLOR="Green"]System -> Administration -> Partition Editor[/COLOR].

---

### Post by virgu on 2009-11-06
[FONT=Comic Sans MS][SIZE=2]Sorry for being late to reply. 

Thanks to dvlchd3 , oldfred and penguinguy for help.Well, I've used Gparted to reformat another 20Gb in ext3 but don't know how to bring it under \Home.[/SIZE][/FONT]

> Rather than just increasing the ext3 partition, you may want to consider adding partitions for /home and/or a /data partition. If you want to share data between windows and Ubuntu a data partition that is NTFS formated is a possiblity.[FONT=Comic Sans MS][SIZE=2] 

For now I  have to mount the partition before using it.

Any idea how to bring the partition under \home ?

Thanks in advance.[/SIZE][/FONT]

---

### Post by tubunu on 2009-11-07
> Any idea how to bring the partition under \home ?

During the install process, select your home partition, e.g. /dev/hdb7 and mount it under /home.

---

### Post by oldfred on 2009-11-07
tubunu is correct if you are doing it as part of a new install. If you want to move home or just mount another data partition in home it is different:

Move home:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

To mount in home you would have to create a mount point 
mkdir ~/data
then mount that directory, but it depends on whether it is ext3, ext4 or ntfs:
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
then if you want to permanent mount it add a line to fstab:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

It is easiest to download and install this and it will create & mount  from a menu:
sudo apt-get install pysdm

---

### Post by virgu on 2009-11-09
Sorry guys I'm late to reply. tubuntu, i'm not installing afresh.but thanks for replying.

> Move home:
[https://help.ubuntu.com/community/Pa...ng/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")
[http://embraceubuntu.com/2006/01/29/...own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")Thanks oldfred, it worked really nice.:D I've moved my /home directory to the new partition. And it's working fine.

Thanks a lot mate.):P

---

