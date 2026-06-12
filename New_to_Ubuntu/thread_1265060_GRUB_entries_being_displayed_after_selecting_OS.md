---
title: "GRUB entries being displayed after selecting OS"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by kinston on 2009-09-12
I restored an Ubuntu image from Clonezilla that works as expected. I did notice one thing though.  When GRUB auto-selects the default entry I get the following:

Booting 'Ubuntu 8.04.3 LTS, kernel 2.6.24-2-generic'

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel  /boot/vmlinuz-2.6.24-24-generic root=UUID=(UUID info)
fcd6b0e ro quiet splash
 [Linux-bzImage, setup=0x2a00, size=0X1d3678]
initrd /boot/initrd.img-2.6.24-23-generic
 [Linux-initrd @ 0x1f8c8000, 0x7279cf bytes]

After this is displayed Ubuntu loads fine.  A similar screen is shown for every entry selected in the GRUB menu.  Is there a way for me to hide that information?

---

### Post by izziere on 2009-09-13
Can you post the contents of /boot/grub/menu.lst here?

Are there any relevant errors occurring in dmesg (or you can browse through /var/log/syslog)?

---

### Post by kinston on 2009-09-13
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
# kopt=root=UUID=1405f68a-71d8-41a9-8461-f3fbdfcd6b0e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=1405f68a-71d8-41a9-8461-f3fbdfcd6b0e ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=1405f68a-71d8-41a9-8461-f3fbdfcd6b0e ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1405f68a-71d8-41a9-8461-f3fbdfcd6b0e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1405f68a-71d8-41a9-8461-f3fbdfcd6b0e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
[B]
SYSLOG Errors[/B]
Sep 13 00:59:12 ubuntu-test kernel: [   12.248400] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[B]
DMESG[/B]
Same as in the syslog
[   12.248281] ACPI: Core revision 20070126
[   12.248400] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.248991] ACPI: setting ELCR to 0200 (from 0e20)


Thank You

---

