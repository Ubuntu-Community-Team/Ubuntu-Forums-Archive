---
title: "Ubuntu appears twice in GRUB"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by ROKtUS on 2009-01-04
Hello.
I have installed ubuntu (dual boot with vista 64 bit) and am using it for everything now! However, I have a problem with my GRUB. I uninstalled Ubuntu once, because it drove me crazy in the beginning. However, I chose to try again and installed it again. The only problem is that Ubuntu appears twice in Grub

It looks like this:
Microsoft Windows Vista
Ubuntu
Ubuntu

Is there a way i can delete one of the Ubuntus? Both Ubuntus lead to the same thing. Another menu with the same Ubuntu variations.
Thank you,

ROKtUS

---

### Post by Elfy on 2009-01-04
Can you post it here and your partitions just to check - but if you've had kernel updates then that would account for it.

```
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by jimmy the saint on 2009-01-04
One should be the standard Ubuntu session and the other should be recovery mode.  When the kernel gets updated you will also see additional grub entries.  Typically the first instance of Ubuntu will be the one that you want.

---

### Post by ROKtUS on 2009-01-05
forest:
here it is.
j@ubuntu:~$ cat /boot/grub/menu.lst
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
timeout		1

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
# kopt=root=UUID=59976EEC7DAFF567 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
# howmany=1

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=59976EEC7DAFF567 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=59976EEC7DAFF567 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1

j@ubuntu:~$ sudo fdisk -l
[sudo] password for j: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2cb52aee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28726   230741563+   7  HPFS/NTFS
/dev/sda2           28727       30401    13454437+   7  HPFS/NTFS

---

### Post by northern lights on 2009-01-05
> **ROKtUS said:**
> ## ## End Default Options ##

title		[COLOR="Red"]Ubuntu 8.10, kernel 2.6.27-9-generic[/COLOR]
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=59976EEC7DAFF567 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		[COLOR="Red"]Ubuntu 8.10, kernel 2.6.27-9-generic (_recovery mode_)[/COLOR]
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=59976EEC7DAFF567 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		[COLOR="Red"]Ubuntu 8.10, _memtest86+_[/COLOR]
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

These are not the same entries. The second is recovery mode and the third memtest mode. Your GRUB menu shows this upon boot though. You could remove the additional modes by editing the above file, but, at least in the case of the Recovery Mode entry, that'd be not very recommendable. In fact rather ill-decided.

After your first kernel update these will even double.

So what, though?! How long do you actually see GRUB?

---

### Post by Bölvaður on 2009-01-05
> **ROKtUS said:**
> 
It looks like this:
Microsoft Windows Vista
Ubuntu
Ubuntu

It looks like as if you used the wubi installer on windows, that will not make grub the boot loader as the above posters are assuming. If you did not use wubi but did a normal installation from live cd then you have GRUB as a boot loader that would look like this (taken from your grub file):

> Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, memtest86+
Other operating systems:
Windows Vista/Longhorn (loader)
Windows Vista/Longhorn (loader)


It is very easy to fix the grub.

just run it with super user rights, read the file to understand how it works and change it. very simple if you just read it over.
```

gksudo gedit /boot/grub/menu.lst
```

---

### Post by hamofgrey on 2009-01-05
If you want a simple GUI solution to the problem install KGRUBEditor using Add/Remove Programs. Simply then remove whatever option as a selection.

Or if you google the problem, this is a good HOW-TO guide.

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

---

