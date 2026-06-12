---
title: "trying to fdisk a FAT32 device"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by Franz01 on 2010-05-31
I have a USB disk attached to a linux box. It is a FAT32 device and I can mount it.

I'd like to add a linux partition (ext3 or ext3) to this USB disk but I am very confused when I run fdisk command:

```
root@xxx:/# fdisk /dev/sdb1

The number of cylinders for this disk is set to 30400.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
```

and when I enter p option this is what I get:

```
Command (m for help): p

Disk /dev/sdb1: 250.0 GB, 250056705024 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   ?      119512      153402   272218546+  20  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb1p2   ?       82801      116350   269488144   6b  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb1p3   ?       33551      120595   699181456   53  OnTrack DM6 Aux3
Partition 3 does not end on cylinder boundary.
/dev/sdb1p4   *       86812       86813       10668+  49  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

not sure how to proceed in order to have a second ext2/3 partition....

---

### Post by cogier on 2010-05-31
That all looks very complicated. Have you tried Gparted, it's in the Repository if you haven't got it already?

---

### Post by Barrucadu on 2010-05-31
You want to run

```
fdisk /dev/sdb
```

/dev/sdb1 is the partition, not the device itself. However, I recommend using gparted, as it's much simpler and handles filesystems for you.

---

### Post by StephenF on 2010-05-31
Try fdisk /dev/sdb instead.

---

### Post by srs5694 on 2010-05-31
If you want to keep data on the disk, don't use fdisk at all, since it can't modify filesystems. Instead, use the text-mode parted, the GUI GParted, or a similar tool. These will enable you to resize your existing FAT partition and create a new one. As others have pointed out, you also need to specify the device as /dev/sdb rather than /dev/sdb1.

Note that Windows only "sees" the first partition on removable disks, so if you want to use the disk with both Windows and Linux, you should shrink the FAT partition by moving its end point earlier rather than by moving its start point later. You'll then create your Linux partition(s) after the FAT partition, so Windows will still be able to read and write the FAT partition.

---

