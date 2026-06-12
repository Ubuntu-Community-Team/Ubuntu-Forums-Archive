---
title: "[SOLVED] Grub installed on wrong hard drive. How do i remove it?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by BewareOfDog on 2009-01-04
I am fairly new to linux and ubuntu. On one of my computers I have a 160GB HDD (IDE) which contains windows xp in the first partition and a second 500GB HDD (SATA) that was to just be for media storage. I installed ubuntu on the first (160GB IDE, 2nd partition, dual boot w/xp). I had many problems with a older PCI nvidia Geforce FX5200 video card. I tried many workarounds suggested by these forums and changed all kinds of things (drivers, etc.). I took the card out and went back to the onboard video but still could not get ubuntu to boot. I took the easy way out and re-installed ubuntu 8.10, but this time I thought, "I'll put it on the SATA drive, faster data transfer with the SATA, right?". Thats what I did, but then grub would not function. I knew that the first install wrote grub to the SATA drive for some reason, even though ubuntu 8.10 was installed on the first IDE drive. I thought, "thats ok, I'll just set 2nd SATA drive as primary boot in bios and windows MBR was untouched." That was fine. The second install was installed on the 2nd drive (SATA) drive in a new partition for ubuntu. (I reformatted over the first ubuntu install on the first drive to NTFS) and for some reason the second install wrote grub to the first drive MBR over windows boot loader. I resolved the grub problem by switching the primary boot drive back to the 160GB IDE drive in BIOS, so that the proper grub is booting. I do still however have a "corrupt" grub bootloader on the 2nd SATA drive (that actually has ubunutu installed on it). Do I just leave it there? Is there a way to delete that? Can one access that part of a hard disk and reformat? The computer is working just fine, I just wish that I was able to control where grub was written in the first place. It should never have been written to that 2nd drive to begin with. Nothing was on there but media files. Thanks for any advice.

---

### Post by logos34 on 2009-01-04
This is easy:

> sudo dd if=/dev/zero of=/dev/**sdc** bs=446 count=1

Just make sure your get the right disk.  Check with

sudo fdisk -l

Or use 'Uninstall' option on Super Grub Disk

---

### Post by BewareOfDog on 2009-01-04
ok, this is what I got from: sudo fdisk -l 


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ffe3ffd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9689    77826861    7  HPFS/NTFS
/dev/sda2            9690       19457    78461460    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x654f16e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        7834       60801   425465460    7  HPFS/NTFS
/dev/sdb2               1         498     4000153+  82  Linux swap / Solaris
/dev/sdb3             499        7833    58918387+  83  Linux

Partition table entries are not in disk order

It is /dev/sdb that has the wrong grub on it. Is the command that you gave me the same, or do I change it for dev/sdb ?    ie:

sudo dd if=/dev/zero of=/dev/sd_**b**_ bs=446 count=1

Thanks for the quick response.

---

### Post by logos34 on 2009-01-04
> **BewareOfDog said:**
> 
sudo dd if=/dev/zero of=/dev/sd_**b**_ bs=446 count=1


yes.

---

### Post by BewareOfDog on 2009-01-04
Wow, what a difference knowing the right command makes. Problem solved. Thanks a million.

---

### Post by logos34 on 2009-01-04
glad I could help.  Mark as 'Solved' (-->thread tools). Enjoy

---

### Post by deadlockedgamer on 2010-04-25
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005ebe5

   Device Boot      Start         End      Blocks   Id  System
tag@tag-desktop:~$ 
is my out put I need to boot off the first hardrive sda would I put sda in the command?

---

### Post by deadlockedgamer on 2010-04-25
and would this move it to the right disk? I don't have a dual boot. The 200 gb drive lost its formating for whatever reason when I installed and now it has to be hooked up to boot. I want to refomat it to hold data but first need to move the boot loader!

---

