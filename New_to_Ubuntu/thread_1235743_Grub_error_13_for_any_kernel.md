---
title: "Grub error 13 for any kernel"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by unfoundbug on 2009-08-09
I recently installed ubuntu onto an SD card for my acer aspire. This is so I can keep the card on the left reader safe and not using the abysmal SSD. I can boot ubuntu fine using the SD card in a USB reader, but if I try to start the OS using grub stored on the SSD I get Error 13 from grub. 
I added in the modules to allow grub to read the SD card and copied all the relevant files from the sd card to the ssd.


menu.lst
```
# The backup copy of the MBR for drive '/dev/sda' is
# here '/boot/grub/mbr.sda.22000'.  You can restore it like this.
# dd if=/boot/grub/mbr.sda.22000 of=/dev/sda bs=512 count=1
#
# Start GRUB global section
#timeout 30
color light-gray/blue black/light-gray
gfxmenu /boot/grub/deep_stage1
# End GRUB global section

# Linux bootable partition config begins
  title     Ubuntu 2.8.28-14
  uuid        faa9b183-fff2-4a01-b855-8e982f2ea71f
  kernel     /boot/initrd.img-2.6.28-14-generic root=UUID = faa9b183-fff2-4a01-b855-8e982f2ea71f ro quiet splash
  initrd     /boot/initrd.img-2.6.28-14-generic
  chainloader +1
# Linux bootable partition config ends
 #Linux bootable partition config begins
  title     Ubuntu 2.8.28-13
  uuid        faa9b183-fff2-4a01-b855-8e982f2ea71f
  kernel     /boot/initrd.img-2.6.28-13-generic root=UUID = faa9b183-fff2-4a01-b855-8e982f2ea71f ro quiet splash
  initrd     /boot/initrd.img-2.6.28-13-generic
  chainloader +1
# Linux bootable partition config ends
#Linux bootable partition config begins
  title     Ubuntu 2.8.28-11
  uuid        faa9b183-fff2-4a01-b855-8e982f2ea71f
  kernel     /boot/initrd.img-2.6.28-11-generic root=UUID = faa9b183-fff2-4a01-b855-8e982f2ea71f ro quiet splash
  initrd     /boot/initrd.img-2.6.28-11-generic
  chainloader +1
# Linux bootable partition config ends



# Linux bootable partition config begins
  title Linux (on /dev/sda1)
  root (hd0,0)
  kernel /boot/vmlinuz root=/dev/sda1 ro vga=771
# Linux bootable partition config ends
```

---

### Post by unfoundbug on 2009-08-10
I just tried reinstalling grub, to no avail, and will now remove and reinstall the relevant kernels

---

### Post by teh603 on 2009-08-10
If I remember right, don't most AAOs not support boot from either SD card reader?

---

### Post by unfoundbug on 2009-08-11
I have read on the internet that it is actually possible. I'm also not booting from the SD card directly. GRUB is located on the internal SSD drive of the netbook. Once grub has loaded, I am trying to get it to use the kernal stored on the SD card.

---

### Post by teh603 on 2009-08-11
Hm... don't know how to do that.

You're sure you'll get better performance from using an SD card in the reader than the internal SSD, though? I've got an eeePC that boots off an SD card and its slower'n molasses.

---

### Post by unfoundbug on 2009-08-11
edit:remove

---

### Post by unfoundbug on 2009-08-11
Issue Solved

```

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		faa9b183-fff2-4a01-b855-8e982f2ea71f
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=faa9b183-fff2-4a01-b855-8e982f2ea71f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

```



New menu.lst
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
# kopt=root=UUID=faa9b183-fff2-4a01-b855-8e982f2ea71f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=faa9b183-fff2-4a01-b855-8e982f2ea71f

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		faa9b183-fff2-4a01-b855-8e982f2ea71f
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=faa9b183-fff2-4a01-b855-8e982f2ea71f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		faa9b183-fff2-4a01-b855-8e982f2ea71f
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=faa9b183-fff2-4a01-b855-8e982f2ea71f ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		faa9b183-fff2-4a01-b855-8e982f2ea71f
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=faa9b183-fff2-4a01-b855-8e982f2ea71f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		faa9b183-fff2-4a01-b855-8e982f2ea71f
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=faa9b183-fff2-4a01-b855-8e982f2ea71f ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		faa9b183-fff2-4a01-b855-8e982f2ea71f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=faa9b183-fff2-4a01-b855-8e982f2ea71f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		faa9b183-fff2-4a01-b855-8e982f2ea71f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=faa9b183-fff2-4a01-b855-8e982f2ea71f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		faa9b183-fff2-4a01-b855-8e982f2ea71f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```


Guide: [http://theadmin.co.uk/?p=54](http://theadmin.co.uk/?p=54)

---

