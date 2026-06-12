---
title: "[SOLVED] menu.1st editing"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Java Geek on 2009-01-04
When I boot, there are now 8 os's to pick from. I have XUBUNTU 8.04 and Windows XP. How would I remove all but the first 2 XUBUNTU boot options?

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=7ee66b8a-c8a1-4fba-a905-6c1f0bc13f52 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=7ee66b8a-c8a1-4fba-a905-6c1f0bc13f52 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=7ee66b8a-c8a1-4fba-a905-6c1f0bc13f52 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=7ee66b8a-c8a1-4fba-a905-6c1f0bc13f52 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7ee66b8a-c8a1-4fba-a905-6c1f0bc13f52 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7ee66b8a-c8a1-4fba-a905-6c1f0bc13f52 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by kestrel1 on 2009-01-04
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkup

sudo gedit /boot/grub/menu.lst
```
remove what you don't need.

---

### Post by Elfy on 2009-01-04
You can either edit the file as root

```
gksu mousepad /boot/grub/menu.lst
``` small L not a 1

OR remove the older kernels with the package management, which will also updat egrub - not sure in xubuntu but synaptic in ubuntu - search for linux-image

Keep at least the 2 newer kernels.

---

### Post by kansasnoob on 2009-01-04
Install startupmanager either from synaptic or:

```
sudo apt-get install startupmanager
```

Then find it in System > Administration > .....

[ATTACH]98713[/ATTACH]

Under the advanced tab tick on "limit # of kernels" and change the "number" to 2!

---

### Post by jamesrl on 2009-01-04
Here's my /boot/grub/menu.lst (its list not 1st):

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
# kopt=root=UUID=997e4050-1640-4377-934e-ac34d3d71de3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=997e4050-1640-4377-934e-ac34d3d71de3

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		997e4050-1640-4377-934e-ac34d3d71de3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=997e4050-1640-4377-934e-ac34d3d71de3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		997e4050-1640-4377-934e-ac34d3d71de3
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=997e4050-1640-4377-934e-ac34d3d71de3 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		997e4050-1640-4377-934e-ac34d3d71de3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=997e4050-1640-4377-934e-ac34d3d71de3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		997e4050-1640-4377-934e-ac34d3d71de3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=997e4050-1640-4377-934e-ac34d3d71de3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		997e4050-1640-4377-934e-ac34d3d71de3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-rt (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=ea5cdba4-e855-42db-80e3-ad6f75c856a5 ro 
initrd		/boot/initrd.img-2.6.24-21-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-rt (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=ea5cdba4-e855-42db-80e3-ad6f75c856a5 ro single 
initrd		/boot/initrd.img-2.6.24-21-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ea5cdba4-e855-42db-80e3-ad6f75c856a5 ro 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ea5cdba4-e855-42db-80e3-ad6f75c856a5 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-20-rt (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-20-rt root=UUID=ea5cdba4-e855-42db-80e3-ad6f75c856a5 ro 
initrd		/boot/initrd.img-2.6.24-20-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-20-rt (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-20-rt root=UUID=ea5cdba4-e855-42db-80e3-ad6f75c856a5 ro single 
initrd		/boot/initrd.img-2.6.24-20-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=ea5cdba4-e855-42db-80e3-ad6f75c856a5 ro 
initrd		/boot/initrd.img-2.6.24-20-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=ea5cdba4-e855-42db-80e3-ad6f75c856a5 ro single 
initrd		/boot/initrd.img-2.6.24-20-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

```
If you scroll down to the settings in the automagic kernel section, you see there's a line in mine that says:
# howmany=all
and you probably want to change it to
# howmany=2
(Edit the file by say typing gksudo [S]gedit[/S] mousepad /boot/grub/menu.lst ).
You then have to rerun update-grub by typing
sudo update-grub
You can manually also manually edit menu.list (as described by other posters), but then each time there's a kernel update, you will have to manually reedit again.

Also note howmany=2 will give you 2 kernels (and hence four lines in grub if each kernel has its own recovery mode).  So you might want # howmany=1, however I'd personally keep 2.  [If you don't like having to scroll down for windows you can move the windows section above the automagic kernel part (not in it), and then change the default that it boots to, to be the 2nd option with default = 1

EDIT: Forgot you said you are in xubuntu.  Replace gedit with mousepad (a graphical xcfe editor).

---

### Post by ranch hand on 2009-01-04
gksudo gedit is safer than sudo gedit.

You might also want to just comment out the unused versions to make sure it works right.  You can remove them later if all is well.  I would remove the old kernals before editing them out of your file.

---

### Post by Elfy on 2009-01-04
gksudo gedit is better indeed but unlikely to work on xubuntu unless it's been installed

removing the kernels should trigger update-grub which will remove them from the list

---

