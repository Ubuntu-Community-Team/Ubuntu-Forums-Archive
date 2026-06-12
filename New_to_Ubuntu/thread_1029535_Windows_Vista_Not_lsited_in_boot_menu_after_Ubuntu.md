---
title: "Windows Vista Not lsited in boot menu after Ubuntu Instalation"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by krinish on 2009-01-03
This is my first post here. Planning to try out Linux for the first time.

I had Windows XP on c: and Vista on d:

I installed Ubuntu 8.10 on C drive.

When the Installation completed there was no listing of Windows Vista in the boot menu.

When i logged into Ubuntu I found the Vista files to be intact on the d:

Here is the fdisk

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x403b403a

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4468 35889178+ 83 Linux
/dev/sda2 4469 30401 208306822+ f W95 Ext'd (LBA)
/dev/sda5 4469 9440 39937558+ 7 HPFS/NTFS
/dev/sda6 9441 19054 77224423+ 7 HPFS/NTFS
/dev/sda7 19055 30400 91136713+ b W95 FAT32
/dev/sda8 30401 30401 8001 82 Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14241423

Device Boot Start End Blocks Id System
/dev/sdb1 1 7011 56315826 7 HPFS/NTFS
/dev/sdb2 7012 30400 187872142+ 5 Extended
/dev/sdb5 7012 15935 71681998+ 7 HPFS/NTFS
/dev/sdb6 15936 23112 57649221 7 HPFS/NTFS
/dev/sdb7 23113 30400 58540828+ 7 HPFS/NTFS

I have edited

gksu gedit /boot/grub/menu.lst

to this

itle Windows Vista
rootnoverify (hd0,0) [COLOR="Red"](Changed to hd0,1 and hd0,2 and hd0,3 and tried)[/COLOR]
makeactive
savedefault
chainloader +1

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa ro single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
uuid c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa
kernel /boot/memtest86+.bin


Please help. I can only boot into Ubuntu now. How to boot into Vista. The grub doesnt have Vista listed.

SOS

