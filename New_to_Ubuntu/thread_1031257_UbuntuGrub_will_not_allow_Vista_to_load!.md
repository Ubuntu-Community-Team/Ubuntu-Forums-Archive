---
title: "Ubuntu/Grub will not allow Vista to load!"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by JamesMcIntyre on 2009-01-05
Hi all, I installed Ubuntu 8.01 on a partition with Windows Vista a couple of months ago.

I haven't really had any problem with it until now - I have still been able to access Vista by selecting the second Grub entry for "Windows Vista/Longhorn". Normally Windows would begin to boot, Blue-Screen, Restart and then I would always be able to get it on the second attempt. This was far from ideal but whatever, as long as I was still able to use Vista.

Yesterday, I used Vista like that and it was fine. Today, I started the computer and Grub auto-timed out and logged in on Ubuntu like it always does. Wishing to use Vista instead, I shut down the computer and restarted. Since then, Vista Blue-Screens EVERY TIME I try to boot it!

I am distraught, and urgently need to restore Vista's functionality, as my degree course requires me to install some Windows software by the end of the week.

I would be massively appreciative if anyone could offer some help to get Vista functional again, it's very urgent. If it helps, I'm using Ubuntu 8.04 on an Advent Laptop which came preinstalled with Vista. I will provide any other specifications or whatever if they help.

I do not have access to the Vista recovery disk/installation disk within the week (living in University halls and left it at home), otherwise I would be inclined to wipe the hard drive and reinstall both Vista and Ubuntu. There must be some way to fix this! If I can't resolve this issue within a couple of days, I'm really going to have to go and buy a new laptop, at massive expense, so that I can use the crucial course software.

Please help me!!

- James

---

### Post by ajcham on 2009-01-05
It may be a long shot, but if all else fails you could try running the software in Wine before forking out on a new laptop.

---

### Post by caljohnsmith on 2009-01-05
Since you don't have a Vista Install CD, the good news is that there is a [Vista Recovery CD]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") that you can download and use instead. How about booting that, go to the command line (recovery console), and do:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. Then try booting Vista again and see if you get any further. Also, do you have a Ubuntu Live CD? If so, please boot that, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and maybe what your Vista problem might be.

---

### Post by JamesMcIntyre on 2009-01-05
Thanks for the inputs you two!

Regarding Wine, I'm inclined not to, because the software, which cost £30, comes with a unique online registration code. I would really much rather install it on an actual Windows system just to make sure I don't mess it up. Besides, having Windows back in the long run is something I want to do just generally anyway.

CalJohnSmith:

Brilliant, thank you so much. I am downloading the Vista Recovery CD now, I will do as you instructed and post here if it works or not.

Regrettably, I do not have the Ubuntu Live CD with me at the moment, so I don't think I'll be able to try that option.

Will report back shortly on success or failure of the Recovery CD.

---

### Post by ajcham on 2009-01-05
> **JamesMcIntyre said:**
> 

Regrettably, I do not have the Ubuntu Live CD with me at the moment, so I don't think I'll be able to try that option.


Can't you download that also?  Obviously, if the recovery CD works, then it won't be necessary.

Anyway, I'll step aside.  I've been here long enough to know that when CJS steps in, my help is surplus to requirements!

---

### Post by JamesMcIntyre on 2009-01-05
Ok, I've tried to do as you say. I successfully downloaded and burnt the recovery programme, and was able to get into the menu on it, but when I tried to use it, it said it was incompatible. I put 2 and 2 together and figured I needed the 32-bit one - which I guess I did because I was able to get another menu.

When I typed chkdsk /r in the command prompt, I got a message saying something like "the drive is write protected", and it wouldn't do it.

Out of curiosity I tried the "Windows Startup Recovery" option, and it did nothing, good nor bad. Any other suggestions?

PS: Ok, I'm going to go ahead and download/burn the Live CD and get that results.txt. One sec!

---

### Post by JamesMcIntyre on 2009-01-05
I'm logged in using the LiveCD I created. Here are the contents of RESULTS.txt, created as described by caljohnsmith. If anyone is able to decipher what might be going wrong, please say!

For reference the second Windows Entry is normally the one which I use to access Vista. The first "Vista/Longhorn" entry, at least on my grub boot screen, is some kind of extra thing which was preinstalled, I guess by the retailer, and the third identical entry is just a kind of useless reiteration which has never been useable. For some reason Ubuntu displays itself twice in Grub as well. I am not really interested in resolving these minor issues, literally I will be completely happy if there is just some way I can access Vista again.

