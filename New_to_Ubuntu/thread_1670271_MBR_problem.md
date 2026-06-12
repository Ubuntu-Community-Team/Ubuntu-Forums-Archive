---
title: "MBR problem"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by The Eight-Bit Link on 2011-01-18
I reinstalled wondows xp (My fave) and after it finished, I found out it rewrote the MBR. How do I fix this? I reloaded grub, but it stops at 
```
 
GRUB Loading stage1.5Read Error

```
Exactly like that. Help please!

---

### Post by bro on 2011-01-18
Do you mean you installed xp after you installed ubuntu, with the intention to dual boot? (you better do it the other way round and install windows first). 

Do you mean to install xp and delete ubuntu completely? 

In any case, if you mean to re-install grub? You can use a live cd for that.

---

### Post by The Eight-Bit Link on 2011-01-18
No, I HAD Windows XP and Ubuntu dual booting, then windows had a derp, so I reinstalled thinking GRUB would just work as normal. Big mistake. Is there a way to fix, or am I screwed?

---

### Post by Quackers on 2011-01-18
Which Ubuntu version is installed?

---

### Post by The Eight-Bit Link on 2011-01-18
10.04

---

### Post by Quackers on 2011-01-18
What commands are you using to re-install grub? You are in the live cd desktop now?

---

### Post by The Eight-Bit Link on 2011-01-18
I tried the un-live grub fix, but yes, I am now in live disk.

BTW: Props to you, I have never had responses come this fast before, on any forum.

---

### Post by Quackers on 2011-01-18
From the live cd desktop please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then I can give you the proper terminal commands to re-install grub, if necessary.

---

### Post by The Eight-Bit Link on 2011-01-18
It's not there, unfortunatly. do you have a copy you could e-mail me or some such like that?

---

### Post by brookie on 2011-01-18
Hi there,
I did a dual boot, linux first and xp later, and used [this post]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") to do it and recover grub. Read the whole post. The grub part comes last. It all worked out but I no longer dual boot, and only use xp in vbox. 
Hope that helps. 
Cheers, 
brook

sorry, that's for the old grub, not grub2, and menu.lst is no longer in /boot/grub/menu.lst
grub2 has that in another place so i'll have to pull up a grub2 page to check

---

### Post by Quackers on 2011-01-18
What do you mean by "it's not there"?

---

