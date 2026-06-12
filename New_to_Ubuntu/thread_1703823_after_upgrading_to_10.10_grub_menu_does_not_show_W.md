---
title: "after upgrading to 10.10 grub menu does not show Windows XP"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by yygyt on 2011-03-09
Here is the output of **sudo fdisk -l**

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfa0b0568

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sda2            9562       19457    79489620    5  Extended
/dev/sda5            9562       19048    76204296   83  Linux
/dev/sda6           19049       19457     3285261   82  Linux swap / Solaris

```

and here is my **menu.lst** file(I added #'s for the obsolete kernels on purpose)

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
# kopt=root=UUID=475aed4c-3f9b-4422-865a-8693ddcf87a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=475aed4c-3f9b-4422-865a-8693ddcf87a5

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

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		475aed4c-3f9b-4422-865a-8693ddcf87a5
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=475aed4c-3f9b-4422-865a-8693ddcf87a5 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		475aed4c-3f9b-4422-865a-8693ddcf87a5
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=475aed4c-3f9b-4422-865a-8693ddcf87a5 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

#title		Ubuntu 10.10, kernel 2.6.32-25-generic
#uuid		475aed4c-3f9b-4422-865a-8693ddcf87a5
#kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=475aed4c-3f9b-4422-865a-8693ddcf87a5 ro quiet splash 
#initrd		/boot/initrd.img-2.6.32-25-generic
#quiet

#title		Ubuntu 10.10, kernel 2.6.32-25-generic (recovery mode)
#uuid		475aed4c-3f9b-4422-865a-8693ddcf87a5
#kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=475aed4c-3f9b-4422-865a-8693ddcf87a5 ro  single
#initrd		/boot/initrd.img-2.6.32-25-generic

#title		Ubuntu 10.10, kernel 2.6.31-20-generic
#uuid		475aed4c-3f9b-4422-865a-8693ddcf87a5
#kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=475aed4c-3f9b-4422-865a-8693ddcf87a5 ro quiet splash 
#initrd		/boot/initrd.img-2.6.31-20-generic
#quiet

#title		Ubuntu 10.10, kernel 2.6.31-20-generic (recovery mode)
#uuid		475aed4c-3f9b-4422-865a-8693ddcf87a5
#kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=475aed4c-3f9b-4422-865a-8693ddcf87a5 ro  single
#initrd		/boot/initrd.img-2.6.31-20-generic

#title		Ubuntu 10.10, kernel 2.6.28-11-generic
#uuid		475aed4c-3f9b-4422-865a-8693ddcf87a5
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=475aed4c-3f9b-4422-865a-8693ddcf87a5 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 10.10, kernel 2.6.28-11-generic (recovery mode)
#uuid		475aed4c-3f9b-4422-865a-8693ddcf87a5
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=475aed4c-3f9b-4422-865a-8693ddcf87a5 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

#title		Ubuntu 10.10, memtest86+
#uuid		475aed4c-3f9b-4422-865a-8693ddcf87a5
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by Foxheadz on 2011-03-09
Have you tried just running ```
sudo update-grub
```?

---

### Post by yygyt on 2011-03-09
> **Foxheadz said:**
> Have you tried just running ```
sudo update-grub
```?

I just tried and nothing changed. I suppose I need to add that partition to the menu manually but I do not know how.

---

### Post by yygyt on 2011-03-09
Any suggestions?

---

### Post by yygyt on 2011-03-09
I didn't understand completely but adding the following lines solved my problem.

title           Windows XP Professional
root            (hd0,0)
makeactive
chainloader     +1

---

### Post by pistachepastis on 2011-05-02
this worked for me yygyt!
thanks!

---

