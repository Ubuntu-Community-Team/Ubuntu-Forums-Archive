---
title: "Questions about GRUB"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by Neon_Knight on 2009-06-11
Well my current situation is this - after a bunch of corrupt partition problems were fixed, and my hard drives were all swapped around for reasons that I won't go into, I've finally got all of my Ubuntu partitions in the GRUB menu working - except my windows XP one.  I formatted and reinstalled Wndows XP today, and then used Super Grub Disk to fix up the GRUB, but the windows XP entry doesn't work.  "Error 13, not executable" or some such.

Basically, is there any application that can simply, scan through all of your current partitions, find ones that are bootable, and generate a working GRUB file from?  I don't like this fiddling around with config files, finding reference names of partitions, taking away a number, using some letter, adding into some file, it all seems terribly stone-age to me.

With the current state of Ubuntu being very graphically and technically advanced in nearly every aspect, it seems very odd to be that we have to go through this horrid process, just to ensure that the GRUB entries are working.

There must be some sort of GUI application that can just scan the partitions and write it to the GRUB, and tell you what it's doing, with helpful friendly progress bars and the like?  That way, every entry points to a proper bootable partition?   And you can, say, select which order they go in, or which ones should show up. And it would also let you preview how it looks.  Super Grub Disk doesn't do any of this as far as I can tell, and if it does it's hidden somewhere amongst some horrid mass of ASCII interface options and help files..  

And why does GRUB have to look so blummin bad as well?   I used Solaris a few years ago, and the partition-selector that came with it was so ridiculously swish that I promptly passed out and needed CPR.  I nearly died that day.

Raging at GRUB at the moment and wanting to fix my Windows XP bootable partition.  :popcorn:

---

### Post by master_kernel on 2009-06-11
> **Neon_Knight said:**
> Well my current situation is this - after a bunch of corrupt partition problems were fixed, and my hard drives were all swapped around for reasons that I won't go into, I've finally got all of my Ubuntu partitions in the GRUB menu working - except my windows XP one.  I formatted and reinstalled Wndows XP today, and then used Super Grub Disk to fix up the GRUB, but the windows XP entry doesn't work.  "Error 13, not executable" or some such.

Basically, is there any application that can simply, scan through all of your current partitions, find ones that are bootable, and generate a working GRUB file from?  I don't like this fiddling around with config files, finding reference names of partitions, taking away a number, using some letter, adding into some file, it all seems terribly stone-age to me.

With the current state of Ubuntu being very graphically and technically advanced in nearly every aspect, it seems very odd to be that we have to go through this horrid process, just to ensure that the GRUB entries are working.

There must be some sort of GUI application that can just scan the partitions and write it to the GRUB, and tell you what it's doing, with helpful friendly progress bars and the like?  That way, every entry points to a proper bootable partition?   And you can, say, select which order they go in, or which ones should show up. And it would also let you preview how it looks.  Super Grub Disk doesn't do any of this as far as I can tell, and if it does it's hidden somewhere amongst some horrid mass of ASCII interface options and help files..  

And why does GRUB have to look so blummin bad as well?   I used Solaris a few years ago, and the partition-selector that came with it was so ridiculously swish that I promptly passed out and needed CPR.  I nearly died that day.

Raging at GRUB at the moment and wanting to fix my Windows XP bootable partition.  :popcorn:
Well, it'd be the day when a program like that came out. Could you post your /boot/grub/menu.lst?

---

### Post by Neon_Knight on 2009-06-11
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d57f5ef1-4e61-4089-86d3-0c3de50d0523 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d57f5ef1-4e61-4089-86d3-0c3de50d0523

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d57f5ef1-4e61-4089-86d3-0c3de50d0523
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d57f5ef1-4e61-4089-86d3-0c3de50d0523 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d57f5ef1-4e61-4089-86d3-0c3de50d0523
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d57f5ef1-4e61-4089-86d3-0c3de50d0523 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d57f5ef1-4e61-4089-86d3-0c3de50d0523
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
rootnoverify	(hd3,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

That "rootnoverify" for Windows XP WAS originally (hd2,0), but my 80GB windows hard drive is listed as sdc1, so I changed it to (hd3,0), assuming that was right.  And then I lost the "not executable" error message and now it just hangs.  

Also here's my fdisk -l (yes, I have quite a few partitions..  6, to be exact, but the sdc1 80GB is my windows bootable.  That 180GB linux partition is the Ubuntu boot partition. Sda6 I think)

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006ac1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1        8001    1  FAT12
/dev/sda2   *           2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sda5               2        5838    46885671    7  HPFS/NTFS
/dev/sda6            5839       28785   184321746   83  Linux
/dev/sda7           28786       30401    12980488+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007816

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7942    63794083+  83  Linux
/dev/sdb2            7943        7955      104422+   f  W95 Ext'd (LBA)
/dev/sdb3            7956       30386   180177007+   7  HPFS/NTFS
/dev/sdb5            7943        7955      104391    e  W95 FAT16 (LBA)

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfab6fab6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3dd2ab17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       19457   156288321    7  HPFS/NTFS

```

---

### Post by master_kernel on 2009-06-11
Try:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
rootnoverify	(hd3,0)
savedefault
chainloader	+1
```

Just getting rid of the maps.

---

### Post by Neon_Knight on 2009-06-11
Didn't work.

It does "starting up..."

and then blank.

---

### Post by master_kernel on 2009-06-11
Seems like you need to chkdsk your Windows drive.

---