```
============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for its boot files.
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /BOOT

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3fcee1b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    19458047     9728000   27  Unknown
/dev/sda2   *    19458048    22530047     1536000    7  HPFS/NTFS
/dev/sda3        22530048   326004727   151737340    7  HPFS/NTFS
/dev/sda4       326007045   625137344   149565150    5  Extended
/dev/sda5       326007108   612911879   143452386   83  Linux
/dev/sda6       612911943   625137344     6112701   82  Linux swap / Solaris

sfdisk -V /dev/sda:

Warning: partition 1 does not end at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 4043 MB, 4043309056 bytes
125 heads, 62 sectors/track, 1018 cylinders, total 7897088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2c6b7369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  1936028272  3787887330   925929529+  68  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(116, 100, 32) logical=(249810, 12, 29)
Partition 1 has different physical/logical endings:
     phys=(288, 101, 46) logical=(488759, 81, 59)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?  1330184192  1869160479   269488144   79  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(357, 32, 43) logical=(171636, 83, 47)
Partition 2 has different physical/logical endings:
     phys=(0, 13, 10) logical=(241181, 124, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?   538989391  1937352302   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(69547, 2, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(249980, 117, 49)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?  1394627663  1394648999       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(179951, 119, 36)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(179954, 88, 44)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

sfdisk -V /dev/sdc:

Warning: partitions 1 and 3 overlap

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="CE9A8B379A8B1B5B" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="58B28C4BB28C2F94" LABEL="System" TYPE="ntfs" 
/dev/sda3: UUID="28088E6C088E38B8" LABEL="Vista" TYPE="ntfs" 
/dev/sda5: UUID="2c3bfbe0-8dd5-4630-946c-cf9a4ea2f6af" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="f835645d-e3c6-4993-b51f-dabf41fb1ff6" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc: LABEL="4 GIG" UUID="252C-2DF5" TYPE="vfat" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc on /media/4 GIG type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

================================== sda1/BOOT: ==================================

total 3616
drwxrwxrwx 1 root root       0 2008-07-25 17:26 .
drwxrwxrwx 1 root root    4096 2008-11-13 05:53 ..
-rwxrwxrwx 1 root root  262144 2008-07-25 21:42 BCD
-rwxrwxrwx 1 root root  262144 2008-07-25 21:42 BCD.LOG
-rwxrwxrwx 1 root root 3170304 2008-01-03 11:23 BOOT.SDI
-rwxrwxrwx 1 root root    2048 2008-01-05 03:23 ETFSBOOT.COM
drwxrwxrwx 1 root root       0 2008-07-25 17:26 FONTS

================================== sda2/Boot: ==================================

total 756
drwxrwxrwx 1 root root   4096 2008-07-25 21:46 .
drwxrwxrwx 1 root root   4096 2009-01-02 18:50 ..
-rwxrwxrwx 1 root root  28672 2009-01-05 22:46 BCD
-rwxrwxrwx 1 root root 262144 2009-01-05 22:46 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-02-06 16:51 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-02-06 16:51 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-02-06 16:51 bootstat.dat
drwxrwxrwx 1 root root      0 2008-07-25 21:46 cs-CZ
drwxrwxrwx 1 root root      0 2008-07-25 21:46 da-DK
drwxrwxrwx 1 root root      0 2008-07-25 21:46 de-DE
drwxrwxrwx 1 root root      0 2008-07-25 21:46 el-GR
drwxrwxrwx 1 root root      0 2008-07-25 21:46 en-US
drwxrwxrwx 1 root root      0 2008-07-25 21:46 es-ES
drwxrwxrwx 1 root root      0 2008-07-25 21:46 fi-FI
drwxrwxrwx 1 root root      0 2008-07-25 21:46 Fonts
drwxrwxrwx 1 root root      0 2008-07-25 21:46 fr-FR
drwxrwxrwx 1 root root      0 2008-07-25 21:46 hu-HU
drwxrwxrwx 1 root root      0 2008-07-25 21:46 it-IT
drwxrwxrwx 1 root root      0 2008-07-25 21:46 ja-JP
drwxrwxrwx 1 root root      0 2008-07-25 21:46 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-21 02:23 memtest.exe
drwxrwxrwx 1 root root      0 2008-07-25 21:46 nb-NO
drwxrwxrwx 1 root root      0 2008-07-25 21:46 nl-NL
drwxrwxrwx 1 root root      0 2008-07-25 21:46 pl-PL
drwxrwxrwx 1 root root      0 2008-07-25 21:46 pt-BR
drwxrwxrwx 1 root root      0 2008-07-25 21:46 pt-PT
drwxrwxrwx 1 root root      0 2008-07-25 21:46 ru-RU
drwxrwxrwx 1 root root      0 2008-07-25 21:46 sv-SE
drwxrwxrwx 1 root root      0 2008-07-25 21:46 tr-TR
drwxrwxrwx 1 root root      0 2008-07-25 21:46 zh-CN
drwxrwxrwx 1 root root      0 2008-07-25 21:46 zh-HK
drwxrwxrwx 1 root root      0 2008-07-25 21:46 zh-TW

================================== sda3/Boot: ==================================

total 756
drwxrwxrwx 1 root root   4096 2008-02-06 16:51 .
drwxrwxrwx 1 root root   8192 2009-01-02 18:51 ..
-rwxrwxrwx 1 root root  24576 2008-07-25 11:04 BCD
-rwxrwxrwx 1 root root 262144 2008-07-25 11:04 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-02-06 16:51 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-02-06 16:51 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-02-06 16:51 bootstat.dat
drwxrwxrwx 1 root root      0 2008-02-06 16:51 cs-CZ
drwxrwxrwx 1 root root      0 2008-02-06 16:51 da-DK
drwxrwxrwx 1 root root      0 2008-02-06 16:51 de-DE
drwxrwxrwx 1 root root      0 2008-02-06 16:51 el-GR
drwxrwxrwx 1 root root      0 2008-02-06 16:51 en-US
drwxrwxrwx 1 root root      0 2008-02-06 16:51 es-ES
drwxrwxrwx 1 root root      0 2008-02-06 16:51 fi-FI
drwxrwxrwx 1 root root      0 2008-02-06 16:51 Fonts
drwxrwxrwx 1 root root      0 2008-02-06 16:51 fr-FR
drwxrwxrwx 1 root root      0 2008-02-06 16:51 hu-HU
drwxrwxrwx 1 root root      0 2008-02-06 16:51 it-IT
drwxrwxrwx 1 root root      0 2008-02-06 16:51 ja-JP
drwxrwxrwx 1 root root      0 2008-02-06 16:51 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-21 02:23 memtest.exe
drwxrwxrwx 1 root root      0 2008-02-06 16:51 nb-NO
drwxrwxrwx 1 root root      0 2008-02-06 16:51 nl-NL
drwxrwxrwx 1 root root      0 2008-02-06 16:51 pl-PL
drwxrwxrwx 1 root root      0 2008-02-06 16:51 pt-BR
drwxrwxrwx 1 root root      0 2008-02-06 16:51 pt-PT
drwxrwxrwx 1 root root      0 2008-02-06 16:51 ru-RU
drwxrwxrwx 1 root root      0 2008-02-06 16:51 sv-SE
drwxrwxrwx 1 root root      0 2008-02-06 16:51 tr-TR
drwxrwxrwx 1 root root      0 2008-02-06 16:51 zh-CN
drwxrwxrwx 1 root root      0 2008-02-06 16:51 zh-HK
drwxrwxrwx 1 root root      0 2008-02-06 16:51 zh-TW

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
# kopt=root=UUID=2c3bfbe0-8dd5-4630-946c-cf9a4ea2f6af ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2c3bfbe0-8dd5-4630-946c-cf9a4ea2f6af ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2c3bfbe0-8dd5-4630-946c-cf9a4ea2f6af ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2c3bfbe0-8dd5-4630-946c-cf9a4ea2f6af ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2c3bfbe0-8dd5-4630-946c-cf9a4ea2f6af ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2c3bfbe0-8dd5-4630-946c-cf9a4ea2f6af /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f835645d-e3c6-4993-b51f-dabf41fb1ff6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda5/boot: ==================================

total 38048
drwxr-xr-x  3 root root      4096 2008-10-15 15:09 .
drwxr-xr-x 22 root root      4096 2008-10-15 15:04 ..
-rw-r--r--  1 root root    420224 2008-08-20 22:15 abi-2.6.24-19-generic
-rw-r--r--  1 root root    420338 2008-08-25 19:39 abi-2.6.24-21-generic
-rw-r--r--  1 root root     74164 2008-08-20 22:15 config-2.6.24-19-generic
-rw-r--r--  1 root root     74188 2008-08-25 19:39 config-2.6.24-21-generic
drwxr-xr-x  2 root ubuntu    4096 2008-10-15 15:04 grub
-rw-r--r--  1 root root   7736582 2008-10-15 15:04 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root ubuntu 8409230 2008-09-27 15:10 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root   7738341 2008-10-15 15:09 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root   7738457 2008-10-15 15:04 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root    103204 2007-09-28 11:03 memtest86+.bin
-rw-r--r--  1 root root   1152364 2008-08-20 22:15 System.map-2.6.24-19-generic
-rw-r--r--  1 root root   1152893 2008-08-25 19:39 System.map-2.6.24-21-generic
-rw-r--r--  1 root root   1903096 2008-08-20 22:15 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root   1905624 2008-08-25 19:39 vmlinuz-2.6.24-21-generic

=============================== sda5/boot/grub: ===============================

total 212
drwxr-xr-x 2 root ubuntu   4096 2008-10-15 15:04 .
drwxr-xr-x 3 root root     4096 2008-10-15 15:09 ..
-rw-r--r-- 1 root ubuntu    197 2008-09-27 15:10 default
-rw-r--r-- 1 root ubuntu     15 2008-09-27 15:10 device.map
-rw-r--r-- 1 root ubuntu   8056 2008-09-27 15:10 e2fs_stage1_5
-rw-r--r-- 1 root ubuntu   7904 2008-09-27 15:10 fat_stage1_5
-rw-r--r-- 1 root ubuntu     16 2008-09-27 15:10 installed-version
-rw-r--r-- 1 root ubuntu   8608 2008-09-27 15:10 jfs_stage1_5
-rw-r--r-- 1 root root     5380 2008-10-15 15:04 menu.lst
-rw-r--r-- 1 root root     5294 2008-10-15 15:04 menu.lst~
-rw-r--r-- 1 root ubuntu   7324 2008-09-27 15:10 minix_stage1_5
-rw-r--r-- 1 root ubuntu   9632 2008-09-27 15:10 reiserfs_stage1_5
-rw-r--r-- 1 root ubuntu    512 2008-09-27 15:10 stage1
-rw-r--r-- 1 root ubuntu 108356 2008-09-27 15:10 stage2
-rw-r--r-- 1 root ubuntu   9276 2008-09-27 15:10 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown MBR on /dev/sdc

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 08 26 00  |.X.MSWIN4.1...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 80 78 00 11 1e 00 00  00 00 00 00 02 00 00 00  |..x.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f5 2d 2c 25 4e  4f 20 4e 41 4d 45 20 20  |..).-,%NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa 33 c9 8e d1 bc  |  FAT32   .3....|
00000060  f8 7b 8e c1 bd 78 00 c5  76 00 1e 56 16 55 bf 22  |.{...x..v..V.U."|
00000070  05 89 7e 00 89 4e 02 b1  0b fc f3 a4 8e d9 bd 00  |..~..N..........|
00000080  7c c6 45 fe 0f 8b 46 18  88 45 f9 38 4e 40 7d 25  ||.E...F..E.8N@}%|
00000090  8b c1 99 bb 00 07 e8 97  00 72 1a 83 eb 3a 66 a1  |.........r...:f.|
000000a0  1c 7c 66 3b 07 8a 57 fc  75 06 80 ca 02 88 56 02  |.|f;..W.u.....V.|
000000b0  80 c3 10 73 ed bf 02 00  83 7e 16 00 75 45 8b 46  |...s.....~..uE.F|
000000c0  1c 8b 56 1e b9 03 00 49  40 75 01 42 bb 00 7e e8  |..V....I@u.B..~.|
000000d0  5f 00 73 26 b0 f8 4f 74  1d 8b 46 32 33 d2 b9 03  |_.s&..Ot..F23...|
000000e0  00 3b c8 77 1e 8b 76 0e  3b ce 73 17 2b f1 03 46  |.;.w..v.;.s.+..F|
000000f0  1c 13 56 1e eb d1 73 0b  eb 27 83 7e 2a 00 77 03  |..V...s..'.~*.w.|
00000100  e9 fd 02 be 7e 7d ac 98  03 f0 ac 84 c0 74 17 3c  |....~}.......t.<|
00000110  ff 74 09 b4 0e bb 07 00  cd 10 eb ee be 81 7d eb  |.t............}.|
00000120  e5 be 7f 7d eb e0 98 cd  16 5e 1f 66 8f 04 cd 19  |...}.....^.f....|
00000130  41 56 66 6a 00 52 50 06  53 6a 01 6a 10 8b f4 60  |AVfj.RP.Sj.j...`|
00000140  80 7e 02 0e 75 04 b4 42  eb 1d 91 92 33 d2 f7 76  |.~..u..B....3..v|
00000150  18 91 f7 76 18 42 87 ca  f7 76 1a 8a f2 8a e8 c0  |...v.B...v......|
00000160  cc 02 0a cc b8 01 02 8a  56 40 cd 13 61 8d 64 10  |........V@..a.d.|
00000170  5e 72 0a 40 75 01 42 03  5e 0b 49 75 b4 c3 03 18  |^r.@u.B.^.Iu....|
00000180  01 27 0d 0a 49 6e 76 61  6c 69 64 20 73 79 73 74  |.'..Invalid syst|
00000190  65 6d 20 64 69 73 6b ff  0d 0a 44 69 73 6b 20 49  |em disk...Disk I|
000001a0  2f 4f 20 65 72 72 6f 72  ff 0d 0a 52 65 70 6c 61  |/O error...Repla|
000001b0  63 65 20 74 68 65 20 64  69 73 6b 2c 20 61 6e 64  |ce the disk, and|
000001c0  20 74 68 65 6e 20 70 72  65 73 73 20 61 6e 79 20  | then press any |
000001d0  6b 65 79 0d 0a 00 00 00  49 4f 20 20 20 20 20 20  |key.....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7e 01  |SYSMSDOS   SYS~.|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200


