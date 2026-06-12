---
title: "Trouble Wit Windows XP Bootloader"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by CosmicFlux on 2010-05-05
Hey,

Right so during my MCDST preperation I installed Windows XP onto my existing Ubuntu 9.10 Laptop. I know it's better to install Windows first BUT I thought I could just pop in the Ubuntu CD afterwards and use it to reinstall Ubuntu, and thus Grub, as I have all my personal files on a separate home partition. Well...I thought wrong!

I put in my 9.04 CD only to find that the partition manager doesn't recognise any of the existing Linux partitions (or the Windows ones for that matter) So I thought that maybe it has something to do with the Grub/Grub2 thing so I downloaded 10.04 and did the same, but it still doesn't recognise my existing partitions. 

So, in short, I need a way of overwriting the Windows bootloader and replacing it with grub so I can boot into Linux AND Windows.

Anyone got any ideas?


Flux

---

### Post by madjr on 2010-05-05
did you go to "computer" and see if they were there?

they are not mounted by default

whats your computer specs

---

### Post by CosmicFlux on 2010-05-05
Yeah, when I run the 10.04 LiveCD and go to computer my home partition is shown there but I don't get why the partition manager of the install doesn't see it. I can't specify it as the home partition to use. It doesn't recognize that any OS is installed, which is weird cos it's usually really good at that

---

### Post by CosmicFlux on 2010-05-05
OK, this doesn't make any sense;

I'm using the Ubuntu 9.04 LiveCD to try and re-install Grub. When I load into the desktop environment ALL of my previous Linux partitions are listed but when I go to the installer and arrive at the partition section it says there are no other operating systems on the computer?!

---

### Post by CosmicFlux on 2010-05-05
I'm trying to use the following method:

find /boot/grub/stage1
root (hd0,0)
setup (hd0)

But when I run the first command I get the following message:

File not found


Does anyone know what that is about?


Flux

---

### Post by wilee-nilee on 2010-05-05
Post this script, paste it to thread highlight it then click on # in the gui.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by CosmicFlux on 2010-05-05
[B]Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 [/B]```
=> Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca7c15e0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    91,795,409    91,795,347   7 HPFS/NTFS
/dev/sda2          91,795,410   114,173,954    22,378,545  83 Linux
/dev/sda3         114,173,955   234,436,544   120,262,590   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5         114,174,081   228,476,429   114,302,349  83 Linux
/dev/sda4         228,476,493   234,436,544     5,960,052  82 Linux swap / Solaris

/dev/sda3 overlaps with /dev/sda4

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        30B8B5CAB8B58F3A                       ntfs                                     
/dev/sda2        e8540263-ca09-4554-902c-a4243154659a   ext3       home                          
/dev/sda4        d425691e-ebc2-4db7-9fa0-765cbe698bc2   swap                                     
/dev/sda5        758bfd35-f5dd-4d74-ab5b-7bc0657189c9   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


=================== sda1: Location of files loaded by Grub: ===================


  31.0GB: boot/grub/core.img

=================== sda2: Location of files loaded by Grub: ===================


  51.7GB: boot/grub/core.img

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=758bfd35-f5dd-4d74-ab5b-7bc0657189c9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=758bfd35-f5dd-4d74-ab5b-7bc0657189c9

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

title        Ubuntu 9.10, kernel 2.6.31-18-generic
uuid        758bfd35-f5dd-4d74-ab5b-7bc0657189c9
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=758bfd35-f5dd-4d74-ab5b-7bc0657189c9 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-18-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-18-generic (recovery mode)
uuid        758bfd35-f5dd-4d74-ab5b-7bc0657189c9
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=758bfd35-f5dd-4d74-ab5b-7bc0657189c9 ro  single
initrd        /boot/initrd.img-2.6.31-18-generic

title        Ubuntu 9.10, kernel 2.6.28-17-generic
uuid        758bfd35-f5dd-4d74-ab5b-7bc0657189c9
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=758bfd35-f5dd-4d74-ab5b-7bc0657189c9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
uuid        758bfd35-f5dd-4d74-ab5b-7bc0657189c9
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=758bfd35-f5dd-4d74-ab5b-7bc0657189c9 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.10, memtest86+
uuid        758bfd35-f5dd-4d74-ab5b-7bc0657189c9
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


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=758bfd35-f5dd-4d74-ab5b-7bc0657189c9 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=e8540263-ca09-4554-902c-a4243154659a /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=d425691e-ebc2-4db7-9fa0-765cbe698bc2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  72.5GB: boot/grub/core.img
  72.5GB: boot/grub/menu.lst
  72.4GB: boot/grub/stage2
  72.5GB: boot/initrd.img-2.6.28-17-generic
  72.4GB: boot/initrd.img-2.6.31-18-generic
  72.4GB: boot/vmlinuz-2.6.28-17-generic
  72.4GB: boot/vmlinuz-2.6.31-18-generic
  72.4GB: initrd.img
  72.5GB: initrd.img.old
  72.4GB: vmlinuz
  72.4GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-05-05
my bad.

---

### Post by oldfred on 2010-05-05
wilee-nilee you do not need to repost, but we do need to get the OP to go back and put the results.txt into code tags (and remove bold).

CosmicFlux could you go back to your post and highlight the entire results.txt that you posted and unbold it and click on the # in the edit panel (on right side). This puts code tags around your entry. It preserves formating from the original (which now may be lost) and puts it in a scroll box. That makes it easier for us to scroll thru and read the entire thing.

I do not know if this is the entire problem or not:
sda1 shows the windows boot files plus a grub file.
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM [COLOR=DarkRed]/boot/grub/core.img[/COLOR]

I do not show a /boot in my XP install but check to see if any windows files are in it otherwise delete it. definitely delete /boot/grub and anything in that.

---

### Post by wilee-nilee on 2010-05-05
I appreciate you telling me this as I try to stay out of the way, no problem. ;)

---

### Post by oldfred on 2010-05-05
wilee-nilee, when I said repost I meant the results.txt. It was your copy I actually read since it was easier to read. I just want to get those who post to use the code (#) tags since it is so much easier to read.

---

### Post by CosmicFlux on 2010-05-06
No, those boot files appearing there are a result of me trying to copy Grub onto the system partition. I didn't know which one it was so I tried them all!

---

### Post by oldfred on 2010-05-06
Extra /boot files in the windows directory often confuses windows. Do not copy grub files to the windows partition.

---

