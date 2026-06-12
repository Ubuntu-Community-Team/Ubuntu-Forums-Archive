---
title: "Ubuntu can't find partition"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by groovy354 on 2010-08-04
I plugged my usb HDD with 3 partitions on it, but Ubuntu sees only one... how to show other ones?

---

### Post by Zorgoth on 2010-08-04
What happens if you type 

"sudo fdisk -l"?

---

### Post by groovy354 on 2010-08-04
Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcadb02d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2       19947   160216245    f  W95 Ext'd (LBA)
/dev/sdd3           19948       30402    83974306    c  W95 FAT32 (LBA)
/dev/sdd4               1           1          31+  11  Hidden FAT12
Partition 4 does not end on cylinder boundary.
/dev/sdd5               2       18535   148874323+   b  W95 FAT32
/dev/sdd6           18536       19947    11341858+   b  W95 FAT32


Partition table entries are not in disk order

(it's not the whole log, just the one 'bout the usb hdd in question)



How to mount other partitions...?

---

### Post by Zorgoth on 2010-08-04
Well, you can manually mount them using the mount command (note that due to the fat32 formatting, you will need to do some stuff to get th epermissions right; they cannot be changed except at time of mounting).

All I can remember about mounting fat32 is that you use the "-t vfat" switch.

Automounting is handled in /etc/fstab for internal devices, but I don't know whether you can do that safely with a device that may or may not be plugged in.

---

### Post by groovy354 on 2010-08-04
What's weird is that it discovers one of the partitions.. why it can't mount others?

---

### Post by -kg- on 2010-08-04
That ***is*** strange, because normally all partitions will automatically mount when you plug a USB device in...even when you reboot and leave the device plugged in.

Which partition is it that mounts?  That way, it will be easier to figure out what the problem is with the rest of them.

---

### Post by groovy354 on 2010-08-04
It shows one partition (named 250 GB something something, but it's only 10.1 GB large). I know wich one it is, but I don't know how to write it...

---

### Post by ranch hand on 2010-08-04
I am not sure what version of Ubuntu you are using but "disk utility" is installed by default in 10.04 and, I believe, available for 9.10.

If you are on 10.04 it will be found at System>Administration>Disk Utility.

It is a pretty handy little bugger and should pick up the partitions if fsdisk is and then you just need to click on the partition and then on "mount partition".

---