krinish
(lost all sleep 1Am  :()

Im not sure if i posted this in the right forum. But i desperately need help. Once this is sorted out, I can use ubuntu and ask you more questions and post in the right forum

---

### Post by Ender41 on 2009-01-03
[QUOTE=krinish;6487209]This is my first post here. Planning to try out Linux for the first time.

I had Windows XP on c: and Vista on d:

I installed Ubuntu 8.10 on C drive.

When the Installation completed there was no listing of Windows Vista in the boot menu.

When i logged into Ubuntu I found the Vista files to be intact on the d:

Here is the fdisk

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x403b403a

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4468 35889178+ 83 Linux
/dev/sda2 4469 30401 208306822+ f W95 Ext'd (LBA)
/dev/sda5 4469 9440 39937558+ 7 HPFS/NTFS
/dev/sda6 9441 19054 77224423+ 7 HPFS/NTFS
/dev/sda7 19055 30400 91136713+ b W95 FAT32
/dev/sda8 30401 30401 8001 82 Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14241423

Device Boot Start End Blocks Id System
/dev/sdb1 1 7011 56315826 7 HPFS/NTFS
/dev/sdb2 7012 30400 187872142+ 5 Extended
/dev/sdb5 7012 15935 71681998+ 7 HPFS/NTFS
/dev/sdb6 15936 23112 57649221 7 HPFS/NTFS
/dev/sdb7 23113 30400 58540828+ 7 HPFS/NTFS

I have edited

gksu gedit /boot/grub/menu.lst

to this

itle Windows Vista
rootnoverify (hd0,0) [COLOR="Red"](Changed to hd0,1 and hd0,2 and hd0,3 and tried)[/COLOR]
makeactive
savedefault
chainloader +1

 From what I understand you to be saying though vista isn't on hd0 it is on hd1


I have vista and linux on the one drive output of fdisk -l

Disk /dev/sda: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19123   153600000    7  HPFS/NTFS
/dev/sda2           42582       43777     9606870    c  W95 FAT32 (LBA)
/dev/sda4           19124       42581   188426385    5  Extended
/dev/sda5           41854       42581     5847628+  82  Linux swap / Solaris
/dev/sda6           19124       30488    91289299+  83  Linux
/dev/sda7           30489       41853    91289331   83  Linux

My menu.1st to run vista is :

title           Vista
root            (hd0,0)
savedefault
makeactive
chainloader     +1


Windows has a tendency to want to be first of the drive and can be a bit piggy if it isn't. Have you tried hd1 instead of hd0 ?

If this doesn't work installing a third party boot manager might get vista working again

---

### Post by caljohnsmith on 2009-01-03
If Vista is on the same drive as Ubuntu, then it looks like part of the issue is that it is on a logical partition, not a primary one. But in order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by krinish on 2009-01-03
Wow soo early replies. Thanks for your help.

As requested

```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for its boot files.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63, but according to the info from fdisk, 
                       sda5 starts at sector 71778483 .
    Operating System:  Windows Vista
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63, but according to the info from fdisk, 
                       sda6 starts at sector 151653663 .
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Win_98
    Boot sector info:  According to the info in the boot sector, sda7 has 
                       182273427 sectors, but according to the info from 
                       fdisk, it has 182273426 sectors.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       112631651 sectors, but according to the info from 
                       fdisk, it has 112631652 sectors.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63, but according to the info from fdisk, 
                       sdb5 starts at sector 112631778 .
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63, but according to the info from fdisk, 
                       sdb6 starts at sector 255995838 . According to the 
                       info in the boot sector, sdb6 has 115298441 sectors, 
                       but according to the info from fdisk, it has 115298442 
                       sectors.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63, but according to the info from fdisk, 
                       sdb7 starts at sector 371294343 .
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x403b403a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    71778419    35889178+  83  Linux
/dev/sda2        71778420   488392064   208306822+   f  W95 Ext'd (LBA)
/dev/sda5        71778483   151653599    39937558+   7  HPFS/NTFS
/dev/sda6       151653663   306102509    77224423+   7  HPFS/NTFS
/dev/sda7       306102573   488375999    91136713+   b  W95 FAT32
/dev/sda8       488376063   488392064        8001   82  Linux swap / Solaris

sfdisk -V /dev/sda:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 6: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 7: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition 8: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x14241423

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   112631714    56315826    7  HPFS/NTFS
/dev/sdb2       112631715   488375999   187872142+   5  Extended
/dev/sdb5       112631778   255995774    71681998+   7  HPFS/NTFS
/dev/sdb6       255995838   371294279    57649221    7  HPFS/NTFS
/dev/sdb7       371294343   488375999    58540828+   7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition [6]: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 6: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition [7]: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 7: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa" TYPE="ext3" 
/dev/sda5: UUID="9A18163D18161939" TYPE="ntfs" 
/dev/sda6: UUID="1228DE4B28DE2E0B" TYPE="ntfs" 
/dev/sda7: UUID="1EB6-16CC" TYPE="vfat" 
/dev/sda8: UUID="42f2ade6-152d-4bc7-b39d-473a6d372b70" TYPE="swap" 
/dev/sdb1: UUID="7CDC3524DC34DA5A" TYPE="ntfs" 
/dev/sdb5: UUID="2AB88B81B88B4A71" TYPE="ntfs" 
/dev/sdb6: UUID="6A5027E45027B62B" TYPE="ntfs" 
/dev/sdb7: UUID="9254353454351D03" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/krinish/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=krinish)

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
# kopt=root=UUID=c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa

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

title Windows Vista
rootnoverify (hd0,0)
makeactive
savedefault
chainloader +1

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c8d8d073-0fe6-4aa0-8ca3-9f14d0f76faa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=42f2ade6-152d-4bc7-b39d-473a6d372b70 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 11948
drwxr-xr-x  3 root root    4096 2009-01-04 04:06 .
drwxr-xr-x 20 root root    4096 2009-01-04 04:06 ..
-rw-r--r--  1 root root  507665 2008-10-24 13:59 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 13:59 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-04 00:42 grub
-rw-r--r--  1 root root 8177322 2009-01-04 04:06 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-12 01:41 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 13:59 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 14:01 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 13:59 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-04 00:42 .
drwxr-xr-x 3 root root   4096 2009-01-04 04:06 ..
-rw-r--r-- 1 root root    197 2009-01-04 04:06 default
-rw-r--r-- 1 root root     30 2009-01-04 04:06 device.map
-rw-r--r-- 1 root root   8108 2009-01-04 04:06 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-04 04:06 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-04 04:06 installed-version
-rw-r--r-- 1 root root   8712 2009-01-04 04:06 jfs_stage1_5
-rw-r--r-- 1 root root   4390 2009-01-04 00:42 menu.lst
-rw-r--r-- 1 root root   4390 2009-01-04 00:36 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-04 04:06 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-04 04:06 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-04 04:06 stage1
-rw-r--r-- 1 root root 121460 2009-01-04 04:06 stage2
-rw-r--r-- 1 root root   9556 2009-01-04 04:06 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-03
Unfortunately it looks like you have a few things preventing you from booting Vista right now; Vista is on a logical partition (sda5), so when you installed Vista, it would have put its boot files in some primary NTFS/FAT partition. But the script you ran was not able to find your Vista boot files in any of your partitions, so you must have unintentionally deleted them at some point, maybe deleting the partition they were in when you installed Ubuntu for example. Another issue is that that your Vista partition's boot sector is an XP boot sector, i.e. it is configured to boot XP's "ntldr" rather than Vista's "bootmgr". In addition, the Vista boot sector incorrectly shows the start of your Vista partition as 63 sectors from the beginning of the HDD, whereas in reality your Vista partition is 71778483 sectors from the beginning of the HDD. 

But the good news is all of those issues should be fixable without having to resort to reinstalling Vista. :) So how about first downloading the [vista_boot_files.tar.gz]("http://www.keepandshare.com/doc/view.php?id=785254&da=y") file to your Ubuntu desktop, and then do:
```
sudo mount /dev/sda5 /mnt
cd ~/Desktop
sudo tar xvf vista_boot_files.tar.gz
sudo mv bootmgr Boot /mnt
```
Next open up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
First delete the Vista entry that you have, and then at the very end of the file, after the "END DEBIAN AUTOMAGIC KERNELS LIST" line, add:
```
title Windows Vista
rootnoverify (hd0,4)
chainloader +1
```
Next boot your Vista Install CD, go to the command line (recovery console) and do:
```
diskpart
```
And at the diskpart prompt do:
```
list volume
exit
```
Using that output, find the drive letter of your Vista partition, and then do:
```
[COLOR="Blue"]E:[/COLOR]\boot\bootsect.exe /nt60 [COLOR="Blue"]C:[/COLOR]
```
But change the C to whichever drive is the Vista partition if it is different, and also the E above should be the drive letter of your Vista Install CD, so change that too if necessary. Next do:
```
bcdedit /store [COLOR="Blue"]C:[/COLOR]\boot\bcd /set {default} osdevice boot
bcdedit /store [COLOR="Blue"]C:[/COLOR]\boot\bcd /set {default} device boot
bcdedit /store [COLOR="Blue"]C:[/COLOR]\boot\bcd /set {bootmgr} device boot
bcdedit /store [COLOR="Blue"]C:[/COLOR]\boot\bcd /set {memdiag} device boot
```
And change all the "C" references above if your Vista drive letter is different. After that, reboot, try and boot Vista from your Grub menu, and let me know exactly what happens. If you have any problems, please run the script again from post #3 and post the results. We can go from there. :)

CREDITS: Many thanks to forum member meierfra for providing the Vista boot files and all the above Vista commands.

---

