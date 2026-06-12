---
title: "How do I format a flashdrive with fat32?"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by jjblackfox on 2009-02-14
Hi, I'm trying to make my usb flashdrive boot super ubuntu, and it's too big to fit on a cd.

I'm following this tutorial:
[http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html](http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html)

The first step is to format my flashdrive with FAT32. How do I do this?

---

### Post by bsharp on 2009-02-14
Plug the flash drive in, and type

```
mkfs -T vfat /dev/whatever_your_flash_drive_is
```

Make sure you put the right device in the command or you will format your harddrive.

---

### Post by jjblackfox on 2009-02-14
> **bsharp said:**
> Plug the flash drive in, and type

```
mkfs -T vfat /dev/whatever_your_flash_drive_is
```

Make sure you put the right device in the command or you will format your harddrive.

I can't find my flashdrive under /dev/ anywhere.

---

### Post by theozzlives on 2009-02-14
I know, I know... I use Windows to format my flash drive.

---

### Post by jjblackfox on 2009-02-14
> **theozzlives said:**
> I know, I know... I use Windows to format my flash drive.

heh, don't have windoze

---

### Post by adult swim on 2009-02-14
with  your flash drive plugged in, what is the output of ```
sudo fdisk -l
```

---

### Post by jjblackfox on 2009-02-14
> **jjblackfox said:**
> I can't find my flashdrive under /dev/ anywhere.

I found it under ../media/
when I try mkfs -t vfat disk, I get: 
"mkfs -T vfat disk/
mke2fs 1.41.4 (27-Jan-2009)
disk/ is not a block special device.
Proceed anyway? (y,n) "

Hitting y gives me: 
"mkfs.ext2: Device size reported to be zero.  Invalid partition specified, or
	partition table wasn't reread after running fdisk, due to
	a modified partition being busy and in use.  You may need to 	reboot
	to re-read your partition table.

"

---

### Post by jjblackfox on 2009-02-14
> **adult swim said:**
> with  your flash drive plugged in, what is the output of ```
sudo fdisk -l
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdaafdaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 4008 MB, 4008246784 bytes
255 heads, 63 sectors/track, 487 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007ee9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3914272    e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(486, 254, 63) logical=(487, 78, 38)

---

### Post by jjblackfox on 2009-02-14
> **jjblackfox said:**
> I found it under ../media/
when I try mkfs -t vfat disk, I get: 
"mkfs -T vfat disk/
mke2fs 1.41.4 (27-Jan-2009)
disk/ is not a block special device.
Proceed anyway? (y,n) "

Hitting y gives me: 
"mkfs.ext2: Device size reported to be zero.  Invalid partition specified, or
	partition table wasn't reread after running fdisk, due to
	a modified partition being busy and in use.  You may need to 	reboot
	to re-read your partition table.

"

mkfs -T vfat /dev/sdb
mke2fs 1.41.4 (27-Jan-2009)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
mkfs.ext2: Permission denied while trying to determine filesystem size

---

### Post by spcwingo on 2009-02-14
Why not just install gparted?

---

### Post by mkvnmtr on 2009-02-14
Like the other poster said Gparted. I always install Gparted and then I can use it to do what ever I need to do to my externals.

---

### Post by jjblackfox on 2009-02-14
> **spcwingo said:**
> Why not just install gparted?

That worked perfectly, thanks

---

### Post by Albertov on 2013-04-06
In my case formatting de USB drive wasn't succesfull. Using Gparted it finished very quickly but when I put the Iso-file to the drive it failed.
I tried using dosfstools too but that didn't work for me eighter.

Finally I succeeded by using DBAN to erase the disk. After that I used Gparted to put a partition back on it and formatted it in FAT32. Then the USB drive was ready to use for saving the Iso-file with Unetbootin.

The only bad thing about Dban is that it can not erase the USB-drive alone, it will erase all the harddrives. So the way to use it is connect the USB-drive to the computer an run Dban. Note that after that this computer is free from any operationsystem and all data will be lost. 
Off course you need a second computer (with Linux or Windows) to save the Iso.

---

### Post by oldos2er on 2013-04-06
Closed, please don't bump old threads.

---

