---
title: "Cant find ubuntu in boot list after reinstalling vista"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by pardesi on 2010-08-12
I reinstalled vista in presence of ubuntu in the same partition in which vista existed before. Now when i use live cd and try to do 
```
sudo grub
root (hd0,0)
setup (hd0)
```
i get 
```

Error 17: Cannot mount selected partition

```

the output of 
```

sudo fdisk -l

```
is 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd186522b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9726    78124063+   5  Extended
/dev/sda2   *       11747       18704    55890135    7  HPFS/NTFS
/dev/sda3           18705       19457     6048472+  82  Linux swap / Solaris
/dev/sda5               1        4255    34178224+  83  Linux
/dev/sda6            4256        9726    43945776   83  Linux

```

and 
```

cat /media/disk//boot/grub/menu.lst

```
gives
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=c23588df-be1c-4eb5-8c01-75ecb1c60b38 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c23588df-be1c-4eb5-8c01-75ecb1c60b38

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		c23588df-be1c-4eb5-8c01-75ecb1c60b38
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=c23588df-be1c-4eb5-8c01-75ecb1c60b38 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		c23588df-be1c-4eb5-8c01-75ecb1c60b38
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=c23588df-be1c-4eb5-8c01-75ecb1c60b38 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		c23588df-be1c-4eb5-8c01-75ecb1c60b38
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=c23588df-be1c-4eb5-8c01-75ecb1c60b38 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		c23588df-be1c-4eb5-8c01-75ecb1c60b38
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=c23588df-be1c-4eb5-8c01-75ecb1c60b38 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		c23588df-be1c-4eb5-8c01-75ecb1c60b38
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c23588df-be1c-4eb5-8c01-75ecb1c60b38 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		c23588df-be1c-4eb5-8c01-75ecb1c60b38
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c23588df-be1c-4eb5-8c01-75ecb1c60b38 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		c23588df-be1c-4eb5-8c01-75ecb1c60b38
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c23588df-be1c-4eb5-8c01-75ecb1c60b38 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		c23588df-be1c-4eb5-8c01-75ecb1c60b38
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c23588df-be1c-4eb5-8c01-75ecb1c60b38 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		c23588df-be1c-4eb5-8c01-75ecb1c60b38
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c23588df-be1c-4eb5-8c01-75ecb1c60b38 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		c23588df-be1c-4eb5-8c01-75ecb1c60b38
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c23588df-be1c-4eb5-8c01-75ecb1c60b38 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c23588df-be1c-4eb5-8c01-75ecb1c60b38
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```
Please help me out.

---

### Post by mikewhatever on 2010-08-12
Well, Ubuntu is obviously not on (hd0,0), but either on (hd0,4) or (hd0,5). Use the correct values in 'root (hdX,Y)'.

---

