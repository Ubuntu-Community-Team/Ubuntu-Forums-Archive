---
title: "Grub questions"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-03-30
I have a question how do i go about getting rid of the older (I now have three different ones the original load and 2 others).  I just want to reclaim the space if they are not needed.  What i would do is drop the oldest and keep the two new kernals.
this is the one that i want to drop "Ubuntu 8.10, kernel 2.6.27-7-generic"
below is  the menu.lst

trinidad

****************************************************************************
****************************************************************************
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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color light-red/blue white/blue

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
# kopt=root=UUID=5e0ca782-03c1-4d00-8530-37825ddd9f3c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5e0ca782-03c1-4d00-8530-37825ddd9f3c

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
# defoptions=splash vga=792

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		5e0ca782-03c1-4d00-8530-37825ddd9f3c
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=5e0ca782-03c1-4d00-8530-37825ddd9f3c ro splash vga=792 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		5e0ca782-03c1-4d00-8530-37825ddd9f3c
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=5e0ca782-03c1-4d00-8530-37825ddd9f3c ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		5e0ca782-03c1-4d00-8530-37825ddd9f3c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5e0ca782-03c1-4d00-8530-37825ddd9f3c ro splash vga=792 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		5e0ca782-03c1-4d00-8530-37825ddd9f3c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5e0ca782-03c1-4d00-8530-37825ddd9f3c ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5e0ca782-03c1-4d00-8530-37825ddd9f3c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5e0ca782-03c1-4d00-8530-37825ddd9f3c ro splash vga=792 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5e0ca782-03c1-4d00-8530-37825ddd9f3c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5e0ca782-03c1-4d00-8530-37825ddd9f3c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5e0ca782-03c1-4d00-8530-37825ddd9f3c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST```

```

---

### Post by 73ckn797 on 2009-03-30
You should be able to uninstall the older kernels using Synaptic Package Manager. That would completely delete anything related to those versions. You could also comment out those entries in grub menu.lst using "#" at the front of each line pertaining to that kernel.

I do not think you will gain very much space. Look at the size of the kernel files in /boot. I do not know where other related files would be found, that is why Synaptic would be the most thorough remedy.

---

### Post by drs305 on 2009-03-30
73ckn797's reply about removing older kernels via synaptic is the 'cleanest' way although the others work as well. It's probably best to keep at least one older working kernel in case something breaks.

A while back I wrote a guide on this topic. It's still referenced in my signature line - the one about StartUp-Manager. It explains your options both via a gui tool called StartUp-Manager as well as some tips if you choose to edit grub manually.

---

### Post by vegetarianshrimp on 2009-03-30
hope this will help:
[http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html](http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html)

---

### Post by trinidadflores on 2009-03-30
> **73ckn797 said:**
> You should be able to uninstall the older kernels using Synaptic Package Manager. That would completely delete anything related to those versions. You could also comment out those entries in grub menu.lst using "#" at the front of each line pertaining to that kernel.

I do not think you will gain very much space. Look at the size of the kernel files in /boot. I do not know where other related files would be found, that is why Synaptic would be the most thorough remedy.

Going  through Synaptic wont mess up the grub right?

---

### Post by drs305 on 2009-03-30
> **trinidadflores said:**
> Going  through Synaptic wont mess up the grub right?

You can use synaptic to safely remove kernels. Look for linux-image.. and then the kernels you want to remove. Example: linux-image-2.6.27-7-generic. You can check the kernel you are currently using with:
```
uname -r
```
Synaptic won't let you remove the kernel in use, but it's still better to know which one you don't want to remove. You can also remove the modules and headers of the kernels you remove. More details in the guide I linked to in my signature line.

Using synaptic to remove the older kernels won't mess up your grub menu but will clean it up, removing any kernel entries for kernels you actually remove via synaptic. If you want to back up your menu.lst first:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```

---

### Post by 73ckn797 on 2009-03-30
drs305 has the best detail and info for what I recommended.

---

### Post by trinidadflores on 2009-03-30
thank you all this helped

---

