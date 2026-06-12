---
title: "edit menu.lst to show Windows XP on grub"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by Zopiac on 2009-06-12
I installed Linux Mint alongside Windows XP (a loose variant of ubuntu), but Windows did not show up on my GRUB. I just got my Kubuntu 9.04 disk in the mail, so I installed it on yet another partition, hoping that it might detect XP and put it on the GRUB. It didn't. The XP partition has been accessable the entire time, but Linux hasn't been able to detect it to put it on the GRUB...

How do I edit menu.lst manually to put Windows on the GRUB? I would post my drive configuration, but I forget the command to list it... :P

Thanks in advance for the help ^_^

---

### Post by Miljet on 2009-06-12
```
sudo fdisk -l
```

---

### Post by nandemonai on 2009-06-12
```
sudo fdisk -l
```

Also, post the output of:

```
cat /boot/grub/menu.lst
```

We can take it from there. You be looking at adding something like:

title		Microsoft Windows XP
rootnoverify	(hd0,3)
savedefault
makeactive
chainloader	+1

Though depending on your setup obviously the numbers will likely differ. ;)

---

### Post by Zopiac on 2009-06-12
> **Miljet said:**
> ```
sudo fdisk -l
```

thx :)

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc85a3fbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        8161    65545200    f  W95 Ext'd (LBA)
/dev/sda2            8162       11133    23872590    7  HPFS/NTFS
/dev/sda3   *       11134       18428    58597087+  83  Linux
/dev/sda4           18429       19457     8265442+  83  Linux
/dev/sda5               2        8161    65545168+   7  HPFS/NTFS

```

Hope that helps with an answer :)

---

### Post by Bölvaður on 2009-06-12
title		Microsoft Windows XP
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1




this also could be  rootnoverify	(hd0,4)

---

### Post by Zopiac on 2009-06-12
> **Bölvaður said:**
> 
rootnoverify	(hd0,1)

I took off the 'noverify' part of 'rootnoverify' and it showed up...had a hunch, since all of my other entries were only 'root'. dunno, but it worked :)

For a little bit, that is. I selected my new Windows XP entry and it told me that i was missing BOOTMGR...

> **Bölvaður said:**
> 
this also could be  rootnoverify	(hd0,4)

I'm going to try this now, hopefully it will work. Minus the noverify, that is. Could you/someone else explain the rootnoverify vs. root thing? I'm interested :)

---

### Post by nandemonai on 2009-06-12
> **Zopiac said:**
> I took off the 'noverify' part of 'rootnoverify' and it showed up...had a hunch, since all of my other entries were only 'root'. dunno, but it worked :)

For a little bit, that is. I selected my new Windows XP entry and it told me that i was missing BOOTMGR...



I'm going to try this now, hopefully it will work. Minus the noverify, that is. Could you/someone else explain the rootnoverify vs. root thing? I'm interested :)

[http://www.gnu.org/software/grub/manual/html_node/root.html](http://www.gnu.org/software/grub/manual/html_node/root.html)

[http://www.gnu.org/software/grub/manual/html_node/rootnoverify.html](http://www.gnu.org/software/grub/manual/html_node/rootnoverify.html)

:)

---

### Post by Zopiac on 2009-06-13
Does anybody know how to get Windows XP working when it gives the BOOTMGR Not Found error? Using neither (hd0,1) nor (hd0,4) works; they both give me the same error.

Here's my menu.lst, if it helps (I have a few of the entries commented out):

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
# kopt=root=UUID=43c6da3d-dc89-4e95-a5ff-4c38c623714d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=43c6da3d-dc89-4e95-a5ff-4c38c623714d

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
uuid		43c6da3d-dc89-4e95-a5ff-4c38c623714d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=43c6da3d-dc89-4e95-a5ff-4c38c623714d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		43c6da3d-dc89-4e95-a5ff-4c38c623714d
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=43c6da3d-dc89-4e95-a5ff-4c38c623714d ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

#title		Ubuntu 9.04, memtest86+
#uuid		43c6da3d-dc89-4e95-a5ff-4c38c623714d
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Linux Mint x64 Edition, kernel 2.6.27-7-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
#title		Linux Mint x64 Edition, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda3)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda3 ro single 
#initrd		/boot/initrd.img-2.6.27-7-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
#title		Linux Mint x64 Edition, memtest86+ (on /dev/sda3)
#root		(hd0,2)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot

title 		Microsoft Windows XP
root	 	(hd0,4)
savedefault
makeactive
chainloader +1
```

---

### Post by Bölvaður on 2009-06-15
> **Zopiac said:**
> 
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        8161    65545200    f  W95 Ext'd (LBA)

```

I didn't realize what this partition might be the one that windows boots from. I have no idea how stupid this is but I guess you can try boot from it.
If the "chainloader +1" command is there it will look for a boot loader or manager or w/e it is. And if it doesnt find one it will give you a *BOOTMGR Not Found *or something similar.
To try to boot from sda1 (the first partition of the first hard disk) you select that partition (hd0 (first hard disk) hd0,0 (first partition on the first hard disk)).

```
title		Microsoft Windows XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Zopiac on 2009-06-15
> **Bölvaður said:**
> I didn't realize what this partition might be the one that windows boots from. I have no idea how stupid this is but I guess you can try boot from it.
If the "chainloader +1" command is there it will look for a boot loader or manager or w/e it is. And if it doesnt find one it will give you a *BOOTMGR Not Found *or something similar.
To try to boot from sda1 (the first partition of the first hard disk) you select that partition (hd0 (first hard disk) hd0,0 (first partition on the first hard disk)).

```
title		Microsoft Windows XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

:( it didn't work...in fact, just for kicks, I tried that with hd0,0 through hd0,4 and nothing worked...worth a shot though.

hd0,1 was the only entry that gave me a windows error, but it was still the BOOTMGR not found error. I have never encountered this error before, does anybody know a fix? Will google error message after post.

Thanks for the help so far!

---

### Post by bluelime on 2009-06-22
i have the exact same problem.  has the solution been found?

---

### Post by Zopiac on 2009-06-24
> **bluelime said:**
> i have the exact same problem.  has the solution been found?

No, it hasn't, sadly. I am still without Windows XP and Wine isn't that good yet :P

---

### Post by presence1960 on 2009-06-24
your boot manager is missing, you need the windows install disk or super grub disk to replace it. Then you will have to restore GRUB. So first restore the windows boot manager from install CD like this : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

This will restore windows boot loader, windows will never boot without it no matter how much you edit your menu.lst. Now you have to restore GRUB because the windows bootloader will overwrite GRUB. Do this :
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```

---

### Post by LewRockwell on 2009-06-24
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

please note that this disk does MANY things and one would be wise to go through it to see what all it can do!

---

