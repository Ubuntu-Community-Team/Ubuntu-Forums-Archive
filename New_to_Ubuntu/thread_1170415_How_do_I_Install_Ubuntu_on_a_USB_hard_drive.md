---
title: "How do I Install Ubuntu on a USB hard drive?"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by bwallum on 2009-05-26
I have a 320GB external 2.5" USB connected hard drive.

I have partioned it with ext3 and FAT32 partitions, the latter to enable file storage with other operating systems.

I installed Ubuntu 9.04 on the ext3 partition, changed my cmos harddrive list to boot it on start up ....and got an error '...failed to load operating system'

Any offers on how to overcome this error please?

Output of sudo fdisk -l (having rebooted on my internal hard drive sda) is: > Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00014e89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9351    75111876   83  Linux
/dev/sda2            9352        9726     3012187+   5  Extended
/dev/sda5            9352        9726     3012156   82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00091c1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e822c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbcc19f9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        7627    61263846   83  Linux
/dev/sdd2            7628       38913   251304795    b  W95 FAT32


---

### Post by Cheesemill on 2009-05-26
When you installed on your external drive, did you select the advanced GRUB options and tell it to install GRUB on the external as well?

If not then there is no boot sector written to your external drive, which gives the error when trying to boot from it.

Cheesemill

---

### Post by grungedoobie on 2009-05-26
Hey, if you have a hankerin' for a bit of the command line controls,

Came across this tutorial:

[http://www.linux.com/archive/feature/62434](http://www.linux.com/archive/feature/62434)

Perhaps that's what you're looking for.

Keep an eye to the right as you scroll down.  That's where the grub install usb boot section is. 

Best of luck,


The Grunge :)

---

### Post by bwallum on 2009-05-26
Thanks guys! I guess I'm getting there. I can get grub up to stage 1.5 where it then throws an error 2. I think it can't see the kernel file, menu.lst as below> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=31529e96-bd79-4a9d-a2d2-c5fe516824f8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=31529e96-bd79-4a9d-a2d2-c5fe516824f8

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		31529e96-bd79-4a9d-a2d2-c5fe516824f8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=31529e96-bd79-4a9d-a2d2-c5fe516824f8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		31529e96-bd79-4a9d-a2d2-c5fe516824f8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=31529e96-bd79-4a9d-a2d2-c5fe516824f8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		31529e96-bd79-4a9d-a2d2-c5fe516824f8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.


The UUID is the volume (single partition) of the USB drive. Any clues?

---

### Post by bwallum on 2009-05-27
Well here I am, working from a 32bit Jaunty installed on a usb harddrive (_not_ a usb solid state memory stick), that plugs into a 64bit pc.

Like most things when you fiddle on a bit, I'm not too sure how I did it. I used the Jaunty i386 live cd and installed to the usb hard drive. When it came to selecting a drive to install on I chose the advanced manual setup option. I created a partition with ext3 file type (60GB) and then a second partition of type swap (3.084GB). I wanted the rest to be a fat32 partition but it jibbed so I left it as unallocated and then used gparted once I got up and running. I now have the 239GB fat32 partition working fine.

It can be a little nervy when choosing the drive to work on when the partitioner opens. If in any doubt use the live cd and run```
sudo lshw -class disk
```You will be shown all the disks on your pc including the usb drive. Look for the logical name of the usb drive, in my case it was /dev/sdd (yours will be different unless you have 3 internal hard drives installed). Select this drive as you work through the partitioner during the install process.

I can now run my diddy little usb drive on any machine once I change the cmos to boot the usb drive first. This is now a brilliant rescue tool for any operating system and really makes simple work of zapping Windows viruses using clam, backing up files, reloading direct to Windows folders etc.

Thanks for all your help!

---

