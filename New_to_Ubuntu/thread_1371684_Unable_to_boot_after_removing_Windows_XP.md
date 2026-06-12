---
title: "Unable to boot after removing Windows XP"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by beegary on 2010-01-03
Im glad i am not on a support contract on these forums, totally using up my beans........


I had a dual boot on my netbook
Windows XP
Karmic Koala

I used gparted to format the windows partition using ext3 assuming that I would just boot straight to Ubuntu without any select screen.
No such luck, first of all I was getting No Operating System message

So I followed directions to fix my grub install, so that grub is installed on my linux partition.
But now all I get is a grub command prompt when I boot?
 I am curently running on a live cd if that helps anything!!

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb034b72b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4706    37800913+  83  Linux
/dev/sda3            4707       17454   102398295    7  HPFS/NTFS
/dev/sda4   *       17455       19457    16089097+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 2063 MB, 2063073280 bytes
16 heads, 32 sectors/track, 7870 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x88865f6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7870     2014704    b  W95 FAT32
ubuntu@ubuntu:~$ 
```

---

### Post by tom.swartz07 on 2010-01-03
> **beegary said:**
> Im glad i am not on a support contract on these forums, totally using up my beans........


I had a dual boot on my netbook
Windows XP
Karmic Koala

I used gparted to format the windows partition using ext3 assuming that I would just boot straight to Ubuntu without any select screen.
No such luck, first of all I was getting No Operating System message

So I followed directions to fix my grub install, so that grub is installed on my linux partition.
But now all I get is a grub command prompt when I boot?
 I am curently running on a live cd if that helps anything!!

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb034b72b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4706    37800913+  83  Linux
/dev/sda3            4707       17454   102398295    7  HPFS/NTFS
/dev/sda4   *       17455       19457    16089097+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 2063 MB, 2063073280 bytes
16 heads, 32 sectors/track, 7870 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x88865f6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7870     2014704    b  W95 FAT32
ubuntu@ubuntu:~$ 
```

Okay, first a few questions..

Are you sure that you deleted your Windows partition? It still shows a partition on your system with NTFS (usually that means Windows, unless you made a separate partition for something else.) Also, It doesnt seem to show your swap partition- that may be a problem..


Anyway, lets see if we could get you booting back up.
According to your fdisk output, Im going to tweak the method so that you could just copy and paste.


Now, we will rebuild your GRUB bootloader. 

Go to applications, Accessories, Terminal.

type
```
Code:
sudo mount /dev/sda1 /mnt
```
then
```
Code:
sudo mount /dev/sda3 /mnt
```
Next type
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
Now, just to be sure, type
```
sudo update-grub
```


You *should* be able to reboot and get back into your system.

---

### Post by beegary on 2010-01-04
> **tom.swartz07 said:**
> Okay, first a few questions..

Are you sure that you deleted your Windows partition? It still shows a partition on your system with NTFS (usually that means Windows, unless you made a separate partition for something else.) Also, It doesnt seem to show your swap partition- that may be a problem..


Yes I deleted the windows partition, I also had an ntfs share partition.

I have followed your terminal commands, but when I get to the firs grub bit \i get an error message:
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator

```

Thanks for your help

---

### Post by beegary on 2010-01-04
After looking through the files on those partitions \i have realised that ubuntu is actually on sda4??
SO \i reran the terminal code using sda4 and got this\;
```
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
/dev/sda does not have any corresponding BIOS drive
```

I think \i have too many problems, I going to reinstall ubuntu tonight. Anyting Ishould watch out for? I am going to wipe the drive and make new partitions what files system should \i use for a ubuntu only setup?

---

### Post by Methuselah on 2010-01-04
Hi beegary,

The common files systems for linux are ext3 and ext4.
The ubuntu installer operates on autopilot of you tell it to use the entire disk.
It'll create a ext4 root (/) partition (if 9.10 otherwise ext3) and a linux swap partition.

However, you can tell the installer exactly how you want your system to be partitioned.
Many people recommend having a separate partition for /home which is equivalent to windows' Document and Settings folder.
This is so you can image home separately for backup purposes or reinstall/upgrade the system on root without touching /home.

I found the link below that gives a good idea of what to expect.
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

All the best!

---

### Post by beegary on 2010-01-04
Thank you Methuselah
I think a fresh start is best anyway, it was my first install and I had messed around quite allot!
Looking forward to being Single Boot Ubuntu!

---