=============================== StdErr Messages: ===============================

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
```

---

### Post by caljohnsmith on 2009-01-05
Getting a "drive is write protected" error certainly seems strange, I'm wondering if chkdsk tried to instead run on your 4 GB USB stick. How about booting the Vista CD again, but this time at the command prompt try:
```
diskpart
```
And at the diskpart prompt do:
```
list volume
exit
```
Find the drive letter of your sda2 Vista install (2nd partition), and then run the chkdsk with:
```
chkdsk /r C:
```
And change "C" to whichever is the Vista drive letter. Please let me know if that works or not.

---

### Post by JamesMcIntyre on 2009-01-05
Ok, the Vista partition is D:, so I did chkdsk there like you said. It did its stuff, and returned "windows has checked the file system and found no problems".

By the way, something which might help. The Blue Screen of Death which windows produces during booting, post-grub, is too fast to read entirely, but the last few words are "dynamic link library HAL.DLL". I'm a layman, but I googled that term and apparently errors to do with that dll are boot-related (for straight up windows systems with no partitions or anything, a recommended fix had to do with boot.ini). I hope this narrows it down - I'm pretty sure the problem is grub-related because of the nature of the error message. Perhaps there's some kind of troubleshooting I can do for the Grub loader?

Edit: Or, some way to repair boot.ini and hal.dll (the Windows ones) safely? That seems to be something like a plan, but I would not have the faintest idea how to do either of these.

---

### Post by caljohnsmith on 2009-01-05
> **JamesMcIntyre said:**
> Ok, the Vista partition is D:, so I did chkdsk there like you said. It did its stuff, and returned "windows has checked the file system and found no problems".

By the way, something which might help. The Blue Screen of Death which windows produces during booting, post-grub, is too fast to read entirely, but the last few words are "dynamic link library HAL.DLL". I'm a layman, but I googled that term and apparently errors to do with that dll are boot-related (for straight up windows systems with no partitions or anything, a recommended fix had to do with boot.ini). I hope this narrows it down - I'm pretty sure the problem is grub-related because of the nature of the error message. Perhaps there's some kind of troubleshooting I can do for the Grub loader?
I think you most likely have a Windows problem rather than a Grub problem at this point; one thing that is not clear is you have three NTFS partitions, all of which have Vista boot files in them. The first sda1 NTFS partition looks like it might be a typical Vista recovery partition based on its size and the fact that it is the first partition, and your sda2 NTFS partition is only 1.5 GB, so that can't be the full Vista install. Yet you said you used the 2nd Vista Grub entry to boot Vista, and that entry would boot the sda2 partition. It looks almost certain that your Vista is actually on sda3, but it would have been possible to boot Vista from sda2 if the Vista sda2 boot files were configured correctly to boot Vista on sda3. I think it would be a good idea to get a clearer picture of your strange Vista boot setup at this point, so how about posting the output of:
```
sudo mkdir /mnt/sda1 /mnt/sda2 /mnt/sda3
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
sudo mount /dev/sda3 /mnt/sda3
ls -l /mnt/sda1 /mnt/sda2 /mnt/sda3
```
And in the meantime, go ahead and boot the Vista Recovery CD again, but this time run "chkdsk" on the sda3 partition since that is the main Vista partition. Let me know what results you get from that, and we can go from there.

---

### Post by JamesMcIntyre on 2009-01-05
Heres the output of the code you posted:

```
/mnt/sda1:
total 344
drwxrwxrwx 1 root root      0 2008-07-25 18:26 BOOT
-rwxrwxrwx 1 root root 333203 2008-01-18 23:45 BOOTMGR
-rwxrwxrwx 1 root root      0 2006-11-10 13:45 hdd
drwxrwxrwx 1 root root      0 2008-07-25 22:34 ImageLayout
drwxrwxrwx 1 root root      0 2008-07-25 22:42 ISO2
drwxrwxrwx 1 root root      0 2008-01-19 08:45 ProgramData
drwxrwxrwx 1 root root      0 2008-01-19 08:45 Program Files
drwxrwxrwx 1 root root   4096 2008-04-30 10:37 sources
drwxrwxrwx 1 root root      0 2008-09-24 15:42 System Volume Information
drwxrwxrwx 1 root root   4096 2008-07-25 18:28 tgm
drwxrwxrwx 1 root root      0 2008-01-19 08:45 Users
drwxrwxrwx 1 root root   8192 2009-01-05 21:19 Windows

