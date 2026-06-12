---
title: "can't see USB hard drive"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by Someone uk on 2010-09-03
(ok i admit i might of done something stupid) 
i got an external hard rive from lacie a bit ago and i tried to create an ext4 partition but the disk utility kept refusing to create this partition but however the utility let me format the entire disk previously there was a 10mb ntfs partition with a lot of windows software and a 1000gb of "free" after it was formatted the utility said the entire space was "unallocated" then disappeared
i tried rebooting with the disk powerd on but it made no diffrence to it being recognised

i just want to ask if there any way i can at least find my hard drive or have i just rendered it unusable?

---

### Post by CharlesA on 2010-09-03
Post the output of this command please:

```
sudo fdisk -l
```

---

### Post by Someone uk on 2010-09-03
^^
> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x007971e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         659     5293386   82  Linux swap / Solaris
/dev/sda2   *         660        5226    36684427+  83  Linux
/dev/sda4            5227       30402   202213368   83  Linux
Partition 4 does not end on cylinder boundary.
doesn't even seem to be recognising the disk :S

---

### Post by jtarin on 2010-09-03
> **Someone uk said:**
> 
 however the utility let me format the entire disk And you formatted it with what filesystem?

---

### Post by bredman on 2010-09-03
In general, the way to prepare a drive is to use 'fdisk' to format the drive and 'mkfs' to make a usable file system. Did you use both commands, and did you have any problems?

Was the USB drive plugged in when you executed the fdisk -l command above?

---

### Post by Someone uk on 2010-09-03
> **jtarin said:**
> And you formatted it with what filesystem?

i just clicked on "format volume" it didn't even prompt me on file system

---

### Post by Someone uk on 2010-09-03
> **bredman said:**
> In general, the way to prepare a drive is to use 'fdisk' to format the drive and 'mkfs' to make a usable file system. Did you use both commands, and did you have any problems?

Was the USB drive plugged in when you executed the fdisk -l command above?

yes it's plugged in and powerd on

---

### Post by Someone uk on 2010-09-03
got it working (dodgy usb extension cable)
should of known it was a hardware fault

---

