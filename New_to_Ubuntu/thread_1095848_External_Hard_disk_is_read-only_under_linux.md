---
title: "External Hard disk is read-only under linux"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Alegria on 2009-03-14
My external hard disk that was first used under windows is read only under Linux. Is there anything that i can do to fix this?
I think it is in FAT32

---

### Post by MaindotC on 2009-03-14
Are you booting from a live cd or do you already have an installation of Ubuntu and you just connected the external drive?  Did windows properly shut down the external drive?  Did you try mounting the external drive with root permissions?

---

### Post by gogic on 2009-03-14
try to defragment it form win

---

### Post by Alegria on 2009-03-14
I have an installation of Ubuntu. Windows did properly shut it down, and if I try it on another windows pc i can write to it. I have also tried mounting it with root permissions.

---

### Post by betrunkenaffe on 2009-03-14
> **Alegria said:**
> I have an installation of Ubuntu. Windows did properly shut it down, and if I try it on another windows pc i can write to it. I have also tried mounting it with root permissions.

Are you sure it isn't ntfs format? You can check by typing

```
sudo fdisk -l
```

I've never had problems writing to FAT before, ntfs requires something extra from what I remember.

---

### Post by Alegria on 2009-03-14
Nope, it is FAT32:

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4541dcfe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    c  W95 FAT32 (LBA)

---

### Post by abybaddi on 2009-03-14
> **Alegria said:**
> My external hard disk that was first used under windows is read only under Linux. Is there anything that i can do to fix this?
I think it is in FAT32

This sometimes happened with my mobile storage, I then had to copy the contents somewhere and had to format it. After that every thing worked fine. And you get to know that windowx can read and write its owm partitions well so no question about your friend's PC.

---

### Post by MaindotC on 2009-03-14
Can you post the drive type and a link, kind of like my signature? I want to see if there's some type of protection put on it. Did you need special windoze software to use the drive or did it work out of the box?

---

### Post by Alegria on 2009-03-14
It did work right out of the box.
"Memorex unltra traveldrive", 160 Gb
it is this one, but than the 160 Gb version: 
[http://www.memorex.com/products/product_details.php?PID=1141](http://www.memorex.com/products/product_details.php?PID=1141)

---

### Post by MaindotC on 2009-03-16
I found the following information in the user's guide regarding compatibility:
> 
o Linux 2.5.x (Please see the [www.memorex.com](www.memorex.com) website under FAQ&#8217;s for &#8220;Mounting on Linux.&#8221;)

Did you follow the directions listed on the website?  Here is the FAQ.  Keep in mind that you do not have to reboot your machine - you can run the following commands from a terminal with root permissions.  You can make whichever directory you like to mount the drive but they SUGGEST /mnt/trek.  Lastly, the drive name in /dev may vary - it seems your system detects the drive as /dev/sdb1 not /dev/sda1.
> 
Q: TravelDrives: How do I mount the TravelDrive or ThumbDrive in Linux?

A: To use the TravelDrive or ThumbDrive on Linux do the following:

   1. Reboot your PC.
   2. Login as root.
   3. Plug in Thumbdrive Smart (the LED should light up).
   4. Open command console: Enter the command: "mkdir -p /mnt/trek ;mount -tvfat /dev/sda1 /mnt/trek"


---

### Post by mikechant on 2009-03-16
A space seems to have gone missing in 4/ above - should be
-t vfat
not
-tvfat

---

### Post by MaindotC on 2009-03-16
Good point, mike.  I must have copied it incorrectly.

---