/mnt/sda2:
total 332
drwxrwxrwx 1 root root   4096 2008-07-25 22:46 Boot
-rwxrwxrwx 1 root root 333203 2008-01-21 02:24 bootmgr
drwxrwxrwx 1 root root      0 2008-09-25 00:30 $RECYCLE.BIN
drwxrwxrwx 1 root root      0 2008-09-24 15:42 System Volume Information

/mnt/sda3:
total 6576495
drwxrwxrwx 1 root root          0 2008-07-25 11:49 Applications
-rwxrwxrwx 1 root root         24 2006-09-18 22:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2008-02-06 16:51 Boot
-rwxrwxrwx 1 root root     333203 2008-01-21 02:24 bootmgr
-rwxrwxrwx 1 root root       8192 2008-02-06 16:51 BOOTSECT.BAK
-rwxrwxrwx 2 root root         10 2006-09-18 22:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 13:02 Documents and Settings
-rwxrwxrwx 1 root root 3209121792 2009-01-02 18:50 hiberfil.sys
drwxrwxrwx 1 root root          0 2008-07-25 10:53 Intel
-rwxrwxrwx 1 root root        369 2008-11-21 09:40 IPH.PH
drwxrwxrwx 1 root root          0 2008-07-25 11:50 MSOCache
-rwxrwxrwx 1 root root 3524792320 2009-01-02 18:50 pagefile.sys
drwxrwxrwx 1 root root          0 2008-01-21 02:32 PerfLogs
drwxrwxrwx 1 root root       4096 2008-11-21 09:40 ProgramData
drwxrwxrwx 1 root root      12288 2008-12-17 06:15 Program Files
drwxrwxrwx 1 root root          0 2008-09-25 00:30 $Recycle.Bin
-rwxrwxrwx 2 root root        268 2008-07-25 12:00 sqmdata00.sqm
-rwxrwxrwx 2 root root        244 2008-07-25 12:00 sqmnoopt00.sqm
drwxrwxrwx 1 root root      20480 2009-01-05 21:23 System Volume Information
drwxrwxrwx 1 root root       4096 2008-09-25 00:28 Users
drwxrwxrwx 1 root root      24576 2009-01-05 21:23 Windows