### Post by The Eight-Bit Link on 2011-01-18
Please ignore my previous statement.
Anyhoo...
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   249,553,709   249,553,647   7 HPFS/NTFS
/dev/sda2         249,553,710   312,576,704    63,022,995   5 Extended
/dev/sda5    *    249,553,773   309,893,849    60,340,077  83 Linux
/dev/sda6         309,893,913   312,576,704     2,682,792  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 137.4 GB, 137438952960 bytes
255 heads, 63 sectors/track, 16709 cylinders, total 268435455 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   268,435,454   268,435,454  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34   134,217,726   134,217,693 Linux or Data
/dev/sdb2     134,217,727   268,435,421   134,217,695 Linux or Data

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1967 MB, 1967128576 bytes
1 heads, 62 sectors/track, 61968 cylinders, total 3842048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *            137     3,842,047     3,841,911   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        962C3BEF2C3BC94F                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7ee67c27-dac0-4a76-880b-a02c6aee2db3   ext3                                     
/dev/sda6        a1a78ab1-dde8-42bc-ab52-5b44d435f643   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        342D5DB01F9DB843                       ntfs                                     
/dev/sdb2        d1f1037f-58f9-4671-9aa7-e0ae0173abdb   ext4       New Volume                    
/dev/sdb: PTTYPE="gpt" 
/dev/sdc1        2020-2020                              vfat       SANYO                         
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/SANYO             vfat       (rw,nosuid,nodev,uhelper=hal,uid=999,umask=0077,shortname=winnt,utf8)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
default        8

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
# kopt=root=UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7ee67c27-dac0-4a76-880b-a02c6aee2db3

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic
uuid        7ee67c27-dac0-4a76-880b-a02c6aee2db3
kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-27-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic (recovery mode)
uuid        7ee67c27-dac0-4a76-880b-a02c6aee2db3
kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 ro  single
initrd        /boot/initrd.img-2.6.32-27-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic
uuid        7ee67c27-dac0-4a76-880b-a02c6aee2db3
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-26-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic (recovery mode)
uuid        7ee67c27-dac0-4a76-880b-a02c6aee2db3
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 ro  single
initrd        /boot/initrd.img-2.6.32-26-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
uuid        7ee67c27-dac0-4a76-880b-a02c6aee2db3
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
uuid        7ee67c27-dac0-4a76-880b-a02c6aee2db3
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic
uuid        7ee67c27-dac0-4a76-880b-a02c6aee2db3
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        7ee67c27-dac0-4a76-880b-a02c6aee2db3
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-15-generic
uuid        7ee67c27-dac0-4a76-880b-a02c6aee2db3
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-15-generic (recovery mode)
uuid        7ee67c27-dac0-4a76-880b-a02c6aee2db3
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.27-11-generic
uuid        7ee67c27-dac0-4a76-880b-a02c6aee2db3
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.27-11-generic (recovery mode)
uuid        7ee67c27-dac0-4a76-880b-a02c6aee2db3
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        7ee67c27-dac0-4a76-880b-a02c6aee2db3
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=7ee67c27-dac0-4a76-880b-a02c6aee2db3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=a1a78ab1-dde8-42bc-ab52-5b44d435f643 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 134.5GB: boot/grub/menu.lst
 134.5GB: boot/grub/stage2
 134.5GB: boot/initrd.img-2.6.27-11-generic
 134.6GB: boot/initrd.img-2.6.28-15-generic
 134.5GB: boot/initrd.img-2.6.31-22-generic
 134.5GB: boot/initrd.img-2.6.32-25-generic
 134.4GB: boot/initrd.img-2.6.32-26-generic
 134.6GB: boot/initrd.img-2.6.32-27-generic
 134.5GB: boot/vmlinuz-2.6.27-11-generic
 134.5GB: boot/vmlinuz-2.6.28-15-generic
 134.5GB: boot/vmlinuz-2.6.31-22-generic
 134.6GB: boot/vmlinuz-2.6.32-25-generic
 134.5GB: boot/vmlinuz-2.6.32-26-generic
 134.4GB: boot/vmlinuz-2.6.32-27-generic
 134.6GB: initrd.img
 134.4GB: initrd.img.old
 134.4GB: vmlinuz
 134.5GB: vmlinuz.old
```

---

### Post by Quackers on 2011-01-18
It seems that you followed an old guide. This guide was for installing grub legacy. Ubuntu 10.04, by default, used grub2
I think grub legacy has been made to boot Ubuntu 10.04, but I haven't done it.
There is an option and that would be to purge grub legacy and install grub2. Fortunately drs305 wrote a guide for this specific purpose and it is available below. You will need to use the full chroot procedure. The partition you want to mount is sda5 and the place to install grub2 is to sda (not sda5).

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Obviously you can wait to see if somebody can help you to get grub legacy to boot 10.04. That may be a good idea.

There is something else about your boot script that looks odd.
```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
```

The space next to Operating System should have Windows XP in there - not nothing.
This is puzzling. If XP boots ok, then it isn't a problem.

---

### Post by The Eight-Bit Link on 2011-01-18
No, XP doesn't boot; GRUB whines like I described in the beginning

---

### Post by Quackers on 2011-01-18
I don't see XP on your system anywhere!

---

### Post by The Eight-Bit Link on 2011-01-18
It was misdetected as vista/seven.
Another problem. My machine in question is not connected and can't connect without ndiswrapper. Help please?

---

### Post by Quackers on 2011-01-18
Errrm, no Windows operating system is present, that I can see. Only a Windows XP boot sector and a Windows Vista/7 boot sector. Not operating systems!
Have you tried an ethernet cable?

---

