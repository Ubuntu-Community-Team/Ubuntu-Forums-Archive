---
title: "Installing new HDD"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by thgthg on 2009-09-03
**Hi everyone!**

I have installed a new disk and have started Gparted to create new partions for Ubuntu PC. I also have another disk installed. The problem is that I dont know how to create one new partion out of the thre now existing on the disk. You can se the partioning information from GParted in the attached image.

---

### Post by Sin@Sin-Sacrifice on 2009-09-03
First you´ll have to umount the disk you want to partition. Then notice the partition names (eg. sdb1, sdb2, sdb3) and figure out which partition you want to split. Then right click the partition you want to split and click resize. Define the size of your new partition and set it up by way of the editor. Anything you want to know about the use of in linux usually comes with a manual page. If you need further assistance try the command ```
man gparted
``` It will tell you just about everything you want to know about gnome partition editor.

---

### Post by thgthg on 2009-09-03
fdisk gives the following info

Disk /dev/sda: 40,0 GB, 40020664320 byte
255 huvuden, 63 sektorer/spår, 4865 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0xb48db48d

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        2518    20225803+   7  HPFS/NTFS
/dev/sda2            2519        4761    18016897+  83  Linux
/dev/sda3            4762        4865      835380    5  Utökad
/dev/sda5            4762        4865      835348+  82  Linux växling / Solaris

Disk /dev/sdb: 40,0 GB, 40020664320 byte
255 huvuden, 63 sektorer/spår, 4865 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x000d661e

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1   *           1        1020     8193118+   b  W95 FAT32
/dev/sdb2            1021        2040     8193150    f  W95 Utökad (LBA

---

### Post by thgthg on 2009-09-03
Sorry, but there is no manual for Gparted.
The only thing I have done so far is to connect the disk, does it mount automatically??

---

### Post by thgthg on 2009-09-03
Sorry, but there is no manual for Gparted.
The only thing I have done so far is to connect the disk, does it mount automatically??

---

### Post by LewRockwell on 2009-09-03
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

.

---

### Post by thgthg on 2009-09-03
Tnx for the help!
I hope I find the answers I need

---

