---
title: "Small &quot;unallocated&quot; space left when resizing/merging partitions"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by dustoashes on 2010-01-17
Hi,
I'm attempting to "merge" two ext3 partitions by resizing partition #2 and adding the unallocated space to partition #1. However, if I resize the partition #2 to the smallest possible, its size is then 2318 mb. So my question is how do I squeeze these 2318 mb to partition #1 and have one, big partition without unallocated space?

The second question would be that I have some other unallocated space, but can't seem to create a partition out of it - since I already have 4 primary partitions. Any idea how to solve this?

I've added a screenshot from Gparted so you can see. Besides the Ubuntu partitions, there's the Windows 7 NTFS partition as well.

[IMG]http://i50.tinypic.com/2d9s7qb.jpg[/IMG]

Thanks!

---

### Post by audiomick on 2010-01-17
Your unallocated space is at the end of the drive. You have to shuffle everything along until the unallocated space is next to the partition you want to add it to.

You should back up anything important before you start moving partitions around.

---

### Post by JKyleOKC on 2010-01-17
If that 2318 MB partition is absolutely empty, simply delete it. That will make it unallocated space, which you can then expand the other partition into (once you have moved things around so that the two are adjacent).

Your fourth primary partition is "extended" which is a container for additional partitions. First expand the extended partition to take up the unallocated space.

Next, you can merge the space with the existing logical (inside the extended) swap partition or create a new one.

If you want to add the free space to another partition, first move it to be adjacent to the one you want to merge it into. Then expand that one to take up the space.

The whole purpose of the extended partition is to make it possible to have more than four partitions total on a drive; there's no difference in performance between a primary and a logical partition. The reason for the four-partition limit is that space in the MBR is quite limited and there's only room for four entries in its partition table. By making one of the four "extended" the system knows to link to an additional table that has no such space limit and can hold as many logical partitions as you want.

Whenever you add a new partition, if the MBR already has three primary partitions defined and none of them is extended, GPartEd will create the fourth as extended and then add the new one as logical within it. This makes it possible to add still more partitions later. That's why your swap partition is inside the extended one.

Hope this helps!

---

### Post by dustoashes on 2010-01-17
Hi,
thanks for the replies. I've managed to shuffle and get the touch on how GParted works, but I'm still wondering if it's possible to shrink **sda1** since it's on the left? If not, does it mean I have to delete the partition and go from there?

---

### Post by audiomick on 2010-01-17
You should be able to shrink sda1 without any trouble. That will leave un-allocated space between it and the next one over.

Once more: backup anything important before messing around with partitions.

---

### Post by hailholyghost on 2010-01-18
> **audiomick said:**
> You should be able to shrink sda1 without any trouble. That will leave un-allocated space between it and the next one over.

Once more: backup anything important before messing around with partitions.

I've been having similar issues in gparted.

I cut out several Gbytes out of my Win7 partition to create the unallocated space that's right next to the Karmic partition I'm using now, and I can't figure out how to combine the two.

When I right-click both the Karmic/ext4 and the unallocated partitions the option to resize is grayed out.

I cannot figure out how to merge the unallocated partition with Karmic.

Help?

Thanks in advance!

---

### Post by dustoashes on 2010-01-18
Hey, I've managed to shuffle around and make all the partitions look as I want them to. 

The only problem I have is that I get an Error 12 when I tried to load Ubuntu at the boot screen. Anyway, this is my sudo fdisk:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    51199154    25599546   83  Linux
/dev/sda3   *    51199155   478126529   213463687+   7  HPFS/NTFS
/dev/sda4       478126530   488392064     5132767+   f  W95 Ext'd (LBA)
/dev/sda5       478126593   488392064     5132736   82  Linux swap / Solaris
```

And menu.lst:

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
# kopt=root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c426a7a4-8085-4083-a540-049e4f78a229

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c426a7a4-8085-4083-a540-049e4f78a229 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c426a7a4-8085-4083-a540-049e4f78a229
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by JKyleOKC on 2010-01-18
> **hailholyghost said:**
> When I right-click both the Karmic/ext4 and the unallocated partitions the option to resize is grayed out.This sounds as if you're running gparted from the Karmic partition. You can't resize a partition while it's mounted. The solution is to boot from the Live CD and run gparted from there. You then should be able to resize the ext4 partition with no difficulty.

---

