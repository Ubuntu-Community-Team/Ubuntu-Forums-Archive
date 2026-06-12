---
title: "Reinstalled Windows XP, repaired GRUB, now can't boot Windows"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by thornate on 2008-12-17
Previously I had two hard drives. HD0 was where Windows XP was installed and HD1 had several partitions, including the one that contained Ubuntu. Now I've changed the HD0 drive and will be using it for file storage. I've installed Windows XP on to one of the other partitions on HD1. Ubuntu hasn't been touched.

Windows was working fine until I repaired GRUB. Now I can load Ubuntu but not Windows. If I choose Windows from the GRUB menu, I get the following response: 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96756&stc=1&d=1229571086[/IMG]
Nothing happens until I press Enter, which takes me back to the GRUB menu.

fdisk -l provides the following response:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e9746

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x410ff0de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13513   108543141    7  HPFS/NTFS
/dev/sdb2           13514       17497    32001480    b  W95 FAT32
/dev/sdb3           17498       17688     1534207+  82  Linux swap / Solaris
/dev/sdb4           17689       19457    14209492+  83  Linux
```/dev/sdb1 is the partition on which Windows is installed

I have edited /boot/grub/menu.lst to change the location of the Windows partition. It now says: 
```
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```


What am I doing wrong? How can I fix this so that I can boot in to either OS?

---

### Post by cdtech on 2008-12-17
If XP isn't on the first hard drive (hd0) then you have to remap it to (hd0). Say it's on (hd1), the second hard drive:

At the GRUB boot menu press "c" to give you a "grub >" prompt, then:
```
grub> rootnoverify (hd1,0)
grub> map (hd0) (hd1)
grub> map (hd1) (hd0)
grub> makeactive
grub> chainloader +1
grub> boot

```
Try that and see if it boots to XP.

**UPDATE::.**
If it boots then we just need to edit the menu.lst to reflect the above.

---

### Post by thornate on 2008-12-17
I'm sorry, I don't understand why I would need to do that. Is it impossible to run Windows off the second hard disk? Won't this screw up the locations of all the other partitions on hd1?

Also, I saw a similar thread where the boot_info9.txt script was given to someone with a similar problem. This is the result of that script, in case it gives any necessary information:
```
Grub is installed in the MBR of /dev/sda and looks on boot drive # 2 in partition #4 for its boot files.
Grub is installed in the MBR of /dev/sdb and looks on the same drive in partition #4 for its boot files.

sda1:
    File system:  vfat
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sdb1:
    File system:  ntfs
    Boot sector  type:  XP
    Boot sector  info:  According to the info in the boot sector, sdb1 starts at sector 63
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM

sdb2:
    File system:  vfat
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sdb3:
    File system:  swap
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sdb4:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e9746

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x410ff0de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   217086344   108543141    7  HPFS/NTFS
/dev/sdb2       217086345   281089304    32001480    b  W95 FAT32
/dev/sdb3       281089305   284157719     1534207+  82  Linux swap / Solaris
/dev/sdb4       284157720   312576704    14209492+  83  Linux
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=625137282, Id= b, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=217086282, Id= 7, bootable
/dev/sdb2 : start=217086345, size= 64002960, Id= b
/dev/sdb3 : start=281089305, size=  3068415, Id=82
/dev/sdb4 : start=284157720, size= 28418985, Id=83

sdb1/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect


sdb4/boot/grub/menu.lst

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
# kopt=root=UUID=a976c032-47db-4234-b5b9-ee85c9297c0f ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=a976c032-47db-4234-b5b9-ee85c9297c0f

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		a976c032-47db-4234-b5b9-ee85c9297c0f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a976c032-47db-4234-b5b9-ee85c9297c0f ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		a976c032-47db-4234-b5b9-ee85c9297c0f
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=a976c032-47db-4234-b5b9-ee85c9297c0f ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a976c032-47db-4234-b5b9-ee85c9297c0f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a976c032-47db-4234-b5b9-ee85c9297c0f ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a976c032-47db-4234-b5b9-ee85c9297c0f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a976c032-47db-4234-b5b9-ee85c9297c0f ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a976c032-47db-4234-b5b9-ee85c9297c0f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
chainloader	+1


sdb4/boot

total 23772
drwxr-xr-x  3 root root    4096 2008-12-16 13:12 .
drwxr-xr-x 20 root root    4096 2008-11-28 13:44 ..
-rw-r--r--  1 root root  507665 2008-11-05 08:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-21 10:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-05 08:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-21 10:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-18 13:02 grub
-rw-r--r--  1 root root 8184935 2008-11-27 11:14 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8185906 2008-12-16 13:12 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-12 06:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-05 08:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-21 10:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-05 08:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-21 10:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-05 08:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-21 10:46 vmlinuz-2.6.27-9-generic

sdb4/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-18 13:02 .
drwxr-xr-x 3 root root   4096 2008-12-16 13:12 ..
-rw-r--r-- 1 root root    197 2008-11-01 22:59 default
-rw-r--r-- 1 root root     30 2008-11-01 22:59 device.map
-rw-r--r-- 1 root root   8108 2008-11-01 22:59 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-11-01 22:59 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-01 22:59 installed-version
-rw-r--r-- 1 root root   8712 2008-11-01 22:59 jfs_stage1_5
-rw-r--r-- 1 root root   5158 2008-12-18 13:02 menu.lst
-rw-r--r-- 1 root root   5158 2008-12-18 13:00 menu.lst~
-rw-r--r-- 1 root root   7352 2008-11-01 22:59 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-11-01 22:59 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-01 22:59 stage1
-rw-r--r-- 1 root root 121460 2008-11-01 22:59 stage2
-rw-r--r-- 1 root root   9556 2008-11-01 22:59 xfs_stage1_5

StdErr Messages 

ls: cannot access /dev/hd?: No such file or directory
ls: cannot access /dev/hd??*: No such file or directory
/dev/sdb3 looks like swapspace - not mounted
mount: you must specify the filesystem type
umount: sdb3: not mounted
```

---

### Post by cdtech on 2008-12-17
All the command does is boot the Windows XP if it see's it. It will not overwrite any configuration settings. The reason for the remap is XP's boot.ini file is set to the "0" device and booting from grub it needs to be fooled into thinking it's the primary drive.

**UPDATE::.**
This is what the menu.lst would look like:
```
title Microsoft Windows XP Home Edition
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader +1

```

---

### Post by thornate on 2008-12-17
So, to see if I understand this correctly: It only actually does it for when I boot Windows? Once I restart the computer, those mappings are lost. Correct?

---

### Post by cdtech on 2008-12-17
Yes, unless you add them to your menu.lst, but we just want to see if it will boot XP using the command prompt (grub) and the settings provided above. If it does then you can edit the menu.lst

---

### Post by Aearenda on 2008-12-17
Before you restored GRUB, I'm guessing you were booting directly off hd1 using the BIOS settings. On some systems this automatically reverses the order in which the drives appear (as cdtech wants to make happen), so that Windows would think it was on drive C:. This is borne out by both instances of 'multi(0)disk(0)rdisk(0)partition(1)\WINDOWS' in the boot.ini file, which look to drive C:. Windows is picky about this.
Now that you have restored Grub, to both hd0 and hd1, which drive is your system booting from in the BIOS? If I'm right (no guarantees), it should work from either drive for Ubuntu (using UUIDs to locate the partitions), but only from hd1 for Windows, which isn't so clever.

---

### Post by thornate on 2008-12-18
Hurrah! It works now. Many thanks.

---

