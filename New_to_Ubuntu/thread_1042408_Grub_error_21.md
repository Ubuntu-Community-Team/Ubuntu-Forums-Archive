---
title: "Grub error 21"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Dr.Fritz on 2009-01-17
hello guys and thanks for your attention ,
i just did a new install anyways here is some helpfull information :
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /grldr /ntldr /NTDETECT.COM /Boot

sdb1: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  Geometry: 16 Heads and 63 sectors per Track.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sdc2 
                       and looks at sector 48414783 of the same hard drive 
                       for the stage2 file and on partition #2 for 
                       /boot/grub/menu.lst .
    Operating System:  Linux Mint 6 Felicia
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc4: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9faa9faa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    75778604    37889271    7  HPFS/NTFS

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6a43a8b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            1008   781422767   390710880    f  W95 Ext'd (LBA)
/dev/sdb5            1071   781422767   390710848+   7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: partition 1 extends past end of disk

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f8001b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1        77674275   165035744    43680735    7  HPFS/NTFS
/dev/sdc2   *          63    73577699    36788818+  83  Linux
/dev/sdc3       165035745  1250258624   542611440    7  HPFS/NTFS
/dev/sdc4        73577700    77674274     2048287+  82  Linux swap / Solaris

Partition table entries are not in disk order

sfdisk -V /dev/sdc:

/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3000B10C00B0D9D4" LABEL="XP" TYPE="ntfs" 
/dev/sdb5: UUID="F468C50E68C4D092" LABEL="Data" TYPE="ntfs" 
/dev/sdc1: UUID="146BBDAD65096E93" LABEL="Vista" TYPE="ntfs" 
/dev/sdc2: UUID="c5abbc16-a5cc-4cc9-986e-1fd3027a0cfd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="2FD7306676E75597" LABEL="Data2" TYPE="ntfs" 
/dev/sdc4: TYPE="swap" UUID="56ea3085-3927-48cb-ab66-62e4580b8686" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mint/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mint)

================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


================================== sda1/Boot: ==================================

total 540
drwxrwxrwx 1 root root   4096 2008-10-27 18:09 .
drwxrwxrwx 1 root root  24576 2009-01-11 16:45 ..
-rwxrwxrwx 1 root root  24576 2008-11-15 20:23 BCD
-rwxrwxrwx 1 root root  21504 2008-11-15 20:17 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-10-16 03:36 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-10-16 03:36 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-10-16 03:36 bootstat.dat
drwxrwxrwx 1 root root      0 2008-10-27 18:09 cs-CZ
drwxrwxrwx 1 root root      0 2008-10-27 18:09 da-DK
drwxrwxrwx 1 root root      0 2008-10-27 18:09 de-DE
drwxrwxrwx 1 root root      0 2008-10-27 18:09 el-GR
drwxrwxrwx 1 root root      0 2008-10-27 18:09 en-US
drwxrwxrwx 1 root root      0 2008-10-27 18:09 es-ES
drwxrwxrwx 1 root root      0 2008-10-27 18:09 fi-FI
drwxrwxrwx 1 root root      0 2008-10-27 18:09 Fonts
drwxrwxrwx 1 root root      0 2008-10-27 18:09 fr-FR
drwxrwxrwx 1 root root      0 2008-10-27 18:09 hu-HU
drwxrwxrwx 1 root root      0 2008-10-27 18:09 it-IT
drwxrwxrwx 1 root root      0 2008-10-27 18:09 ja-JP
drwxrwxrwx 1 root root      0 2008-10-27 18:09 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 07:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-10-27 18:09 nb-NO
drwxrwxrwx 1 root root      0 2008-10-27 18:09 nl-NL
drwxrwxrwx 1 root root      0 2008-10-27 18:09 pl-PL
drwxrwxrwx 1 root root      0 2008-10-27 18:09 pt-BR
drwxrwxrwx 1 root root      0 2008-10-27 18:09 pt-PT
drwxrwxrwx 1 root root      0 2008-10-27 18:09 ru-RU
drwxrwxrwx 1 root root      0 2008-10-27 18:09 sv-SE
drwxrwxrwx 1 root root      0 2008-10-27 18:09 tr-TR
drwxrwxrwx 1 root root      0 2008-10-27 18:09 zh-CN
drwxrwxrwx 1 root root      0 2008-10-27 18:09 zh-HK
drwxrwxrwx 1 root root      0 2008-10-27 18:09 zh-TW

=========================== sdc2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sdc2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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
##      altoptions=(single-user) single
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

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sdc2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sdc2 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd2,1)
kernel		/boot/last-good-boot/vmlinuz root=/dev/sdc2 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd2,1)
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


