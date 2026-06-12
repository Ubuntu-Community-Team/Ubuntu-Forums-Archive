---
title: "I don't see jaunty on my menu.lst grub editor"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by libihero on 2009-06-19
i'm trying to make 8.10 the default booter, and get rid of the repetitive options in grub, but i can't seem to figure out how to do it.
here is what it looks like

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=82a7e57d-276f-48a5-a463-fa1e9d117c95 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=82a7e57d-276f-48a5-a463-fa1e9d117c95

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
# defoptions=vga=788 quiet splash

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
uuid		82a7e57d-276f-48a5-a463-fa1e9d117c95
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=82a7e57d-276f-48a5-a463-fa1e9d117c95 ro vga=788 quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		82a7e57d-276f-48a5-a463-fa1e9d117c95
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=82a7e57d-276f-48a5-a463-fa1e9d117c95 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		82a7e57d-276f-48a5-a463-fa1e9d117c95
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=82a7e57d-276f-48a5-a463-fa1e9d117c95 ro vga=788 quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		82a7e57d-276f-48a5-a463-fa1e9d117c95
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=82a7e57d-276f-48a5-a463-fa1e9d117c95 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		82a7e57d-276f-48a5-a463-fa1e9d117c95
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=82a7e57d-276f-48a5-a463-fa1e9d117c95 ro vga=788 quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		82a7e57d-276f-48a5-a463-fa1e9d117c95
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=82a7e57d-276f-48a5-a463-fa1e9d117c95 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		82a7e57d-276f-48a5-a463-fa1e9d117c95
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
splashimage=/boot/grub/splashimages/medine_moon_right_below.xpm.gz
```

---

### Post by WildeBeest on 2009-06-19
Edit the menu.lst file and change the default value to 0.
 
 
```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		[COLOR=red]4 -> 0[/COLOR]


```

---

### Post by Paqman on 2009-06-19
There's a good tool for cleaning up menu.lst called startupmanager. It actually does a lot of other cool stuff too, so it's well worth checking out. Just tell it what system you want to boot by default and how many kernel versions you want to keep. Job done.

---

