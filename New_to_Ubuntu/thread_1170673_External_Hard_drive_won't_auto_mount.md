---
title: "External Hard drive won't auto mount"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by robgora on 2009-05-26
I just installed the Ubuntu 8.04 32 bit verion. I first tried the 64 bit version but installed the 32 bit over the 64 bit. The issue I am having is my 1.5 tb External hard drive shows up as "USB Drive" in under "Computer". When I double click on it, it gives me an error saying it can't be mounted. 
 
If I use the command, "sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs" the drive will mount as "hd-ntfs" and I can see my data. But I still see the "USB Drive" as well. Is there a way to make my external hard drive show up correctly without having to do it from the Terminal?
 
**Edit**
When I first installed the 64 bit version, the external hard drive worked fine. It was only after installing the 32 bit version that I started seeing this issue.

---

### Post by camper365 on 2009-05-26
Try

```
sudo aptitude reinstall ntfs-3g
```
That package might have issues with it.

---

### Post by robgora on 2009-05-26
After re-installing ntfs-3g it still acts the same.

**Edit**
This is what I get when I type fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28680   230368252    7  HPFS/NTFS
/dev/sda2           28681       28742      498015   82  Linux swap / Solaris
/dev/sda3           28743       38913    81698557+  83  Linux

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
1 heads, 63 sectors/track, 46512336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Disk identifier: 0x01a6c147

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2    46512256  1465136032+   7  HPFS/NTFS

---

### Post by kay-man on 2009-05-26
Do you have an entry in /etc/fstab for the drive?

You'll need something like this:

```
UUID=EA68D95268D91E60 <mount point> ntfs-3g defaults,locale=nl_NL.UTF-8 0 2
```

With a different locale, most probably.

You can find the UUID by running:

```
blkid /dev/sdb1
```

---

### Post by robgora on 2009-05-26
No there is nothing in the /etc/fstab for the /dev/sdb1 (my external drive. But there is also nothing like what you posted. The only thing that I have is this.

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=b6cf7993-1174-4bd1-80d5-52b8dcd1a08e / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda2 :
UUID=8ec4456e-714d-4b5f-8cf7-5603ba25a44a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/Seagate\040Harddrive ntfs-3g defaults,locale=en_US.UTF-8 0 0

**Edit**
This is the print out from doing a lsusb.

Bus 007 Device 004: ID 0bc2:3300 Seagate RSS LLC 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 005 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 005 Device 003: ID 413c:8126 Dell Computer Corp. 
Bus 005 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

---

### Post by benerivo on 2009-05-26
You could try putting an entry in fstab for it, but i only really know how to add an entry for a drive that is permanently plugged in. Does your drive has its own power supply, and is it plugged in all the time?

I might try a line like...

UUID=KJGIJJHF78765H7 /media/hd-ntfs ntfs-3g defaults 0 0

(making sure that i had made the folder "hd-ntfs", and that i had changed its permissions to have read/write access)

Also, get the right UUID number for your drive by mounting it manually and using the blkid command in a terminal.

---

### Post by powel212 on 2009-05-26
Add/Remove

NTFS Configuration Tool

It should show up either under System Tools or System>Administration once it is installed.

A nice GUI for handling internal and external NTFS devices automatically at boot.

No need to edit fstab or sudo anything.

Enjoy

Powel

---

### Post by robgora on 2009-05-26
> **powel212 said:**
> Add/Remove
 
NTFS Configuration Tool
 
It should show up either under System Tools or System>Administration once it is installed.
 
A nice GUI for handling internal and external NTFS devices automatically at boot.
 
No need to edit fstab or sudo anything.
 
Enjoy
 
Powel
 
I have the NTFS Config tool installed but it only shows the partition that Windows is installed on. And I can see the device in fdisk -l. But it only shows as a USB Drive under computer. And I can manually mount it. But why can't it mount right when I plug it in?

---

### Post by kay-man on 2009-05-27
I think you need a line in /etc/fstab or it won't mount

---