```

I'll do the chkdisk for partition 3 one sec. 

As a contingency plan, I have a technical question regarding Windows reinstallation - say, as a last resort, I just reformat my hard drive and want to do a clean Vista install. Can I use a disk which is not mine? Other people in my building have Vista CDs with them. Is there a way I could use my own product key (which I don't know, but which I think is written on the bottom of my laptop) to install from a disk which is not my own? This is only a last resort, but really I need to know if I can do this if all else fails.

I'll just run chkdsk again now like you said.

---

### Post by JamesMcIntyre on 2009-01-05
Ok, on the CHKDSK front, diskpart -> List Volume decided that Volume 3 was the DVD-ROM. I guessed that "System" (C:) which was about 150 GB or something, must be the "real" vista, so I did chkdsk /r on that instead and it did the same as before, basically saying it checked the file system and found no problems.

---

### Post by caljohnsmith on 2009-01-05
> **JamesMcIntyre said:**
> 
As a contingency plan, I have a technical question regarding Windows reinstallation - say, as a last resort, I just reformat my hard drive and want to do a clean Vista install. Can I use a disk which is not mine? Other people in my building have Vista CDs with them. Is there a way I could use my own product key (which I don't know, but which I think is written on the bottom of my laptop) to install from a disk which is not my own? This is only a last resort, but really I need to know if I can do this if all else fails.

If you can find your Vista product key somewhere, then I think you should be able to use someone else's Vista Install CD to install Vista but with your product key. Anyway, it is clear now that Vista is definitely on sda3, and since the chkdsk didn't help, can you go ahead and borrow one of your friend's Vista CDs and do a "Vista Repair"? That might be enough to get your Vista booting again, and would save having to do a complete reinstall. Good luck and let me know how it goes. :)

---

### Post by JamesMcIntyre on 2009-01-08
I'm afraid you aren't going to like what I have to say, but I may as well give this thread closure.

I reformatted my hard-drive and did a clean reinstall from a friend's disk - Vista only. For now at least, I'm done with Ubuntu. As a student whose honours degree depends on my ability to word-process essays and make sure they're in on the deadline, I simply cannot deal with the system instability which dual-booting with Ubuntu apparently entails.

Though I did not previously mention this as it was not salient to the problem, no Ubuntu sound drivers apparently exist for my laptop yet either, so that was another major functionality which was missing. I'll be honest, I had already all but stopped using Ubuntu altogether, primarily for this reason.

Sorry to bail out on you all, but I have neither the technical knowledge nor the patience to make running Ubuntu worthwhile for somebody in my position.

Thanks massively to caljohnsmith et al for their help regarding my problem.

- James

---

### Post by mailbuntu on 2009-01-09
hi everyone

I'm trying to dual boot ubuntu (with vista installed first).

I was following this and [guide]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") and [this one]("http://neosmart.net/wiki/display/EBCD/Ubuntu").

I got to the point where the Grub boot loader shows everything: ubuntu, ubuntu (recovery mode) and vista longhorn (loader) but when I choose vista longhorn (loader), my computer reboots (like when we do a usual restart), then it takes me to the Grub loader menu again, zero changes :(


The closest I got was: when i click on Vista longhorn (loader) it shows Windows is Starting...but i never gets to anywhere further than that.


Could you please help me with this?

---

### Post by mailbuntu on 2009-01-09
using the command caljohnsmith has given above; here is the content of RESULTS.txt. Hope this helps. Cheers

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /grldr /Boot

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda3: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d2d1d2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   147460634    73730286    7  HPFS/NTFS
/dev/sda2       147460635   230532749    41536057+  83  Linux
/dev/sda3       230532750   234436544     1951897+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 999 MB, 999817216 bytes
21 heads, 20 sectors/track, 4649 cylinders, total 1952768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         254     1952767      976257    6  FAT16

sfdisk -V /dev/sdb:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="587022157021FB00" TYPE="ntfs" 
/dev/sda2: UUID="716e33b3-eceb-4848-9026-0817e93df251" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="0fa63923-02e8-4360-a64f-a215e9f02896" 
/dev/sdb1: SEC_TYPE="msdos" UUID="1ED5-4570" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/illusionist/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=illusionist)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

================================== sda1/Boot: ==================================

total 504
drwxrwxrwx 1 root root   4096 2009-01-12 01:02 .
drwxrwxrwx 1 root root   8192 2009-01-11 06:49 ..
-rwxrwxrwx 1 root root  24576 2009-01-12 17:01 BCD
-rwxrwxrwx 1 root root  21504 2009-01-12 17:01 BCD.LOG
-rwxrwxrwx 2 root root      0 2009-01-12 01:02 BCD.LOG1
-rwxrwxrwx 2 root root      0 2009-01-12 01:02 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2009-01-12 01:02 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-12 01:02 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-12 01:02 da-DK
drwxrwxrwx 1 root root      0 2009-01-12 01:02 de-DE
drwxrwxrwx 1 root root      0 2009-01-12 01:02 el-GR
drwxrwxrwx 1 root root      0 2009-01-12 01:02 en-US
drwxrwxrwx 1 root root      0 2009-01-12 01:02 es-ES
drwxrwxrwx 1 root root      0 2009-01-12 01:02 fi-FI
drwxrwxrwx 1 root root      0 2009-01-12 01:02 Fonts
drwxrwxrwx 1 root root      0 2009-01-12 01:02 fr-FR
drwxrwxrwx 1 root root      0 2009-01-12 01:02 hu-HU
drwxrwxrwx 1 root root      0 2009-01-12 01:02 it-IT
drwxrwxrwx 1 root root      0 2009-01-12 01:02 ja-JP
drwxrwxrwx 1 root root      0 2009-01-12 01:02 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 20:21 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-12 01:02 nb-NO
drwxrwxrwx 1 root root      0 2009-01-12 01:02 nl-NL
drwxrwxrwx 1 root root      0 2009-01-12 01:02 pl-PL
drwxrwxrwx 1 root root      0 2009-01-12 01:02 pt-BR
drwxrwxrwx 1 root root      0 2009-01-12 01:02 pt-PT
drwxrwxrwx 1 root root      0 2009-01-12 01:02 ru-RU
drwxrwxrwx 1 root root      0 2009-01-12 01:02 sv-SE
drwxrwxrwx 1 root root      0 2009-01-12 01:02 tr-TR
drwxrwxrwx 1 root root      0 2009-01-12 01:02 zh-CN
drwxrwxrwx 1 root root      0 2009-01-12 01:02 zh-HK
drwxrwxrwx 1 root root      0 2009-01-12 01:02 zh-TW

=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=716e33b3-eceb-4848-9026-0817e93df251 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=716e33b3-eceb-4848-9026-0817e93df251

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
uuid		716e33b3-eceb-4848-9026-0817e93df251
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=716e33b3-eceb-4848-9026-0817e93df251 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		716e33b3-eceb-4848-9026-0817e93df251
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=716e33b3-eceb-4848-9026-0817e93df251 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		716e33b3-eceb-4848-9026-0817e93df251
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root       (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=716e33b3-eceb-4848-9026-0817e93df251 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=0fa63923-02e8-4360-a64f-a215e9f02896 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda2/boot: ==================================

total 11948
drwxr-xr-x  3 root root    4096 2009-01-11 22:09 .
drwxr-xr-x 20 root root    4096 2009-01-11 22:09 ..
-rw-r--r--  1 root root  507665 2008-10-24 18:59 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 18:59 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-09 19:33 grub
-rw-r--r--  1 root root 8178763 2009-01-11 22:09 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-12 05:41 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 18:59 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 19:01 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 18:59 vmlinuz-2.6.27-7-generic

=============================== sda2/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-09 19:33 .
drwxr-xr-x 3 root root   4096 2009-01-11 22:09 ..
-rw-r--r-- 1 root root    197 2009-01-11 22:09 default
-rw-r--r-- 1 root root     15 2009-01-11 22:09 device.map
-rw-r--r-- 1 root root   8108 2009-01-11 22:09 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-11 22:09 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-11 22:09 installed-version
-rw-r--r-- 1 root root   8712 2009-01-11 22:09 jfs_stage1_5
-rw-r--r-- 1 root root   4646 2009-01-09 19:33 menu.lst
-rw-r--r-- 1 root root   4607 2009-01-11 23:39 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-11 22:09 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-11 22:09 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-11 22:09 stage1
-rw-r--r-- 1 root root 121460 2009-01-11 22:09 stage2
-rw-r--r-- 1 root root   9556 2009-01-11 22:09 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-09
It looks like at least part of your Vista booting problem is because the Grub entry for Vista is not correct. How about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change the Vista entry at the bottom to:
```
title Windows Vista
root (hd0,0)
chainloader +1
```
Then reboot, try Vista again from the Grub menu, and let me know exactly what happens; we can work from there. :)

---

### Post by mailbuntu on 2009-01-09
hi caljohnsmith

thanks for takin a look at it :)

I just copy and paste what u typed, vista will not boot still :(

I could see "Starting now" flashes very quickly then my computer reboots and stops when it reaches the Grub boot loader.

---

### Post by caljohnsmith on 2009-01-09
It sounds like you may have a Vista problem rather than a Grub problem at this point, Mailbuntu. Do you have a Vista Install CD? If so, I would boot that, go to the command line (recovery console) and do:
```
bootrec /rebuildbcd
bootrec /fixboot
chkdsk /r
```
And run the chkdsk command as many times as it takes until it reports no errors. If you don't happen to have your Vista Install CD handy, you can instead download and use a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). After doing the above commands, reboot, and let me know exactly what happens when you try Vista from the Grub menu again; we can work from there. :)

---

### Post by mailbuntu on 2009-01-09
hi caljohnsmith,


I used Vista install cd to boot,

i could run the 1st two command but the 3rd one gave me this error:

This type of the file system is NTFS
Cannot lock current drive
Windows cannot run disk checkin on this volume because it is write protected.

and tat error msg doesnt seem to go away no matter how many times i type :)

hope this helps.

edited:

i just tried to boot vista from Grub,

now its displayin a black screen with "Starting up..." on top. doesnt seem like its bootin up

---

### Post by caljohnsmith on 2009-01-09
OK, so even though you couldn't run the chkdsk command, and since you could run the other two commands, did you by chance try to boot Vista again? If not, please try and let me know what happens. If you get the same behavior, how about booting into Ubuntu and do:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```
And please post the output. Note that ntfsfix is not the same as chkdsk, but it might help remove the "lock" on your Vista partition that makes it write-protected, but I don't know for sure. It shouldn't hurt your Vista partition though, so how about try it, and if it says it completed successfully, try running "chkdsk /r" from the Vista CD again. Also, when you run the chkdsk command, if it gives you a choice to force "dismount" the volume, say yes. Let me know how that goes.

