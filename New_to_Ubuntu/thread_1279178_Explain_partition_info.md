---
title: "Explain partition info"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by upstatelabs on 2009-09-30
I have set up a server with Ubuntu 9.04 (headless)  and have found my raid1(hardware) disk partition information like this:

daves@newton:~$ sudo parted /dev/sda print
Model: HPT DISK 8_0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      32.3kB  500GB  500GB  primary                boot, lvm
 2      500GB   500GB  255MB  extended
 5      500GB   500GB  255MB  logical   ext2

Can someone explain how the primary and extended partitions (1 & 2) seem to occupy the same space?  And how it was done?  And what does the 'lvm' flag imply?

Many thanks!

---

### Post by credobyte on 2009-09-30
```
HDD - Partition #1
-----------------
      |
      ---------------------- Partition #1/A
      |
      ---------------------- Partition #1/B
```All you have there is LVM ( logical volume manager ), which contains 2 partitions - 2 x 255Gb.

---

### Post by upstatelabs on 2009-09-30
Thank you.  That was what I thought I had set up, but the info just seemed strange because when I added a second RAID array and set it up with LVM partitions, it didn't have the 'lvm' flag or the extended partition.

---

