---
title: "how to ntfs in ubuntu 10.10"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by magedsoft on 2010-11-27
how make ntfs in ubuntu 10.10 side to 
root ,home ,swap 
and what's the suitable size for root and home and swap in my computer 


MOTHERBORAD GIGABYTE G41 COMBO
RAM 4 GIGA(2*2GIGA)
CPU DUALCORE 2.7/2M
HARDDIAK 1000GB
DVDSONY
SCREEN LCD PENQ 19


HOW MAKE SPECIAL SPACE FOR APT FOLDER 
THANK YOU

---

### Post by coffeecat on 2010-11-27
NTFS is a Microsoft filesystem which does not support Linux/Unix permissions. If what you are asking is how to create NTFS partitions for Linux root, home and swap partitions, you cannot use NTFS for such partitions.

The only use for NTFS when using Linux is for a shared data partition if you have Windows on the same machine, or for external USB drives. But only use NTFS if you have Windows available for filesystem repair; the Linux tools do not replace Windows' chkdsk.

---

### Post by Hippytaff on 2010-11-27
+1 coffecat and also  just to mention that the file format you need for these partitions is ext4 :-)

also swap is usually 2xRAM unless you've got 2BG RAM etc, in which case make it the same size so you can hibernate :-)

---

