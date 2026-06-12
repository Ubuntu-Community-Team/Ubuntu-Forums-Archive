---
title: "Dual Booting Allocate Drive Space issues"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by lorantjakab on 2010-12-21
Im at the allocate drive space window in ubi, and i have partitioned windows. i have a 160 gig hard drive, partitioned 80 gigs for windows and the rest for ubuntu. now where i select the partition i am lost even though i followed other people on the dual booting but that is for 10.4 and its older. what do i do here at this window, what do i partition, and even i partition the free space of 80 gig it says no root file system is defined, please correct this from the partitioning menu. 
 
I am on a dying laptop trying super hard to fix the real thing. Any replies are helpful. thanks guys.
 
I have 
/dev/sda
/dev/sda1/ntfs
/dev/sda2/ext2
what is missing?

---

### Post by halj32 on 2010-12-21
the easiest way to do it is boot from your windows disk & when your in the installer give windows a partition of 80 gig & install.
When it's finished install Ubuntu, when installing manually set up the partition, if you want to use hibernate you will need a swap partition larger than your ram if not it's up to you I dont use swap partitions.
then you'll need the install partition ( / ) to which you can install everything including your home or you can make a home partition ( /home ) once youve decided what you want click on the apply also it's best to use ext3 or 4
so the minimum youll need is 2 partitions
one ntfs for windows &
one ext3 or 4 for Linux
if you want you can have a swap & a home as well so max you'll have 4 partitions
/sda1/ntfs
/sda2/swap
/sda3/ext3 or 4
/sda4/home
size is up to you swap is usually 1.5-2 time ram & give your install partition plenty of room for updates & programs 

hope this helps

---

