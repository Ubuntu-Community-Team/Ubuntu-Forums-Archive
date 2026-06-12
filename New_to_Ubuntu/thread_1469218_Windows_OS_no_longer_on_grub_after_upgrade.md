---
title: "Windows OS no longer on grub after upgrade"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by bneva on 2010-05-02
I currently dual boot XP/Ubuntu and I am having a bit of a grub problem....

I was at version 9.04 and decided to upgrade to 9.10 and then 10.04.  When I finished upgrading to 9.04 my windows partition was no longer listed on the grub menu.  I don't really have any clue on how to add an entry in here.  I have looked around a bit and people generally just went
```

title		Windows XP
root		(hd0,0)
```

but as far as I know my windows is on my 2nd hard drive so instead of the 
(hd0,0) I tried (hd1,0) which doesn't work.  I am currently just trying different combos to see if I can figure it out.

Can anyone help me out?  Are there any commands to list the partitions that would say windows is on this or something?

---

### Post by WinterRain on 2010-05-02
Not sure, but try ```
sudo update-grub
```

---

### Post by GSF1200S on 2010-05-02
> **bneva said:**
> I currently dual boot XP/Ubuntu and I am having a bit of a grub problem....

I was at version 9.04 and decided to upgrade to 9.10 and then 10.04.  When I finished upgrading to 9.04 my windows partition was no longer listed on the grub menu.  I don't really have any clue on how to add an entry in here.  I have looked around a bit and people generally just went
```

title		Windows XP
root		(hd0,0)
```

but as far as I know my windows is on my 2nd hard drive so instead of the 
(hd0,0) I tried (hd1,0) which doesn't work.  I am currently just trying different combos to see if I can figure it out.

Can anyone help me out?  Are there any commands to list the partitions that would say windows is on this or something?

Open a terminal and type:
```
sudo update-grub
```

It should mention windows in the printout following (as well as Ubuntu). If that doesnt work, can you give us the printout of:
```
sudo fdisk -l
```

---

### Post by Animal X on 2010-05-02
before you do anything, can you show us a copy of your menu.lst ?

---

### Post by bneva on 2010-05-02
This was the output of the fdisk command

```
omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb6284573

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27428   220315378+   7  HPFS/NTFS
/dev/sda2           27429       30401    23880622+   5  Extended
/dev/sda3           30273       30401     1036161   82  Linux swap / Solaris
/dev/sda5           27429       30272    22844367   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd224d224

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7774    62444623+   7  HPFS/NTFS
/dev/sdb2            7775        9729    15703537+   5  Extended
/dev/sdb5            9642        9729      706828+  82  Linux swap / Solaris
/dev/sdb6            7775        9641    14996614+  83  Linux

Partition table entries are not in disk order
```

---

### Post by bneva on 2010-05-02
> **Animal X said:**
> before you do anything, can you show us a copy of your menu.lst ?

sorry didn't see your post.

The windows part is what I put in myself

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
# kopt=root=UUID=5c8379f7-9236-4956-8b60-17369df3c662 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5c8379f7-9236-4956-8b60-17369df3c662

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		5c8379f7-9236-4956-8b60-17369df3c662
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=5c8379f7-9236-4956-8b60-17369df3c662 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		5c8379f7-9236-4956-8b60-17369df3c662
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=5c8379f7-9236-4956-8b60-17369df3c662 ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid		5c8379f7-9236-4956-8b60-17369df3c662
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=5c8379f7-9236-4956-8b60-17369df3c662 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		5c8379f7-9236-4956-8b60-17369df3c662
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=5c8379f7-9236-4956-8b60-17369df3c662 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid		5c8379f7-9236-4956-8b60-17369df3c662
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=5c8379f7-9236-4956-8b60-17369df3c662 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid		5c8379f7-9236-4956-8b60-17369df3c662
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=5c8379f7-9236-4956-8b60-17369df3c662 ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		5c8379f7-9236-4956-8b60-17369df3c662
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Windows XP
root		(hd1,0)


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
#title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda5)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa #ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-15-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
#title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda5)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa #ro single 
#initrd		/boot/initrd.img-2.6.28-15-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
#title		Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda5)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa #ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-13-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
#title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda5)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa #ro single 
#initrd		/boot/initrd.img-2.6.28-13-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
#title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa #ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa #ro single 
#initrd		/boot/initrd.img-2.6.28-11-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
#title		Ubuntu 9.04, kernel 2.6.27-11-generic (on /dev/sda5)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa #ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-11-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
#title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda5)
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=279a4161-3118-4204-8992-37912d668ffa #ro single 
#initrd		/boot/initrd.img-2.6.27-11-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
#title		Ubuntu 9.04, memtest86+ (on /dev/sda5)
#root		(hd0,4)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot

