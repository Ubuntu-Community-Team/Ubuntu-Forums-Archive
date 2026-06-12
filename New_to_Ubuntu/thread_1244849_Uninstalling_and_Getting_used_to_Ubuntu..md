---
title: "Uninstalling and Getting used to Ubuntu."
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Caboose104 on 2009-08-19
When I first got Ubuntu, I didn't know what I was getting into. So now Im going to back to Windows XP, but am going to get a Virtual Drive thing so I can get used to Ubuntu before switching to it completely. My question is when I load the windows XP Cd will it delete ubuntu or is there a way to uninstall/delete it before i load in the CD?

---

### Post by 3rdalbum on 2009-08-19
If it's Windows XP, you need to format the partition as fat32 or ntfs first, using Gparted on the Ubuntu live CD.

---

### Post by Caboose104 on 2009-08-19
What? O.o

---

### Post by 3rdalbum on 2009-08-19
> **Caboose104 said:**
> What? O.o

1. Boot up the Ubuntu live CD (also known as the Desktop CD)

2. Go to System > Administration > Partition Editor

3. Select your hard drive and right-click. Choose "Format As" and go to "fat32" as the filesystem type.

4. Click Apply.

5. After it has finished, reboot the machine and install Windows. It will now see the fat32 partition on your hard drive and be able to install.

---

### Post by Merk42 on 2009-08-20
First off, the Windows XP install disc should be able to format it.

Second you want NTFS, not Fat32

---

### Post by mazz0 on 2009-08-20
Aye, the Windows installer is perfectly capable of removing your Ubuntu installation.  It's when you want to /keep/ it that you have a problems!

---

### Post by 3rdalbum on 2009-08-20
> **mazz0 said:**
> Aye, the Windows installer is perfectly capable of removing your Ubuntu installation.  It's when you want to /keep/ it that you have a problems!

Ahh okay, I've never installed Windows XP. I've only ever read topics of "I'm trying to install Windows XP and it says no hard disks connected!" and the suggestion has always been to reformat the whole hard disk as a Windows-detectable format.

---

### Post by Copernicus1234 on 2009-08-20
> **3rdalbum said:**
> 1. Boot up the Ubuntu live CD (also known as the Desktop CD)

2. Go to System > Administration > Partition Editor

3. Select your hard drive and right-click. Choose "Format As" and go to "fat32" as the filesystem type.

4. Click Apply.

5. After it has finished, reboot the machine and install Windows. It will now see the fat32 partition on your hard drive and be able to install.

FAT 32? Your last windows must have been Windows 95 or something. :)

---

### Post by MelDJ on 2009-08-20
My question is when I load the windows XP Cd will it delete ubuntu

yes. when you install windows you have to format the drive to ntfs. Since ubuntu uses ext3, it will be formatted.

---

### Post by philinux on 2009-08-20
I reinstalled an xp system last weekend. Worms trojans you name it.

The xp disk works just fine just follow your nose. NTFS.

---

### Post by running_rabbit07 on 2009-08-20
There was a thread just yesterday where the OP was saying that the install disk didn't see the HD because of the format not being NTFS nor FAT. It didn't even recognize the drive.

---

### Post by Mark Phelps on 2009-08-20
> **running_rabbit07 said:**
> There was a thread just yesterday where the OP was saying that the install disk didn't see the HD because of the format not being NTFS nor FAT. It didn't even recognize the drive.

That often happens because original XP disks were not able to see drives connected through SATA controllers.  I've also read that if the current drive is formatted entirely for Linux (Ext 3 or Ext 4), the XP disk doesn't even see the drive, also.  The solution has been to boot from an Ubuntu CD, run GParted, and remove the partitions and/or create new empty partitions that XP can see.

---

