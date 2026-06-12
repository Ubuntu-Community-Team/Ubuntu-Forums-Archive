---
title: "so confused by my own partitioning"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Knacker on 2008-12-28
Hi, 
I'm honestly not certain about the history of how I got here, but i have a strange partition situation...and I can't figure out what I've done. I have a 15gb partition that auto-mounts in nautilus, but isn't (as far as I can tell) listed in my fstab file. The 15gb mounted partition (auto-mounted at /media/disk) contains a file system for a previous version of ubuntu. I'd like to delete it and merge that 15gb with my /home partition, but my worry is that the 15gb old-ubuntu-filesystem partition is also my boot partition! Or at least so it seems from what i see from "sudo fdisk -l". The strange thing about THAT, though, is that the boot menu (menu.lst) that I see when i start up does not reflect the information in the menu.lst that is in (what I THINK) is the boot partition. Which is all to say that I have no idea what's going on. 
In other words, my question is this: is /dev/sda1 my mystery old-ubuntu-file-system partition? Is it also my boot partition? And, finally, how can i safely delete that old file system and merge that partition wiht my home directory (/dev/sda2)?

Sorry if this is confusing -- I'm confused. I'm going to paste in the relevant parts of the obvious files. Could someone please take a look and help me understand. Thanks a lot.      

Screenshot of gparted: 
[http://img236.imageshack.us/my.php?image=screenshotgpartedpw1.jpg](http://img236.imageshack.us/my.php?image=screenshotgpartedpw1.jpg)

/etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=05018208-15c6-42f4-8c7f-c7a9b376a0e1 /               ext3    relatime,errors=remount-ro 0       0
# /dev/sda2
UUID=cb1779d5-a1a0-471c-a0cb-b5f437ebd1ba /home           ext3    relatime        0       0
# /dev/sda3
UUID=93214e15-66d9-4fdc-ace6-f261f4179f8d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
______________________

sudo fdisk -l: 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00013be7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825       16612   118784610   83  Linux
/dev/sda3           19210       19457     1992060   82  Linux swap / Solaris
/dev/sda4           17316       19209    15213555   83  Linux

Partition table entries are not in disk order

___________________________

/boot/grub/menu.lst:

title		Linux Mint, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin

 
Thanks again!

---

### Post by zvacet on 2008-12-28
You can delete it and add to your home partition.You can also add 5GB of anallocated space to your home.If you have trouble booting [reinstall grub.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

---

### Post by louieb on 2008-12-28
> **Knacker said:**
> ..In other words, my question is this: is /dev/sda1 my mystery old-ubuntu-file-system partition? Is it also my boot partition? 

And, finally, how can i safely delete that old file system and merge that partition wiht my home directory (/dev/sda2)?

/dev/sda1 seems to be just as you thought your old Ubuntu installation. According to /etc/fstab  it is not the boot partition. 

While you can use Gparted to delete sda1 and grow sda2 to the left and fill that space. sda2 is so full and will take an hour or more to complete - I would not trust it to do it safely. A power surge or cut off would be disastrous to your data.   

For safety sake sda2 needs to copied off to another disk before  merging sda1 and sda2.
Good Luck.

---

### Post by Knacker on 2008-12-31
sounds right. thanks so much!:D

---

