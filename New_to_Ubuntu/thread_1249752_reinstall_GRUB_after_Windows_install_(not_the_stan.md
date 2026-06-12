---
title: "reinstall GRUB after Windows install (not the standard GRUB reinstall)"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by rockerphil on 2009-08-25
ok, here's the deal, i'm currently quad booting my old Dell Dimension L500cx with a minimal Ubuntu 8.04 LTS install, Xubuntu 9.04, Windows XP Pro and Damn Small Linux and i recently replaced my primary hard drive that contained my Windows partition with a larger one (about 120 GB rather than the 8 GB HDD i had). well here's where it gets tricky. i've got a LOT of music on the hard drive (about 90 GB worth). so i repartitioned the hard drive to preserve the music, and Windows ended up being installed to the the second partition, identified as the E drive by Windows, and identified as hda2 by my Ubuntu installs with the music being on the C drive (hda1) so i can't exactly simply restore my old GRUB menu.lst file as it would end up trying to boot Windows from my music partition so until i can figure this out i've been accessing my Linux installs via the Super GRUB disk, and after searching the all mighty Google for days i'm kicking it to you guys. any help is appreciated and if any more info is needed please ask. much thanks in advance,

Phil

---

### Post by eagle416 on 2009-08-25
couldn't you just edit your menu.1st and tell it to go to hda2 instead of hda1?

---

### Post by rockerphil on 2009-08-25
thanks for the idea eagle416, but no luck. i tried it and when i tried to boot my Windows partition i got the error message that the BOOTMGR file is missing.

---

### Post by mike555 on 2009-08-25
Have you thought of using " GAG " bootloader , that's what I use on my multi-boot system ..... [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by rockerphil on 2009-08-25
i'll give GAG a shot, but for now i'd simply like to get GRUB working again seeing as it's what i've grown accustomed to

---

### Post by kansasnoob on 2009-08-25
Please post the output of both:

```
sudo fdisk -l
```

and:

```
cat /boot/grub/menu.lst
```

Make that three:

```
cat /boot/grub/menu.lst.backup
```

---

### Post by rockerphil on 2009-08-25
here ya go kansasnoob

```
phil@phillip:~$ sudo fdisk -l
[sudo] password for phil: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa6d90266

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10129    81361161    7  HPFS/NTFS
/dev/sda2   *       10130       14593    35857080    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe26ae26a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         510     4096543+  83  Linux
/dev/sdb2             511         553      345397+  83  Linux
/dev/sdb3             554        2880    18691627+   5  Extended
/dev/sdb4            2881        4865    15944512+   7  HPFS/NTFS
/dev/sdb5             554        1891    10747453+  83  Linux
/dev/sdb6            2836        2880      361431   82  Linux swap / Solaris
/dev/sdb7            1892        2788     7205121   83  Linux
/dev/sdb8            2789        2835      377496   82  Linux swap / Solaris

Partition table entries are not in disk order
phil@phillip:~$
```

```
phil@phillip:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=fe902709-3f2b-4da8-bbd5-03eb2d048733 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)
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

title           Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root            (hd1,4)
kernel          /boot/vmlinuz-2.6.24-24-generic root=UUID=fe902709-3f2b-4da8-bbd5-03eb2d0487
33 ro quiet splash
initrd          /boot/initrd.img-2.6.24-24-generic
quiet

title           Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root            (hd1,4)
kernel          /boot/vmlinuz-2.6.24-24-generic root=UUID=fe902709-3f2b-4da8-bbd5-03eb2d0487
33 ro single
initrd          /boot/initrd.img-2.6.24-24-generic

title           Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root            (hd1,4)
kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=fe902709-3f2b-4da8-bbd5-03eb2d0487
33 ro quiet splash
initrd          /boot/initrd.img-2.6.24-23-generic
quiet

title           Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root            (hd1,4)
kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=fe902709-3f2b-4da8-bbd5-03eb2d0487
33 ro single
initrd          /boot/initrd.img-2.6.24-23-generic

title           Ubuntu 8.04.3 LTS, memtest86+
root            (hd1,4)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           DSL (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/linux24 root=/dev/hdd1 quiet vga=normal noacpi noapm nodma noscsi frug
al 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           DSL fb800x600 (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/linux24 root=/dev/hdd1 quiet vga=788 noacpi noapm nodma noscsi frugal 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           DSL fb1024x768 (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/linux24 root=/dev/hdd1 quiet vga=791 noacpi noapm nodma noscsi frugal 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title           DSL fb1280x1024 (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/linux24 root=/dev/hdd1 quiet vga=794 noacpi noapm nodma noscsi frugal 
savedefault
boot

phil@phillip:~$ 
```

```
phil@phillip:~$ cat /boot/grub/menu.lst.backup
cat: /boot/grub/menu.lst.backup: No such file or directory
phil@phillip:~$ 
```

thanks for the help,

Phil

---

### Post by bodhi.zazen on 2009-08-25
Your windows boot stanza is not pointing to the correct partition.

Windows is on (hd0,1) not (hd0,0).

Edit /boot/grub/menu.lst 

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
**[COLOR=darkred]rootnoverify            (hd0,1)[/COLOR]**
savedefault
makeactive
chainloader     +1
```Once you have fixed it , see this thread : [How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by rockerphil on 2009-08-26
thanks for the tip bodhi.zazen, but it didn't work. when i try to boot the Windows OS it says that the BOOTMGR file is missing. the help is greatly appreciated, and i'd like to get this fixed soon. thanks in advance

Phil

---

### Post by chakebubu on 2009-09-29
I have a similar problem. I had grub working well with Ubuntu and Windows. But I formatted my windows partition and istalled windows again. Now the computer boots directly to windows and I cant access my Ubuntu 9.04. How do I restore Grub bootloader?

---

### Post by bodhi.zazen on 2009-09-29
> **chakebubu said:**
> I have a similar problem. I had grub working well with Ubuntu and Windows. But I formatted my windows partition and istalled windows again. Now the computer boots directly to windows and I cant access my Ubuntu 9.04. How do I restore Grub bootloader?

You need to re-install grub.

[Recovering Ubuntu after installing Windows - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

