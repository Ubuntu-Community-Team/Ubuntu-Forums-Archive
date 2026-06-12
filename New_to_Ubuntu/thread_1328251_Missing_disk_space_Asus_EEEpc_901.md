---
title: "Missing disk space Asus EEEpc 901"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by kux on 2009-11-16
I have been using EEEbuntu (with Jaunty 9.04) installed on my 16GB SDD for a couple of months. Upon checking the Disk Usage Analyzer utility I now realise that Ubuntu only allows me to access 8GB of my SDD!

I installed Ubuntu as a dual boot with XP (which came with my machine). As far as I can tell XP is installed on my 4GB SDD and Ubuntu on the 16GB. Seeing as how I have very limited space to start with - how can I reclaim the other half of my 16GB?

I'm running:
EeePC 901
EEEbuntu (with Ubuntu 9.04)
Bios 2.6.30-02063004-generic
Intel(R) Atom(TM) CPU N270   @ 1.60GHz

Also, this is preventing me from upgrading to Ubuntu 9.10 - Does anyone know: If I was able to upgrade, would that affect the processes configured on EEEbuntu? Thanks!

---

### Post by mikechant on 2009-11-16
I guess it's to do with how your partitions are set up.
If you could run the following in a terminal (ALT-F2 to get a terminal)
```
fdisk -l
```
and post the output here that might help

(note the fdisk option is a lower case letter L, not a number one).

---

### Post by dca on 2009-11-16
sudo fdisk -l
 
(or)
 
sudo sfdisk -l

---

### Post by kux on 2009-11-16
Disk /dev/sda: 490 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/128/63 (instead of 490/255/63).
For this listing I'll assume that geometry.
Units = cylinders of 4128768 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+    967     968-   3902944+   7  HPFS/NTFS
/dev/sda2        968     975       8      32256   ef  EFI (FAT-12/16/32)
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty

Disk /dev/sdb: 981 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+    932     933-   7494291   83  Linux
/dev/sdb2        933     980      48     385560    5  Extended
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
/dev/sdb5        933+    980      48-    385528+  82  Linux swap / Solaris

---

### Post by blazemore on 2009-11-22
Hey, thanks for opening a thread (nb, he originally PM'd me)

Well it seems you have Linux on /dev/sdb1 and then the rest is empty. The best thing to do would be to boot from a Live USB and open the Partition Editor.

From here (making sure you select the right disk in the top-right corner) you can move, resize and delete partitions.

---

### Post by kux on 2009-11-22
Can I resize partitions without messing up my settings or deleting files accidentally?

---

### Post by snowpine on 2009-11-24
I would recommend a fresh install of Ubuntu 9.10 (assuming you have thoroughly tested it as a Live CD/USB first). You can use it as an opportunity to partition your drives correctly.

eeebuntu is **not** Ubuntu and trying to upgrade eeebuntu 9.04 to Ubuntu 9.10 [probably won't work]("http://forum.eeebuntu.org/viewtopic.php?f=25&t=4560").

> **kux said:**
> Can I resize partitions without messing up my settings or deleting files accidentally?

You should always back up your data to an external drive before messing with your partitions.

---

