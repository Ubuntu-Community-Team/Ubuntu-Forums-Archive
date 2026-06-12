---
title: "Default startup list"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by meddyliol on 2009-02-28
How can I get my PC to auto startup in Windows XP instead of Ubuntu? I am configuring my Son's PC and he would like it to start in Windows until he gets used to Ubuntu.

I hope this makes sense.

Thanks

Brian :guitar:

---

### Post by rraj.be on 2009-02-28
You just want to edit your Grub File to change this sequence.

try this

```
sudo gedit /boot/grub/menu.lst
```

ths will show a text file like this

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
default		4

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
# kopt=root=UUID=4588e65e-b92a-4761-b74b-c36ec54691b7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,8)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=4588e65e-b92a-4761-b74b-c36ec54691b7 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,8)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=4588e65e-b92a-4761-b74b-c36ec54691b7 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,8)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```


In this change the file so that the windows boot loader comes to the top before any other operating systems like this

```


title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,8)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=4588e65e-b92a-4761-b74b-c36ec54691b7 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,8)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=4588e65e-b92a-4761-b74b-c36ec54691b7 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,8)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1


```


In the above code i have pasted only what is necessary ., . .. i have deleted all other unwanted stuffs there..


You can also change the timeout value to small value in the same file if required.

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10


```

to 

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3


```




There is a GUI tool known as startup-manager available for these things.

you can install that by typing this in the terminal

```
sudo apt-get install startupmanager
```

This start up manager has many additional GUI features to added upon stuffs related to Startup

---

### Post by meddyliol on 2009-02-28
Brilliant, I knew someone would have the answer. I personally think Linux is excellent and I will never go back to Microsoft. I just hope my son will think the same.

Thanks again

Brian :popcorn:

---

### Post by rraj.be on 2009-02-28
You are always welcomed. . .

:) And Linux always RockZ :)

---

