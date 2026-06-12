---
title: "Issues with a new partition"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by AustenB on 2009-07-20
Hi, I recently setup Ubuntu to dual boot with Vista, and used GParted to modify the existing partitions, and create a new one for data for Ubuntu.  After partitioning everything, I've ran into a two issues.

First, the new partition can only be accessed with sudo (i think that's what it's called) permission.  I'd like to change this, considering it's just blank space and nothing valuable in it.  I found this out because I can't copy anything onto the new drive cause it says I don't have the permission.

Second, and less important, my boot menu now lists everything twice.  Before partitioning, It listed everything once.  I'd like to fix this issue, but it's really not negatively effecting anything

Help would be greatly appreciated :D

---

### Post by Zero++ on 2009-07-20
can you post a copy of your /boot/grub/menu.lst file?

---

### Post by AustenB on 2009-07-20
Sure, here it is.

edit: crap it didn't attach, one sec

---

### Post by AustenB on 2009-07-20
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=ebc72e5e-2929-40d9-bc63-89b545e43967 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ebc72e5e-2929-40d9-bc63-89b545e43967

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        ebc72e5e-2929-40d9-bc63-89b545e43967
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ebc72e5e-2929-40d9-bc63-89b545e43967 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        ebc72e5e-2929-40d9-bc63-89b545e43967
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ebc72e5e-2929-40d9-bc63-89b545e43967 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        ebc72e5e-2929-40d9-bc63-89b545e43967
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ebc72e5e-2929-40d9-bc63-89b545e43967 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ebc72e5e-2929-40d9-bc63-89b545e43967
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ebc72e5e-2929-40d9-bc63-89b545e43967 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ebc72e5e-2929-40d9-bc63-89b545e43967
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

--------------------------------------------
I just pasted the insides of it cause it said it was an invalid file

---

### Post by Zero++ on 2009-07-20
According to this there are 5 Linux options and 2 Windows options and should look a little something like this.

Ubuntu 9.04, kernel 2.6.28-13-generic
Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28-11-generic
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, memtest86+

Other operating systems:

Windows Vista (loader)
Windows Vista (loader)

is that right? 

you can choose which of those you want to boot into and delete the /boot/grub/menu.lst file. I would boot into each and see where they lead. This is how my computer looks when it boots (the linux part anyway) and I just kept all of them. 

The windows part is a bit more tricky because they say there is a windows on the first and second partition of the first hard drive (see below). 

rootnoverify    (hd0,0)
rootnoverify    (hd0,1)

I would boot into both of these partitions and see what happens I would also get into Gparted and take a look. 

If you do decide this is worth taking the risk of editing your menu.lst make sure you make a backup of the file maybe even on a jumb drive.

Worst case scenario you screw it up and grub won't boot right. All you should have to do is boot from the Ubuntu live CD and replace the menu.lst file with your backup and it should work again. 

Hope this helps.

---

### Post by Michaelg14 on 2009-07-20
I'm not sure what you mean by data. Linux keeps most of its "data" in the home directory.  If you mean to use the new partition for home it needs to be mounted as "/home" As the home partition you will have automatic access to it. (if it is _your_ home)  You will also be able to change distros a little easier with a separate home partition.  I don't know how to mount it at this point, I have always specified a separate partition as home when I was installing Ubuntu but I am sure someone will have that info.

---