---

### Post by mailbuntu on 2009-01-09
hi caljohnsmith,

After having executed successfully two out of those 3 commands I did try to boot vista again from Grub. This time i get a black screeen with "Starting up..." at the top, but it doesnt seem like its bootin up.

anyways, i tried the other comamnds from ur previous post, i got this:

```
illusionist@illusionist-desktop:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ntfsprogs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ntfsprogs has no installation candidate
illusionist@illusionist-desktop:~$ sudo ntfsfix /dev/sda1
sudo: ntfsfix: command not found
illusionist@illusionist-desktop:~$ 
illusionist@illusionist-desktop:~$ 
```

cheers

---

### Post by caljohnsmith on 2009-01-09
It looks like maybe you don't have all your repositories enabled; how about opening System > Admin > Software Sources, and check the boxes to enable all the repositories under the "Ubuntu Software" tab. Then try installing the ntfsprogs again. Also, when you ran the chkdsk command, did it give you an option to force dismount the Vista partition?

---

### Post by matey3 on 2009-01-09
I know you formatted the drive but I was just wondering anyone else in the same situation could hit F8 and enter the Safe Mode right after selecting Vista?
Just curious if that would work? or would he still get the blue screen and HAL error??
(i think hardware abstract layer usually gets semi-by passed in safe mode thats why i asked).
Thanks for the replies, I learned a lot here.

