---
title: "messed up installation"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by patchido on 2009-10-19
this is what happend, i used live cd 9.04 to partiocionate my hdd into 3 partitions i had 2 of about 5 gbs, and another partition for what was left of the hdd about 100 gb so, i installed windows xp on one of the 5 gb partitions, and i ran ubuntu installation, and i manually specifyed the partiotion space, and after that everything was a mess, if i run the partiotion editor i get

/dev/sda1/
file system extended 4.87Gib 

then i get sda2 ext2 mount poiint / thats 4.88 its ubuntu flags boot

sda3 linux-swap- 1.91G(i forgot to write that i did this while installing ubuntu, took a long time

and at the end, i get unallocated of 100.12 Gib

what is really strange to me is that at the very top i have another unallocated of 7.84Mib, what is this??

and if i try to edit that partiotion, it tells me that i cannot have nmore the 5 partitions something like it, plz help me, ill post my fstab in case it helps

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65cc02ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2         637     5108670    5  Extended
/dev/sda2   *         638        1274     5116702+  83  Linux
/dev/sda3            1275        1523     2000092+  82  Linux swap / Solaris
/dev/sda5               2         637     5108638+   7  HPFS/NTFS
pato@pato-laptop:~$ 

```

BTW i cant boot into windows from grub, tried to modify it but still wouldnt work

grub menu.lst```
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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=827c5ede-b612-44f8-9151-68efae1c77b6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=827c5ede-b612-44f8-9151-68efae1c77b6

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
uuid		827c5ede-b612-44f8-9151-68efae1c77b6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=827c5ede-b612-44f8-9151-68efae1c77b6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		827c5ede-b612-44f8-9151-68efae1c77b6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=827c5ede-b612-44f8-9151-68efae1c77b6 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		827c5ede-b612-44f8-9151-68efae1c77b6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Guindows Xp
root		(hd0,1)
savedefault
chainloader	+1
```

---

### Post by jrev on 2009-10-19
the best thing you could do is to start again your installation following the rules :)

here it is : [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

hope it helps :P

---

### Post by patchido on 2009-10-19
i still need some guides, what type of format should my document partiotion have?? cause i want to be able to get to it from windows and ubuntu

---

### Post by jrev on 2009-10-19
You can select the ext3 format for your partitions.

You should know that all your documents from windows can be opened and modified under Linux.

Give us some examples and we will tell you how to do

You can run windows & linux on the same computer but you can also switch directly to linux without trouble, apart for your habits that will have to change quicker !*
I have been slow to convert myself because i didn't know I would find a good help here

---

### Post by jrev on 2009-10-19
I see you are not a newcomer !

You can select the ext3 format for your partitions.

You should know that all your documents from windows can be opened and modified under Linux.

Give us some examples and we will tell you how to do

You can run windows & linux on the same computer but you can also switch directly to linux without trouble, apart for your habits that will have to change quicker !

---

### Post by patchido on 2009-10-19
dude, i am not a new user, ive been kind of inactive cause my laptop got broken :P getting back to linux, the problem is that i really need windows beacuse i dont like how my tablet works on gimp, i love how it works in photosop under windows its only for that, but i still want to have it there

---

