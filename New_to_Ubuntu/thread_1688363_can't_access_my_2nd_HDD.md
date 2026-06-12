---
title: "can't access my 2nd HDD"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by Jouke S on 2011-02-15
Hey guys.
I run a dualboot of Windows 7 and Ubuntu 10.10.
I have two HDD's; my primary 750gb one which I use as my primary HDD for both Ubuntu and Windows. No problems with this one.

My second HDD, which I use for file storage only, doesn't seem to want to show its files to me on Ubuntu, while it works perfectly on Windows.

This is what GParted says about it: 
[[IMG]http://img821.imageshack.us/img821/9158/hddc.png[/IMG]](http://img821.imageshack.us/i/hddc.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by TeoBigusGeekus on 2011-02-15
Run a checkdisk to it from windows and try again.

---

### Post by Hawkoon on 2011-02-15
it is not encrypted by any chance?

---

### Post by sikander3786 on 2011-02-15
Can you please post the output of this command.

```
sudo fdisk -lu
```

---

### Post by Jouke S on 2011-02-15
> **Hawkoon said:**
> it is not encrypted by any chance?


Ooh, that could be. I think I've run bitlocker a while ago. I'll look into that now.


sudo fdisk -lu
```
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69baf5f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    30722047    15360000   27  Unknown
/dev/sda2   *    30722048   747984895   358631424    7  HPFS/NTFS
/dev/sda3       747984896  1269094399   260554752    7  HPFS/NTFS
/dev/sda4      1269096446  1465147391    98025473    5  Extended
/dev/sda5      1269096448  1457086463    93995008   83  Linux
/dev/sda6      1457088512  1465147391     4029440   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcdce01a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953521663   976759808    7  HPFS/NTFS

```

---

### Post by Immolatus on 2011-02-15
open up gparted --> format and name the drive. The OS will show it in the "places" tap after that. It's just not got a name and probably isn't formatted. Remember, Linux treats everything as a file. How would you find a file with no name? you wouldn't unless you binsearched the whole drive/partition for contents.

---

### Post by Jouke S on 2011-02-15
Update: 
I cannot boot into Windows 7 anymore.
It's been slow for ages, I've been dreading reboots for months (that's why I usually left it on for usually a month consecutively), boots took about 15 minutes usually.
Now I just can't log in to Windows at all. It says it's updating and then just shuts down when it's done, only to do the same on the next boot. 
If the problem is encrypting of the HDD (I'm pretty sure I did encrypt it with bitlocker), please tell me. I will probably just do a clean install of Windows then. 

Thanks for the help guys

---

### Post by Jouke S on 2011-02-15
> **Immolatus said:**
> open up gparted --> format and name the drive. The OS will show it in the "places" tap after that. It's just not got a name and probably isn't formatted. Remember, Linux treats everything as a file. How would you find a file with no name? you wouldn't unless you binsearched the whole drive/partition for contents.

I've formatted it to ext4, that's what Ubuntu uses by default IIRC. I can't seem to find an option to rename my drive though?
EDIT: actually, I thought I had formatted it to ext4. I hadn't applied the changes yet. I get a message popping up saying this may cause data loss, would it be a good idea to just proceed, or not? This isn't a new HDD, it's filled with about 900gb files I want to keep.

Thanks for the help

---

### Post by Immolatus on 2011-02-15
This isn't a new HDD, it's filled with about 900gb files I want to keep.



My best advice: Boot windows in safe mode(stops most background processes). Back up all important data. Reinstall win on first drive using half of the drive. Install Ubuntu next, manually edit partition table setting first partition for Linux as swap(closer to center of disk means swap will access faster). Format and name the spare drive. If you format the second drive to Fat32 both OS's can use it BTW.

---

### Post by Hawkoon on 2011-02-15
> **Jouke S said:**
> I've formatted it to ext4, that's what Ubuntu uses by default IIRC. I can't seem to find an option to rename my drive though?
EDIT: actually, I thought I had formatted it to ext4. I hadn't applied the changes yet. I get a message popping up saying this may cause data loss, would it be a good idea to just proceed, or not? This isn't a new HDD, it's filled with about 900gb files I want to keep.

Thanks for the help

I wouldn't format the drive until you have a backup of your data. If you cannot mount the drive on your system, maybe you have access to another healthy Windows?

> **Jouke S said:**
> If the problem is encrypting of the HDD (I'm pretty sure I did encrypt  it with bitlocker), please tell me. I will probably just do a clean  install of Windows then.

I can't help you with Win7, never used bitlocker either. I use truecrypt, it works on both Windows and Linux. Until I unlock my drives (I do it manually) gparted would show me similar diagnostics to what you are reporting, hence my comment.

Just had a look, bitlocker seems to be Windows only!!! But if the drive is fully encrypted, and you want to make a backup of your data, you will have to get Windows running including bitlocker.

---

