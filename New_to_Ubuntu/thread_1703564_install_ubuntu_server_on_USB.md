---
title: "install ubuntu server on USB"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by rawatabhishek23 on 2011-03-09
Hi,
I have installed Ubuntu Server 10.04 on a usb drive on one of my old laptops. I used USB for installation since my internal HDD had some issues. My concern (which i noticed later) is that the USB which I used for Server generally shows /dev/sdb1 but if i use the other pendrives (on different usb ports) the server hangs and the "server usb" name changes to /dev/sdc1 after hard restart while the new pendrive gets the name /dev/sdb1. 

I want to fix the disk label for the "server usb".

---

### Post by Daveth on 2011-03-09
this may help you:

[HTML]https://help.ubuntu.com/community/RenameUSBDrive[/HTML]

---

### Post by rawatabhishek23 on 2011-03-15
Thanks for the suggestion. But i still have some problem. I think I should rephrase my question. What should i do to prepare the USB for installing Ubuntu server?

I recall, while installing server when i was prompted for partition, I had selected Guided which created 1 ext4 partition and 1 swap partition. Do I need to make modifications in MBR? Should I format the USB first in ext4 format?

My USB (with Ubunu Server) keeps crashing and the following shows the system logs:

Mar  6 20:27:19 raond630 kernel: [    7.273651]  sdb: sdb1 sdb2 < sdb5 >
Mar  6 20:27:19 raond630 kernel: [    7.360134] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Mar  7 16:54:39 raond630 kernel: [    7.229879]  sdb: sdb1 sdb2 < sdb5 >
Mar  7 16:54:39 raond630 kernel: [    7.321199] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Mar  7 17:48:57 raond630 kernel: [    7.286034]  sdb1
Mar  7 21:58:24 raond630 kernel: [    7.270509]  sdb: sdb1 sdb2 < sdb5 >
Mar  7 21:58:24 raond630 kernel: [    7.348841] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
Mar  7 21:58:24 raond630 kernel: [    7.348849] EXT4-fs (sdb1): write access will be enabled during recovery
Mar  7 21:58:24 raond630 kernel: [   18.532502] EXT4-fs (sdb1): orphan cleanup on readonly fs
Mar  7 21:58:24 raond630 kernel: [   18.532511] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 154863
Mar  7 21:58:24 raond630 kernel: [   18.532570] EXT4-fs (sdb1): 1 orphan inode deleted
Mar  7 21:58:24 raond630 kernel: [   18.532574] EXT4-fs (sdb1): recovery complete
Mar  7 21:58:24 raond630 kernel: [   19.951548] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Mar  9 11:58:01 raond630 kernel: [    7.257636]  sdb: sdb1 sdb2 < sdb5 >
Mar  9 11:58:01 raond630 kernel: [    7.352953] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Mar 14 07:07:58 raond630 kernel: [    7.278138]  sdb: sdb1 sdb2 < sdb5 >
Mar 14 07:07:58 raond630 kernel: [    7.364979] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
Mar 14 07:07:58 raond630 kernel: [    7.364987] EXT4-fs (sdb1): write access will be enabled during recovery
Mar 14 07:07:58 raond630 kernel: [    9.495515] EXT4-fs (sdb1): orphan cleanup on readonly fs
Mar 14 07:07:58 raond630 kernel: [    9.500915] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 155075
Mar 14 07:07:58 raond630 kernel: [    9.503887] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 392015
Mar 14 07:07:58 raond630 kernel: [    9.510858] EXT4-fs (sdb1): 2 orphan inodes deleted
Mar 14 07:07:58 raond630 kernel: [    9.510864] EXT4-fs (sdb1): recovery complete
Mar 14 07:07:58 raond630 kernel: [    9.541927] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Mar 15 01:58:55 raond630 kernel: [    7.266386]  sdb: sdb1 sdb2 < sdb5 >
Mar 15 01:58:55 raond630 kernel: [    7.354835] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
Mar 15 01:58:55 raond630 kernel: [    7.354843] EXT4-fs (sdb1): write access will be enabled during recovery
Mar 15 01:58:55 raond630 kernel: [   17.026793] EXT4-fs (sdb1): recovery complete
Mar 15 01:58:55 raond630 kernel: [   17.083811] EXT4-fs (sdb1): mounted filesystem with ordered data mode
Mar 15 11:22:32 raond630 kernel: [    7.254509]  sdb: sdb1 sdb2 < sdb5 >
Mar 15 11:22:32 raond630 kernel: [    7.343840] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
Mar 15 11:22:32 raond630 kernel: [    7.343848] EXT4-fs (sdb1): write access will be enabled during recovery
Mar 15 11:22:32 raond630 kernel: [    9.958845] EXT4-fs (sdb1): recovery complete
Mar 15 11:22:32 raond630 kernel: [    9.961660] EXT4-fs (sdb1): mounted filesystem with ordered data mode

---

