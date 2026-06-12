---
title: "no partion shown at step of install"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by ovej001 on 2010-09-28
This my first attempt at installing Ubuntu. I am trying to install Ubuntu 10.4 on a Dell Inspiron 1721 with a seagate 320 gb harddrive. I already have Vista installed on the  drive when i get to step 4 of the installation there are no partitions shown,the box under the device,type etc. is blank. When I install a different hard drive a samsung 250 also with vista the partitions are shown. I wish to use the 320 Gb hard drive as my primary and the 250 as a secondary as test have shown a number of bad sectors on the 250.

---

### Post by jtarin on 2010-09-28
What are the differnces in the two drives other than size? SATA, PATA,ATA? Are you conncting them one at a time or running Primary, Secondary drives? Have you tried to run Ubuntu in the try but not install mode? You can use GPARTED in that mode from the desktop of GNOME. It can be found in the menu.

---

### Post by srs5694 on 2010-09-28
I can't be positive, but it could be you've got the problem described [on this Web page of mine.](http://www.rodsbooks.com/missing-parts/index.html) To be sure, start the Ubuntu installer in live CD mode, open a text-mode shell (terminal) window, and type "sudo fdisk -lu". Post the output here, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

---

### Post by Mark Phelps on 2010-09-29
BE careful... If you want to install on the drive that already contains Vista, do NOT use the Ubuntu installer to shrink the Vista partition.  Doing so runs the risk of corrupting that partition and rendering Vista unbootable.  Instead, use the Vista Disk Management utility to shrink it, leaving room for Ubuntu.

Also, if you already have the Dell-typical 4-partition installation, you've got a LOT of work ahead of you because that's the maximum number of primary partitions you can have.  You'll have to remove one before you can create a partition for Ubuntu.

---

