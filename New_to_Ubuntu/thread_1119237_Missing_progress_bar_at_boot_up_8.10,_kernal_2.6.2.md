---
title: "Missing progress bar at boot up 8.10, kernal 2.6.27.11"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by CraigJordan on 2009-04-07
After running the update after new install of 8.10, kernal 2.6.27.11-generic
The boot up splash progress bar doesn't display, just a black sceen.
I have checked the menu.lst file for appropriate settings.
I have run the various install updates.
I have installed startup manager and tried various resolutions and color depths.

I notice that sudo update-grub complains that the splash image isn't found yet the image file referenced by the menu.lst file are present and the correct revision as associated to the kernal.

Any help out there for this nubie would be appreciated.

---

### Post by Hospadar on 2009-04-07
What if you point menu.lst at a different splash?

---

### Post by CraigJordan on 2009-04-08
Thanks for your reply Hospadar. I haven't changed the image files in the
/boot directory as it seems update-grub can't seem to see them or is looking in the wrong place. Any idea how to check that.

craig@Sailfish:/boot/grub$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done



Here is a copy of the menu.lst

title           Ubuntu 8.10, kernel 2.6.27-11-generic
uuid            cbdd44df-4a23-4bb2-b12c-51faad434b32
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=cbdd44df-4a23-4bb2-b12c-51faad434b32 ro quiet splash
initrd          /boot/initrd.img-2.6.27-11-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid            cbdd44df-4a23-4bb2-b12c-51faad434b32
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=cbdd44df-4a23-4bb2-b12c-51faad434b32 ro  single
initrd          /boot/initrd.img-2.6.27-11-generic

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            cbdd44df-4a23-4bb2-b12c-51faad434b32
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=cbdd44df-4a23-4bb2-b12c-51faad434b32 ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet



ls of the /boot directory


craig@Sailfish:/boot$ ls -l
total 23804
-rw-r--r-- 1 root root  508385 2009-01-29 13:11 abi-2.6.27-11-generic
-rw-r--r-- 1 root root  507665 2008-11-04 13:00 abi-2.6.27-7-generic
-rw-r--r-- 1 root root   91358 2009-01-29 13:11 config-2.6.27-11-generic
-rw-r--r-- 1 root root   91364 2008-11-04 13:00 config-2.6.27-7-generic
drwxr-xr-x 3 root root    4096 2009-04-08 08:14 grub
-rw-r--r-- 1 root root 8200499 2009-04-07 16:30 initrd.img-2.6.27-11-generic
-rw-r--r-- 1 root root 8198681 2009-04-07 16:09 initrd.img-2.6.27-7-generic
-rw-r--r-- 1 root root  124152 2008-09-11 13:11 memtest86+.bin
-rw-r--r-- 1 root root 1031799 2009-01-29 13:11 System.map-2.6.27-11-generic
-rw-r--r-- 1 root root 1029585 2008-11-04 13:00 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root    1074 2009-01-29 13:12 vmcoreinfo-2.6.27-11-generic
-rw-r--r-- 1 root root    1073 2008-11-04 13:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r-- 1 root root 2248912 2009-01-29 13:11 vmlinuz-2.6.27-11-generic
-rw-r--r-- 1 root root 2244464 2008-11-04 13:00 vmlinuz-2.6.27-7-generic
craig@Sailfish:/boot$

---

### Post by Jakey_TheSnake on 2009-04-08
Can you attach to a post your entire menu.lst file? Also, a screenshot of whats in /boot/grub/splashimages/

edit: I probably won't find this thread again, email me at [email]clampstand@gmail.com[/email] as well, and shoot me a pm.

---

### Post by CraigJordan on 2009-04-08
Here is the menu.lst file:

craig@Sailfish:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=cbdd44df-4a23-4bb2-b12c-51faad434b32 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cbdd44df-4a23-4bb2-b12c-51faad434b32

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		cbdd44df-4a23-4bb2-b12c-51faad434b32
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cbdd44df-4a23-4bb2-b12c-51faad434b32 ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		cbdd44df-4a23-4bb2-b12c-51faad434b32
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cbdd44df-4a23-4bb2-b12c-51faad434b32 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		cbdd44df-4a23-4bb2-b12c-51faad434b32
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cbdd44df-4a23-4bb2-b12c-51faad434b32 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cbdd44df-4a23-4bb2-b12c-51faad434b32
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cbdd44df-4a23-4bb2-b12c-51faad434b32 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cbdd44df-4a23-4bb2-b12c-51faad434b32
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


splashimages directory 


craig@Sailfish:~$ ls -l /boot/grub/sp*
total 16044
-rw-r--r-- 1 root root 8200499 2009-04-08 08:28 initrd.img-2.6.27-11-generic
-rw-r--r-- 1 root root 8198681 2009-04-08 08:28 initrd.img-2.6.27-7-generic
craig@Sailfish:~$ 

Thanks for helping the newbie

---

### Post by Jakey_TheSnake on 2009-04-08
Run: 

```
sudo update-alternatives --config usplash-artwork.so
```

Choose a usplash theme, then enter:

```
sudo update-initramfs -u
```

---

### Post by CraigJordan on 2009-04-08
Hi Jakey,
Seems I have only 1 program that provides artwork.

craig@Sailfish:~$ sudo update-alternatives --config usplash-artwork.so

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.
craig@Sailfish:~$

Thanks for your help and ideas,

         -c

---