```

---

### Post by Animal X on 2010-05-02
no prob, actually im a noob, but i been through something like this before. Also you're sure that you can see the XP file system intact, right?

To be honest, i use vista, and i always had to use chainloader +1, im not sure that applies to XP

---

### Post by GSF1200S on 2010-05-02
> **bneva said:**
> This was the output of the fdisk command

```
omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb6284573

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27428   220315378+   7  HPFS/NTFS
/dev/sda2           27429       30401    23880622+   5  Extended
/dev/sda3           30273       30401     1036161   82  Linux swap / Solaris
/dev/sda5           27429       30272    22844367   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd224d224

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7774    62444623+   7  HPFS/NTFS
/dev/sdb2            7775        9729    15703537+   5  Extended
/dev/sdb5            9642        9729      706828+  82  Linux swap / Solaris
/dev/sdb6            7775        9641    14996614+  83  Linux

Partition table entries are not in disk order
```

Do you have two hard drives? /dev/sda and /dev/sdb are different devices, so I need to know which one you are using to boot off of. Usually its /dev/sda, but then mine boots from /dev/sdb (which is the second drive recognized as Ubuntu starts). 

In short, which hard drive do you boot from? The block sizes (which roughly equal the total size of each partition) might help you sort out which drive you are using. Let me know.. Should be an easy fix.

---

### Post by Animal X on 2010-05-02
right, well heres mine for reference:

default=1
timeout 9
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message

title MEPIS
root (hd0,1)
kernel /boot/vmlinuz root=/dev/sda2 nomce quiet splash vga=791 
initrd /boot/initrd.img
boot

title Aero
rootnoverify (hd0,0)
chainloader +1

title Ubuntu
root (hd0,4)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=1ae21232-5350-4b69-9a80-f71810532b5f ro xforcevesa quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title MEMTEST
kernel /boot/memtest86+.bin

---

### Post by bneva on 2010-05-02
> **Animal X said:**
> no prob, actually im a noob, but i been through something like this before. Also you're sure that you can see the XP file system intact, right?

To be honest, i use vista, and i always had to use chainloader +1, im not sure that applies to XP

I fixed it by adding the chainloader line!  The noobs prevail....huzzah

> **GSF1200S said:**
> Do you have two hard drives? /dev/sda and /dev/sdb are different devices, so I need to know which one you are using to boot off of. Usually its /dev/sda, but then mine boots from /dev/sdb (which is the second drive recognized as Ubuntu starts). 

In short, which hard drive do you boot from? The block sizes (which roughly equal the total size of each partition) might help you sort out which drive you are using. Let me know.. Should be an easy fix.

Yes sorry I should have mentioned I have 2 HD, I believe my linux partition would be on sdb5 according to that fdisk print out?!?! which would be my first HD.

but the problem is fixed now, thanks everyone for helping

---

### Post by Animal X on 2010-05-02
> **GSF1200S said:**
> Do you have two hard drives? /dev/sda and /dev/sdb are different devices, so I need to know which one you are using to boot off of. Usually its /dev/sda, but then mine boots from /dev/sdb (which is the second drive recognized as Ubuntu starts). 

In short, which hard drive do you boot from? The block sizes (which roughly equal the total size of each partition) might help you sort out which drive you are using. Let me know.. Should be an easy fix.



good point, maybe a blkid command could be useful here?

---

### Post by Animal X on 2010-05-02
Awesome, glad to see it work. Peace.

---

### Post by Animal X on 2010-05-02
goofed up my edit, nm this, lol

---

