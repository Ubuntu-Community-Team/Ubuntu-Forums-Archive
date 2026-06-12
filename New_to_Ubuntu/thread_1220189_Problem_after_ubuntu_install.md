---
title: "Problem after ubuntu install"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Mazata on 2009-07-22
I recently installed Ubuntu on a system with 3 Hds first off grub seemed to get installed on the wrong Hd (Fixed) 
But now I cannot boot into XP I did not defrag but from what I remember I had relatively low fragmentation.
I just resized the 120gb hd to install ubuntu 

I lost both my xp key and cd but have brought an unused cd from the office home. Tried to boot onto that but get a blue screen of death after it loads the drivers. 

Please help :confused:

---

### Post by TeoBigusGeekus on 2009-07-22
Please post us the output of 
```
sudo fdisk -l
```
(-L)
and
the content of your menu.lst file
```
gksudo gedit /boot/grub/menu.lst
```
(.LST)

---

### Post by SaaTeeVaaGreen on 2009-07-22
could you post the contents of your menu.lst file and the results of ```
sudo fdisk -l
``` we should be able to see what the problem is then:)

---

### Post by Mazata on 2009-07-22
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x149f1297

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12634   101482573+   7  HPFS/NTFS
/dev/sda2           12635       14593    15735667+   5  Extended
/dev/sda5           12635       14505    15028776   83  Linux
/dev/sda6           14506       14593      706828+  82  Linux swap / Solaris


I've taken all the other HDs off the mobo but still no dice



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
# kopt=root=UUID=85cf029c-7753-46dd-968a-a6db2955ec7e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=85cf029c-7753-46dd-968a-a6db2955ec7e

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
uuid        85cf029c-7753-46dd-968a-a6db2955ec7e
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=85cf029c-7753-46dd-968a-a6db2955ec7e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        85cf029c-7753-46dd-968a-a6db2955ec7e
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=85cf029c-7753-46dd-968a-a6db2955ec7e ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        85cf029c-7753-46dd-968a-a6db2955ec7e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=85cf029c-7753-46dd-968a-a6db2955ec7e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        85cf029c-7753-46dd-968a-a6db2955ec7e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=85cf029c-7753-46dd-968a-a6db2955ec7e ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        85cf029c-7753-46dd-968a-a6db2955ec7e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Dell Utility Partition
#root        (hd0,0)
#savedefault
#makeactive
#chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by SaaTeeVaaGreen on 2009-07-22
it seems like window$ is on a different drive to the one mentioned in the fdisk output. do you know if this sounds correct? 

if so, you will probably need to change the rootnoverify location of the xp entry at the end of menu.lst to match that drive, likely to be (hd1,0).

---

### Post by Mazata on 2009-07-22
It's on that drive, like I said I took all the other drives off (One is a media drive) (the other I used just for virtual memory).

---

### Post by Mazata on 2009-07-22
Bump

---

### Post by sandyd on 2009-07-22
Perhaps

```

title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```
should be
```

title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```
p.s. do a
```

ls 

```of your windows partition please (on the current disk)

---

### Post by Mazata on 2009-07-23
How do I do a ls of that partition

---

### Post by SaaTeeVaaGreen on 2009-07-23
in your terminal type ```
ls /windows
```and this will tell you the contents of your windows partition, if its present

---