---

### Post by mailbuntu on 2009-01-09
hi

I managed to install ntfsprogs, and i did sudo ntfsfix /dev/sda1 too.
am gonna try chkdsk in the vista repairing thingy now. I'll get back to u asap :)

---

### Post by mailbuntu on 2009-01-09
hi caljohnsmith,
this is the output after i did sudo ntfsfix /dev/sda1

```
sillusionist@illusionist-desktop:~$ sudo ntfsfix /dev/sda1
[sudo] password for illusionist: 
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.
illusionist@illusionist-desktop:~$ 
```

However, I still couldnt do chkdsk /r

it gave me the same error :(

@matey3, are u askin about my case? no, am not able to get into safe mode as my vista wont boot up :|

never mind, my bad haha

---

### Post by mailbuntu on 2009-01-09
hi caljohnsmith,

what else you reckon I can try?? I just had another go, I still cannot do chkdsk /r :(

it gave me the same error as before.

cheers

---

### Post by caljohnsmith on 2009-01-09
So chkdsk didn't give you an option to dismount the Vista partition? I noticed from the script output that you have "grldr" in your Vista root directory which is Grub4DOS's boot loader. Were you experimenting with Grub4DOS at some point? If so, what did you do? Or I think grldr might have come with the EasyBCD program you tried, because EasyBCD uses "NeoGrub" which is a derivative of Grub4DOS I think. In Ubuntu, please post the output of:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
Also, to make sure your Vista boot loader has been reset properly, how about trying the following commands from your Vista CD:
```
bcdedit /store C:\boot\bcd /set {default} osdevice boot
bcdedit /store C:\boot\bcd /set {default} device boot
bcdedit /store C:\boot\bcd /set {bootmgr} device boot
bcdedit /store C:\boot\bcd /set {memdiag} device boot

```
Let me know if you get any errors, and if not, try booting Vista again and let me know exactly what happens. We can go from there.

---

### Post by mailbuntu on 2009-01-09
hi

after i did sudo mount /dev/sda1 /mnt && ls -l /mnt, i got this

```
illusionist@illusionist-desktop:~$ sudo mount /dev/sda1 /mnt && ls -l /mnt
[sudo] password for illusionist: 
total 2401905
-rwxrwxrwx 1 root root         24 2006-09-19 07:13 autoexec.bat
drwxrwxrwx 1 root root       4096 2009-01-12 01:02 Boot
-rwxrwxrwx 1 root root     438840 2006-11-02 20:23 bootmgr
-rwxrwxrwx 1 root root       8192 2009-01-12 01:02 BOOTSECT.BAK
-rwxrwxrwx 2 root root         10 2006-09-19 07:13 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 23:30 Documents and Settings
-rwxrwxrwx 1 root root     171136 2008-04-17 01:36 grldr
-rwxrwxrwx 1 root root 1072484352 2009-01-11 06:50 hiberfil.sys
-rwxrwxrwx 1 root root 1386409984 2009-01-11 06:50 pagefile.sys
drwxrwxrwx 1 root root       4096 2006-11-02 23:30 ProgramData
drwxrwxrwx 1 root root       4096 2006-11-02 23:30 Program Files
drwxrwxrwx 1 root root          0 2009-01-11 06:45 $Recycle.Bin
drwxrwxrwx 1 root root          0 2009-01-11 06:05 System Volume Information
drwxrwxrwx 1 root root       4096 2009-01-11 06:45 Users
drwxrwxrwx 1 root root      16384 2009-01-11 06:07 Windows
illusionist@illusionist-desktop:~$ 
```

I have no clues about Grub4DOS's existence whatsoever :)

Im gonna have to restart, I'll get back to u asap.

cheers

---

### Post by mailbuntu on 2009-01-09
hi

after tyepin bcdedit /store C:\boot\bcd /set {default} osdevice boot

I got this msg: The element data type specified iis not recognised or does not apply to the specified entry.

thanks for ur time! I really appreciate it.

edited: instead of osdevice, i typed csdevice :( haha

am gonna type in the rest. sorrry about tat

---

### Post by mailbuntu on 2009-01-09
okay, all 4 executed successfully.

Ive also tried to boot up vista. I get the same back screen with "Starting up..." on top.

I'd edit my post but it'd be hard for u to read, so am posstin a differnt reply. :)

cheers

---

### Post by caljohnsmith on 2009-01-09
Hmmmm. According to the script you ran, it appears that your Vista boot sector is OK, but Vista's booting behavior might suggest otherwise; how about checking your Vista boot sector by doing:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows Vista sda1 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows Vista from the Grub menu. Or if testdisk says that the boot sectors are identical and does not give you an option to "Rebuild BS", let me know. We can work from there.

---

### Post by mailbuntu on 2009-01-09
its saying tat "Extrapolated boot sctor and current boot sector are indentical."

cheers

---

### Post by caljohnsmith on 2009-01-09
I'm going to have to ask a friend who knows a lot about Vista to offer his advice for your situation, because I've never run into a "cannot lock current drive" error myself when running chkdsk. I'll ask him to get back to you at his earliest convenience, which will probably be some time today. Sorry I can't help you any further at the moment, but I'm not sure what might be causing your "cannot lock current drive" error. :)

---

### Post by mailbuntu on 2009-01-09
no, no, dun say that. uve helped me heaps, am learning hehe :)
I really appreciate for what uve done :) Thanks from Australia hehe

its 3am in Australia now :|I better get some sleep and deal with this dual boot as soon as I get up.

cya

---

### Post by matey3 on 2009-01-09
mailbuntu
thanks for the reply. I was just wondering!

I have had grub problems before, it usually happens when I installed a new program like xen, somehow the grub menu changes and refers to wrong partition. 
for instance if it is supposed to be hda2 , 0 it changes itself into hda0 , 0 or some other number(s)?

I think it is a good idea to go ahead for everyone and save a copy of the original/working menu.lst under /boot/grub in a safe place if you dont feel like editing the menu file every time. 
Although I dont think it is the case in here (bcs Ubuntu boots fine) but any way I am also new but have seen that error at least on 3 diff. machines so far.

---

### Post by caljohnsmith on 2009-01-09
Mailbuntu, when you get around to it, my friend suggested to try the following:
```
chkdsk C:
```
from the Vista Install CD; that won't actually attempt to fix anything, but it will return the current status of the partition. That may give a clue why you previously got the lock error.

---

