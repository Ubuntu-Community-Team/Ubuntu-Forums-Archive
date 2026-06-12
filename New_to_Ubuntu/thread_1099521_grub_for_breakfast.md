---
title: "grub for breakfast"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-03-18
Last night I reinstalled windows but to a smaller partition and then turned the rest of what used to be my windows partition into a storage drive for linux. enclosed is a snapshot of what my partitions look like.  But the reason why i am submitting this post is i now cannot get to my linux partition and i am currently running my live disk.  

How do i get my ubuntu install back...without reinstalling it?

---

### Post by taurus on 2009-03-18
When you reinstalled windows, it wiped out GRUB so you need to reinstall it again if you want to boot Ubuntu & windows.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by trinidadflores on 2009-03-18
> **taurus said:**
> When you reinstalled windows, it wiped out GRUB so you need to reinstall it again if you want to boot Ubuntu & windows.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I have a question.  I followed the steps found on the above link.  That worked, but now it shows 2 entries for the ubuntu install.  How do i get it so that it only shows 1 and the 1 recovery partition.  I have enclosed the following text file.

The first of which is the menu.lst file.

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
# kopt=root=UUID=4597837b-e3e2-4032-8b0f-f8703570d33d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4597837b-e3e2-4032-8b0f-f8703570d33d

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		4597837b-e3e2-4032-8b0f-f8703570d33d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4597837b-e3e2-4032-8b0f-f8703570d33d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		4597837b-e3e2-4032-8b0f-f8703570d33d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4597837b-e3e2-4032-8b0f-f8703570d33d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4597837b-e3e2-4032-8b0f-f8703570d33d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4597837b-e3e2-4032-8b0f-f8703570d33d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4597837b-e3e2-4032-8b0f-f8703570d33d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4597837b-e3e2-4032-8b0f-f8703570d33d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4597837b-e3e2-4032-8b0f-f8703570d33d
kernel		/boot/memtest86+.bin
quiet

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
makeactive
chainloader	+1

---

### Post by kansasnoob on 2009-03-18
IMHO just install startupmanager either from synaptic or go to terminal and:

```
sudo apt-get install startupmanager
```

It'll then show up in System > Administration >

If you click on the advanced tab you can tick on "limit number of kernels" and select "1".  

**Note: every time there is a kernel update I'd change that temporarily to "2" until you're sure the new kernel boots OK!**

A bit more here:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

Oh, you can also "de-select" the memtest option! How often do you use that?

---

### Post by trinidadflores on 2009-03-18
this worked thank you.

---

