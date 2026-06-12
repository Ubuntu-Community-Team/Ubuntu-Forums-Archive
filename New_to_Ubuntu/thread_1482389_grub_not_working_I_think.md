---
title: "grub not working I think"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by squrl on 2010-05-13
I have seen several references to this problem in the past but cant find an answer with search.

I have two drives. One has XP the other is 8.04 

I lost the ability to boot to XP unless I pull the plug to the 8.04 drive.
I can boot 8.04 with everything connected but not xp

Thanks

---

### Post by louieb on 2010-05-13
If your booting to Ubuntu then GRUB is working - it just not doing what you want it to do.

Exactly what happens? Do you get the GRUB menu at boot? Does it have an XP entry? What happen when you select XP. Are the drives internal or external? 

Please get and run the [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/") and put the results.txt file in your next post.

---

### Post by squrl on 2010-05-13
I get the slight delay to boot. The grub menu only shows the 8.04 entry plus one for checking memory. Nothing shows up for xp at all.

The drives are sata internal               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bf756

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,933,760,114 1,933,760,052  83 Linux
/dev/sda2       1,933,760,176 1,953,520,064    19,759,889   5 Extended
/dev/sda5       1,933,760,178 1,953,520,064    19,759,887  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000784a2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008a872

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   488,263,544   488,263,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e7c365ec-50bd-4a30-a30c-4591d0523542   ext3                                     
/dev/sda5        2802d08d-b88a-4504-ad22-509b1c82f2d6   swap                                     
/dev/sdb1        bdaf07f8-e153-43dd-8a6a-74d8922a7fed   ext2                                     
/dev/sdc1        58C88CEDC88CCAA8                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb1        /media/disk              ext2       (rw,nosuid,nodev,uhelper=hal)


=========================== sda1/boot/grub/menu.lst: ===========================

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
hiddenmenu

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
# kopt=root=UUID=e7c365ec-50bd-4a30-a30c-4591d0523542 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=e7c365ec-50bd-4a30-a30c-4591d0523542 ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=e7c365ec-50bd-4a30-a30c-4591d0523542 ro single
initrd		/boot/initrd.img-2.6.24-27-generic

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=e7c365ec-50bd-4a30-a30c-4591d0523542 ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=e7c365ec-50bd-4a30-a30c-4591d0523542 ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e7c365ec-50bd-4a30-a30c-4591d0523542 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2802d08d-b88a-4504-ad22-509b1c82f2d6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 799.6GB: boot/grub/menu.lst
 799.7GB: boot/grub/stage2
 799.7GB: boot/initrd.img-2.6.24-26-generic
 799.6GB: boot/initrd.img-2.6.24-27-generic
 799.7GB: boot/initrd.img-2.6.24-27-generic.bak
 799.7GB: boot/vmlinuz-2.6.24-26-generic
 799.7GB: boot/vmlinuz-2.6.24-27-generic
 799.6GB: initrd.img
 799.7GB: initrd.img.old
 799.7GB: vmlinuz
 799.7GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

---

### Post by louieb on 2010-05-13
No XP entry in /boot/grub/menu.lst. 

Try these changes. from a terminal window:
1st make a backup

```
sudo copy /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

now use gedit to edit

```
gksudo gedit /boot/grub/menu.lst
```

find the hiddenmenu line and comment it out so the grub menu always displays on boot.
and add a entry for XP. 

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]#hiddenmenu[/COLOR]
 
```

Try this XP entry make it the last lines of menu.lst

```

title Win XP Home
      map (hd0) (hd2)
      map (hd2) (hd0)
      rootnoverify (hd2,0)
      makeactive
      chainloader +1
      boot


```


That should work - if not then post the content of /boot/grub/device.map 
may have to make a minor tweak to it to - looks like you have 3 hdds - did you have 3 when you installed Ubuntu?

---

### Post by oldfred on 2010-05-13
Did you have your windows entry inside the automagic area and with a kernel update that area is rewritten.

Add this after the end automagic at the bottom or before the start automagic (about 1/3 down from top) in your menu.lst

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

---

