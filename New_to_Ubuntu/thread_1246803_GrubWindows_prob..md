---
title: "Grub/Windows prob."
date: 2009-08-22
forum: New to Ubuntu
---

### Post by Paul T. on 2009-08-22
I've had to re-install Windowz XP (on top of existing installation) because of a 'hal.dll' error, Windowz now works fine and the dual boot option is still present, however if I try to boot into Ubuntu I get a "Windows cannot start because hal.dll is missing or corrupt" error. :confused:

---

### Post by j7%&lt;RmUg on 2009-08-22
Im assuming that you have 2 hard drives, one with ubuntu and one with windows on it.

Try disconnecting the power and data cables from your windows drive and then try booting into ubuntu, if you manage to boot ubuntu then your windows drive is the problem.

Also have you installed ubuntu inside windows, on a separate partition but on the same drive or on a seperate hard drive?

---

### Post by Penguin Guy on 2009-08-22
Boot into your Ubuntu Live CD.
Firstly; try and locate your Linux installation (it should be in the 'Places' menu named something like '100GB Media'). Once you've found linux find the /boot/grub/menu.lst file and paste it into here.
Secondly run the command [COLOR="Green"]sudo fdisk -l[/COLOR] and post the results back here.

Hopefully this will give us a little more information about what could have gone wrong.

---

### Post by Paul T. on 2009-08-23
[B]Hi,
should have mentioned that I have full install of Ubuntu in seperate partition on my 'C' drive.

Contents of menu.lst file:[/B]

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
# kopt=root=UUID=9790908d-e8a0-4820-b269-62da8adb6ebb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9790908d-e8a0-4820-b269-62da8adb6ebb

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


title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		9790908d-e8a0-4820-b269-62da8adb6ebb
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=9790908d-e8a0-4820-b269-62da8adb6ebb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		9790908d-e8a0-4820-b269-62da8adb6ebb
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=9790908d-e8a0-4820-b269-62da8adb6ebb ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		9790908d-e8a0-4820-b269-62da8adb6ebb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9790908d-e8a0-4820-b269-62da8adb6ebb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		9790908d-e8a0-4820-b269-62da8adb6ebb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9790908d-e8a0-4820-b269-62da8adb6ebb ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		9790908d-e8a0-4820-b269-62da8adb6ebb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


**sudo fdisk -l:**

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10d99b60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11151    89570376    7  HPFS/NTFS
/dev/sda2           11152       30401   154625625    f  W95 Ext'd (LBA)
/dev/sda5           11152       30009   151476853+  83  Linux
/dev/sda6           30010       30401     3148708+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90a890a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS


**Also if it's of help, here is contents of Windows boot.ini file:**

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=optin

C:\wubildr.mbr="Ubuntu" 


**Appreciate your help** :P

---

### Post by Paul T. on 2009-08-23
Just to add to my confusion:

"grub> find /boot/grub/stage1
 (hd0,4)"

but fdisk says:

/dev/sda5 11152 30009 151476853+ 83 Linux


Is grub on 4 or 5?

---

### Post by Elfy on 2009-08-23
grub counts from 0 - so sda5 is 0,4

---

### Post by Paul T. on 2009-08-24
*Bump*

Still trying to solve this prob, anyone help me please?

---

### Post by bumanie on 2009-08-24
Boot live cd and in terminal type > sudo grub > root (hd0,4) > setup (hd0) > quit Reboot and grub should work again. Note: As forestpixie said, (hd0,4) is the same as /dev/sda5 - grub counts from zero, sda counts from one.

---

### Post by Paul T. on 2009-08-24
Sorted!
Many thx bumanie :P

---

### Post by LewRockwell on 2009-08-24
> **Paul T. said:**
> *Bump*

Still trying to solve this prob, anyone help me please?

We must have missed where anyone recommended the Super Grub Disk

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

