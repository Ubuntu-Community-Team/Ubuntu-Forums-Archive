---
title: "Removing multiple installs"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by KROwen1959 on 2010-08-11
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x92d292d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24014   192891412    7  HPFS/NTFS
/dev/sda2           82560      121601   313604865    7  HPFS/NTFS
/dev/sda3           24014       82559   470262785    5  Extended
/dev/sda5           69811       82036    98191360   83  Linux
/dev/sda6           82036       82559     4206592   82  Linux swap / Solaris
/dev/sda7           39622       55317   126076724   83  Linux
/dev/sda8           68583       69810     9862144   82  Linux swap / Solaris
/dev/sda9           24014       38982   120227840   83  Linux
/dev/sda10          38982       39621     5134336   82  Linux swap / Solaris

Partition table entries are not in disk order

I have more than 1 of the same version at boot up and would love to take off all of the ones I don't need. I did some mistakes on my first install and reinstalled again thinking it would overwrite but it didn't. I have 1000 gig hard drive and I shrank it for Linux install. If I have to I can delete all Linux and start a fresh install. Thank you all for help. I have been to several threads to work out my issues and everybody is great

---

### Post by mike555 on 2010-08-11
You could use gparted , but it's tricky if you just delete the ones you don't want it might mess up grub , maybe better to just format them ext3 and leave the partitions for backup/media or whatever .

 if you want to reinstall you should read up on how ... [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)  (but don't do wubi) .... or just plan out what size you want and use gparted from the live disk to make the partition and a swap partition (usually 2 GB.  ).

---

