---
title: "Error while parsing number"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by HolySpagetty on 2008-12-30
Hello, (again..)

I have successfully installed XP on a seperate drive when all of a sudden when I try to boot XP for the first time after loading it to the Grub Boot Menu, I get an Error. I thought this would be the best place to put it.

My menu.lst shows as follows

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
timeout		3

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
# kopt=root=UUID=126aacd9-472e-4bdc-9608-a1707d41f5f3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=126aacd9-472e-4bdc-9608-a1707d41f5f3

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		126aacd9-472e-4bdc-9608-a1707d41f5f3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=126aacd9-472e-4bdc-9608-a1707d41f5f3 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		126aacd9-472e-4bdc-9608-a1707d41f5f3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=126aacd9-472e-4bdc-9608-a1707d41f5f3 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		126aacd9-472e-4bdc-9608-a1707d41f5f3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=126aacd9-472e-4bdc-9608-a1707d41f5f3 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		126aacd9-472e-4bdc-9608-a1707d41f5f3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=126aacd9-472e-4bdc-9608-a1707d41f5f3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		126aacd9-472e-4bdc-9608-a1707d41f5f3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title 		Windows XP
root 		(hdo,1)
savedefault
makeactive
chainloader 	+1

```

Please help. I just want to use my XP!!

Thanks in advance to everyone that helps.

---

### Post by HolySpagetty on 2008-12-30
Can someone please help??

I really need to get on my XP! :(

---

### Post by Malalo on 2008-12-30
Well, first strange thing I noticed is that the file states that your WinXP is on hdo instead of hd0...

---

### Post by HolySpagetty on 2008-12-30
Well golly. Look at that.

Sorry guys. Operator Error!

I will check back to see if it works right after.. :D

---

### Post by HolySpagetty on 2008-12-30
Thanks a lot. It works now.

Now it is the job of getting all of my drivers to work on XP x64!

Looks like a challenge to me!

:KS to Malalo!

---

### Post by Malalo on 2008-12-30
> **HolySpagetty said:**
> Operator Error!

Naaah it's just a typo, everyone does them... Glad to see it works !
Good luck with your Vista x64 drivers !

---

