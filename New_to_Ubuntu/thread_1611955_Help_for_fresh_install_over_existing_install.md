---
title: "Help for fresh install over existing install"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by phubert28 on 2010-11-02
I'm beginning to believe my upgrade from 10.4 to 10.10 had problems I will not be able to resolve without a fresh install.

I have Windows on my 320GB drive (only saving the data)
and Linux on my 160GB drive (ask DELL why I couldn't buy a 2nd 320 with my Optiplex 360!!)

In my haste, I made the mistake of allowing the install to do the partitioning when I installed 10.4, tho I had earlier created an ext4 partition when thinking of Linux...

Hey, tho an admin for years on a number of platforms, (mainframe, mini, Sun, Cisco, Windows servers and workstations) I'd retired and somehow seemed to forget EVERYTHING for a time!!!

GParted shows the following:

The 160 is partitioned as follows

/dev/sdb 149.01GB
Partition
/dev/sdb1 – ext4 – Mount point /media/-long string- Size: 81.04GiB Used: 1.45GB Unused: 79.59GiB
unallocated 3.80MiB
/dev/sdb2 – extended
…/dev/sdb5 – ext4 – Mount Point: / –               Size: 65.15GiB – Used 14.32 GiB Unused: 50.84GiB
…/dev/sdb6 – linux-swap –                          Size: 2.81GiB


My question:


Given what I have (above), could I create a mount point /home -now- and move my 'home' there BEFORE a new install????


I DO have a 12GB stick that might be able to hold everything under /home if it came to that.


Since this IS 'absolute beginner', can anyone guide me through doing 10.10 over (I'm on 64 bit as well)?


I know I'd have to download and burn the ISO.


Should I just put up with my problems and wait until 11.4???

---

### Post by bryanfblareunion on 2010-11-02
Ya, that's why i do clean installs whena  new version comes out. Try burning a new copy? and then install that..... that's what I'd do.

---

### Post by kwacka on 2010-11-02
You can find instructions for creating/moving to a new /home partition at: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/").

Hope this helps.

---

### Post by phubert28 on 2010-11-02
[kwacka]("http://ubuntuforums.org/member.php?u=111756"), Thanks for that reference!

---

