---
title: "USB Unmountable"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by hex_ten on 2009-01-16
When attempting to mount my new USB stick I get the message "Invalid mount option when attempting to mount volume".

Here is the result of fdisk -l

hex@hex-laptop:~$ sudo fdisk -l
[sudo] password for hex: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000197cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14264   114575548+  83  Linux
/dev/sda2           14265       14593     2642692+   5  Extended
/dev/sda5           14265       14593     2642661   82  Linux swap / Solaris

Disk /dev/sdb: 4216 MB, 4216324096 bytes
130 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 8060 * 512 = 4126720 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?       96543      238170   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(96542, 119, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(238169, 54, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       20930      261132   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(20929, 28, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(261131, 30, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      231996      472198   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(231995, 28, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(472197, 29, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      358025      358032       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(358024, 124, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(358031, 109, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
hex@hex-laptop:~$ 

Unfortunately I haven't got a clue what's going wrong OR what this means, could somebody help me.

Thanks,
- Hex

EDIT: I should add that i'm running ubuntu 8.04.1 hardy

---

### Post by taurus on 2009-01-16
Do you have any valuable files on /dev/sdb (USB drive)?  The partition table is a big mess so maybe it's probably best to use gparted from System -> Administration (install it if you don't have one) to delete all the partitions on /dev/sdb1.  Then, create a new one, /dev/sdb1, and format it to whatever filesystem you want.

---

### Post by hex_ten on 2009-01-16
Hey, thanks for the quick response, so to install I'd just search that in the package manager?

Ok, then I reformat the drive and use FAT32?

Going to go and see if i can workout how to install the partition editor

Thanks,
- Hex - completely new to linux

---

### Post by taurus on 2009-01-16
If you use synaptic or add/remove, the package name is gparted.  Otherwise, you can install it from a terminal with

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```
And yes, you can format it to fat32/vfat.

---

### Post by hex_ten on 2009-01-16
Thanks again! I managed to find it in the package manager and now it seems to work fine! Haven't tried it on windows but it should work as it's fat32.

Quick noob question - how to I rename the drive?

Thanks for taking me through this step by step! Hopefully some other people new to ubuntu will find this info useful.

- Hex

---

### Post by hex_ten on 2009-01-16
Renamed it in windows and it works perfectly! Thanks again.

One small question though, what's wrong with this fdisk?

hex@hex-laptop:~$ sudo fdisk -l
[sudo] password for hex: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000197cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14264   114575548+  83  Linux
/dev/sda2           14265       14593     2642692+   5  Extended
/dev/sda5           14265       14593     2642661   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e71f6b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001    7  HPFS/NTFS
hex@hex-laptop:~$ 

Is the main problem that it's running NTFS?

- Hex

---

### Post by taurus on 2009-01-16
> **hex_ten said:**
> 

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e71f6b4

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1               1      182401  1465136001    7  HPFS/NTFS**
hex@hex-laptop:~$ 

Is the main problem that it's running NTFS?

- Hex

Yip.  You've formatted it as ntfs filesystem.  But that is the main problem are we talking about now?  When you are done using your USB drive in windows, make sure you use the Safely Remove Hardware icon in the bottom right corner to unmount it first before you unplug it.

---

### Post by hex_ten on 2009-01-16
Ahh, thanks very much once again. I think that's me out of questions now!

Thanks!

- Hex

---