=============================== sdc2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc2
UUID=c5abbc16-a5cc-4cc9-986e-1fd3027a0cfd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc4
UUID=56ea3085-3927-48cb-ab66-62e4580b8686 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc2/boot: ==================================

total 12664
drwxr-xr-x  4 root root    4096 2009-01-17 17:57 .
drwxr-xr-x 20 root root    4096 2009-01-17 17:57 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
lrwxrwxrwx  1 root root       1 2009-01-17 17:45 boot -> .
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-07 08:32 gfxmenu
drwxr-xr-x  2 root root    4096 2009-01-17 17:57 grub
-rw-r--r--  1 root root 8903882 2009-01-17 17:57 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sdc2/boot/grub: ===============================

total 244
drwxr-xr-x 2 root root   4096 2009-01-17 17:57 .
drwxr-xr-x 4 root root   4096 2009-01-17 17:57 ..
-rw-r--r-- 1 root root    197 2009-01-17 17:57 default
-rw-r--r-- 1 root root     45 2009-01-17 17:57 device.map
-rw-r--r-- 1 root root   9440 2009-01-17 17:57 e2fs_stage1_5
-rw-r--r-- 1 root root   9120 2009-01-17 17:57 fat_stage1_5
-rw-r--r-- 1 root root     19 2009-01-17 17:57 installed-version
-rw-r--r-- 1 root root   8224 2009-01-17 17:57 iso9660_stage1_5
-rw-r--r-- 1 root root  10144 2009-01-17 17:57 jfs_stage1_5
-rw-r--r-- 1 root root   4571 2009-01-17 17:57 menu.lst
-rw-r--r-- 1 root root   8480 2009-01-17 17:57 minix_stage1_5
-rw-r--r-- 1 root root  11296 2009-01-17 17:57 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-17 17:57 stage1
-rw-r--r-- 1 root root 125674 2009-01-17 17:57 stage2
-rw-r--r-- 1 root root  10856 2009-01-17 17:57 xfs_stage1_5

=============================== StdErr Messages: ===============================

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
```

im pretty sure its something simple 
thx in advance!

---

### Post by caljohnsmith on 2009-01-17
It looks like all you may need to do is change your BIOS to boot the sdc Mint drive rather than the sda drive. How about trying that and let me know how it goes.

---

### Post by Dr.Fritz on 2009-01-17
hello caljohnsmith! nice to have you help me again :P 
well it is already that way, my bios is set to boot from my hard drive where mint is installed, it wasnt that way(i had the other drive boot first and i changed it) and i was getting  the same error but the polished mint menu wouldnt even appear, now it does but it wont let me boot any OS i have

---

### Post by caljohnsmith on 2009-01-17
When you get the Grub menu on start up, how about selecting the first Mint entry, press "e" to edit it, select the line that says "root (hd2,1)", press "e" to edit it, change it to "root (hd0,1)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Mint. Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Mint, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "# groot=(hd2,1)" to use the (hd0,1) that worked to boot Mint. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by Dr.Fritz on 2009-01-17
well in mint grub menu there is a line that u can type into when any grub line is highlighted. i changed it to /dev/sda1 instead of /dev/sdc2 and left ```
ro quiet splash
``` unchanged but nothing happened.. i still got "disk not found" message.

---

### Post by caljohnsmith on 2009-01-17
OK, how about instead do this from a Live CD:
```
sudo mount /dev/sdc2 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And then change all the Mint entries to use (hd0,1) similar to:
```
title		Linux Mint 6, kernel 2.6.27-7-generic
root		[COLOR="Blue"](hd0,1)[/COLOR]
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sdc2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

```
Also change the "groot" line in the file to use (hd0,1):
```
# groot=[COLOR="Blue"](hd0,1)[/COLOR]
```
Save, reboot, and let me know how far you get.

---

### Post by Dr.Fritz on 2009-01-18
a big THANKS caljohnsmith! again you solved my Grub problem!
by the way i will reinstall winxp so i will have to restore grub, i suppose it is the usual?
```
find /boot/grub/stage1 
root (hdx,y)
setup (hdx)
```

thanks again!

---

### Post by caljohnsmith on 2009-01-18
> **Dr.Fritz said:**
> a big THANKS caljohnsmith! again you solved my Grub problem!
by the way i will reinstall winxp so i will have to restore grub, i suppose it is the usual?
```
find /boot/grub/stage1 
root (hdx,y)
setup (hdx)
```

thanks again!
Really glad to hear that worked OK, and if you are going to reinstall XP, then those commands you show should work just fine. Cheers and have fun with Mint and XP. :)

---

