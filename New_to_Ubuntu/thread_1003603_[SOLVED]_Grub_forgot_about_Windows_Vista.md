---
title: "[SOLVED] Grub forgot about Windows Vista"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by pablolie on 2008-12-06
I have a question: I just re-installed 8.10 64-bit, and low and behold, even though Grub correctly saw Windows Vista 64 on the drive, it is not a part of the Grub menu, it has disappeared as a boot option. What is even stranger is that when starting off the Windows installation CD, Windows will claim it is all very well with the OS and there is nothing to repair.

My question is - how can I go back to the Windows bootloader when Ubuntu is now the only OS I can change? Can I edit Grub and add Windows to the options? How?

Thanks so much!

PS: Here are the results of a command I see the experts always ask for when it comes to boot issues:

pablo@ubuntu64server:~$ sudo fdisk -lu
 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2affd92d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   731004919   365501436    7  HPFS/NTFS
/dev/sda2       731005695   976751999   122873152+   5  Extended
/dev/sda5       731005758   966679244   117836743+  83  Linux
/dev/sda6       966679308   976751999     5036346   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2affd92d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   731004919   365501436    7  HPFS/NTFS
/dev/sdb2       731005695   976751999   122873152+   5  Extended
/dev/sdb5       731005758   966679244   117836743+  83  Linux
/dev/sdb6       966679308   976751999     5036346   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2ab79833

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   976769023   488383488    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   976768064   488384001    7  HPFS/NTFS
pablo@ubuntu64server:~$

---

### Post by lovelyvik293 on 2008-12-06
please post the /boot/grub/menu.lst file.

---

### Post by pablolie on 2008-12-06
Here it is... Thanks!!

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
# kopt=root=/dev/mapper/isw_ecaidddicc_raid-c5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/mapper/isw_ecaidddicc_raid-c5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/mapper/isw_ecaidddicc_raid-c5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by pablolie on 2008-12-06
Both OS are installed on a mirrored RAID.

---

### Post by Solaris3k1 on 2008-12-06
You need to add your Vista partition to your boot list.  It isn't there at all.

Add something along the lines of 

```

title		Microsoft Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

To the end of your /boot/grub/menu.lst file.  If I'm right, you have Vista on the first partition of your first hard drive, so this should do it.

---

### Post by pablolie on 2008-12-06
Thanks - wish I could have tried that out in time.

In the meantime, I followed the advice on
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

to restore the Vista boot sequence, and of course now in turn I can not load Ubuntu. I have added it to EasyBCD, but it will not load successfully...

---

### Post by Duck2006 on 2008-12-06
These may help.

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://ubuntuforums.org/showthread.php?t=506668](http://ubuntuforums.org/showthread.php?t=506668)

---

### Post by Solaris3k1 on 2008-12-06
> **pablolie said:**
> Thanks - wish I could have tried that out in time.

In the meantime, I followed the advice on
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

to restore the Vista boot sequence, and of course now in turn I can not load Ubuntu. I have added it to EasyBCD, but it will not load successfully...

Okay, I'm pretty new, but I've never heard of EasyBCD and... well... considering your troubles, it doesn't seem so easy.  It appears just to be a bootloader auto-editor.

Post your NEW /boot/grub/menu.lst and we'll see what we can do.  It's probably just another edit needed.

---

### Post by Duck2006 on 2008-12-06
> Okay, I'm pretty new, but I've never heard of EasyBCD

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by pablolie on 2008-12-06
Well, menu.lst is one of those files that Ubuntu won't grant one the privilege to change... what is the trick there?

---

### Post by Duck2006 on 2008-12-06
To edit your menu.lst in the terminal

gksudo gedit /boot/grub/menu.lst

and you can edit it.

Some info on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by pablolie on 2008-12-06
Thanks so much - finally managed to get this all going!

---

