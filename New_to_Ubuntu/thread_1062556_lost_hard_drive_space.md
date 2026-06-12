---
title: "lost hard drive space"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by melave on 2009-02-07
Hi all

I have just installed ubuntu 8.10 doing a dual boot with vista 

It seems i have lost a bit of hard drive space I have a 160g hd, 35g is for vista but if i look on system monitor it tells me that dev/sda5 is 67.8g

i ran sudo fdisk -l
these are the results
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    73336724    36667338+   7  HPFS/NTFS
/dev/sda2       155650048   161941639     3145796    7  HPFS/NTFS
/dev/sda3       161951265   312576704    75312720    5  Extended
/dev/sda5       161951328   306343484    72196078+  83  Linux
/dev/sda6       306343548   312576704     3116578+  82  Linux swap / Solaris

I am very new to linux and really don't know what i am doing.
Have i lost space?
What is sda3?
and what should i do?

thanks in advance  :D

---

### Post by mpl34 on 2009-02-07
I suggest burning gparted to a disk and using it to find how your harddrive is being used. It will display where you vista and ubuntu partition is and where the free space is located

EDIT: sda3 is most likely where your free space is located and by using Gparted you will be able to extend your ubuntu partition to incorporate this free space.

---

### Post by mcduck on 2009-02-07
Hard to tell based on that output since part of it is missing (the beginning that tells size of the disk, and cylinder size).

What I can definitely tel you that sda3 has nothing to do with it, that's just extended partition that contains sda5 and sda6 (your Linux partitions,) and they take all the space available inside sda3.

Please run "df -h" and post the complete output here for a bit more understandable information about your disk usage..

---

### Post by melave on 2009-02-07
Hi all

Thanks for your help guys. Well i ran gparted and after a couple of goes i think she is all good. I have 75g on vista and 68 on linux

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc17da417

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         117        9688    76887090    7  HPFS/NTFS
/dev/sda2            9689       10081     3145796    7  HPFS/NTFS
/dev/sda3           10082       19457    75312720    5  Extended
/dev/sda5           10082       19069    72196078+  83  Linux
/dev/sda6           19070       19457     3116578+  82  Linux swap / Solaris


ran df -h

Filesystem            Size Used Avail Use% Mounted on
/dev/sda5              68G  2.5G   62G   4% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  108K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1010M   1% /dev
tmpfs                1012M  104K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile


Mcduck what is this telling me?

---

