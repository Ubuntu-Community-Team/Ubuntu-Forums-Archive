---
title: "Error 13 when trying to load W7 i dualboot with 9.04"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by madsc89 on 2009-06-23
Hi. I am running dual boot with Ubuntu 9.04 and Windows 7 on a single SSD. I installed W7 first, then Ubuntu. W7 worked for several days, but now, suddenly, it doesn't. I suspect it to be a result of me tweaking ext4 on my Ubuntu partition. I've added noatime, removed (and tried to replace journal) and some other things. When I now try to choose Windows in the grub menu, I get "error 13: invalid or unsupported executable format".

I've searched for an answer, but to no avail. 
This is my /boot/grub/menu.lst
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
# kopt=root=UUID=ae838f82-e996-4e61-a45e-7af452d49762 ro elevator=deadline

## default grub root device
## e.g. groot=(hd0,0)
# groot=ae838f82-e996-4e61-a45e-7af452d49762

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
uuid		ae838f82-e996-4e61-a45e-7af452d49762
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=ae838f82-e996-4e61-a45e-7af452d49762 ro elevator=deadline quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		ae838f82-e996-4e61-a45e-7af452d49762
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=ae838f82-e996-4e61-a45e-7af452d49762 ro elevator=deadline  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		ae838f82-e996-4e61-a45e-7af452d49762
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ae838f82-e996-4e61-a45e-7af452d49762 ro elevator=deadline quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		ae838f82-e996-4e61-a45e-7af452d49762
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ae838f82-e996-4e61-a45e-7af452d49762 ro elevator=deadline  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		ae838f82-e996-4e61-a45e-7af452d49762
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
rootnoverify	(hd0,0)
makeactive
chainloader	+1
```

fdisk -l says:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8094fd4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        7917    63488000    7  HPFS/NTFS
/dev/sda3            7918        9729    14554890    5  Extended
/dev/sda5            7918        7947      240943+  82  Linux swap / Solaris
/dev/sda6            7948        9729    14313883+  83  Linux

```
The W7 partition is sda2 (but is the "boot" in sda1?), and Ubuntu is sda6.

Any ideas as how to resolve this problem?
Thank you.

---

### Post by madsc89 on 2009-06-24
Bump. Perhaps an idea of where to look for an answer?

---

### Post by Don1500 on 2009-06-24
Try changeing this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
rootnoverify	(hd0,1)  <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
makeactive
chainloader	+1

It may not work, but it won't hurt and you can change it back real easy.

---

### Post by madsc89 on 2009-06-24
Thank you. Perhaps some progress? Now it said "BOOTMGR missing    press CTR+ALT+DEL to restart".
Either the problem is replaced with another, or I've added an additional one.

Any further suggestions?

EDIT: With hdo,2, I got Error 12: Invalid device

EDIT2: It seems that this is a well known Vista -issue (I've got W7, but it's pretty much the same!?). I'll try fixing it with the Windows DVD, if you haven't got another idea. I would think I am going to have to repair grub after that?

---

### Post by presence1960 on 2009-06-24
windows 7 needs to boot from sda1 which should be labeled System Reserved. so your (hd0,0) is correct.

this from a page on GRUB errors: 13 : "Inconsistent filesystem structure"

This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.

Try restoring GRUB, if that does not work you may have to use the Win 7 DVD to repair Win 7. After that you may have to restore GRUB again.

---

### Post by madsc89 on 2009-06-24
Thank you for a well explained reply. I tried restoring grub, but it didn't work. Perhaps because of the fact that it recreated grub, still with hd0,5(, while W7 is on hd0,0)? I'll try repairing windows later.

---

