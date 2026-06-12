---
title: "Flash drive boots persistence but not GRUB"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by theozzlives on 2009-01-14
Hi,

I had my flash drive booting with pendrivelinux's instructions on setting up a persistent drive, it had some restrictions though. I spent yesterday installing a full install from the alt CD-ROM (with my hard drive unplugged).

Now this morning I try to boot USB (with my CMOS set right) and it goes straight to my HD.

I know I'm missing something simple and stupid but can't figure out what. Help please!

---

### Post by caljohnsmith on 2009-01-14
So your BIOS does support booting from a USB drive? How about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by theozzlives on 2009-01-14
Here ya go:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20964824    10482381   83  Linux
/dev/sda2        20964825   251144144   115089660   83  Linux
/dev/sda3   *   251144145   304190774    26523315    7  HPFS/NTFS
/dev/sda4       304190775   312576704     4192965    5  Extended
/dev/sda5       304190838   312576704     4192933+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 3: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 8054 MB, 8054636032 bytes
255 heads, 63 sectors/track, 979 cylinders, total 15731711 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cdf1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    14956514     7478226   83  Linux
/dev/sdb2        14956515    15727634      385560    5  Extended
/dev/sdb5        14956578    15727634      385528+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="b37ac976-2337-487e-a1ed-80e7a6edf077" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="bbe88f91-aa3a-4d91-bcab-9d704608421a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="FE3884CD3884867D" TYPE="ntfs" 
/dev/sda5: UUID="93064781-041b-423c-8179-85b6c0312b20" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="73642897-89ba-402a-b690-b89404139ebe" TYPE="ext3" 
/dev/sdb5: UUID="51833f72-36ec-49dc-a53b-73a0597b3e1b" TYPE="swap" 

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
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color red/black white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=b37ac976-2337-487e-a1ed-80e7a6edf077 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b37ac976-2337-487e-a1ed-80e7a6edf077

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
# defoptions=quiet splash vga=792

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
uuid		b37ac976-2337-487e-a1ed-80e7a6edf077
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b37ac976-2337-487e-a1ed-80e7a6edf077 ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		b37ac976-2337-487e-a1ed-80e7a6edf077
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b37ac976-2337-487e-a1ed-80e7a6edf077 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b37ac976-2337-487e-a1ed-80e7a6edf077
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b37ac976-2337-487e-a1ed-80e7a6edf077 ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b37ac976-2337-487e-a1ed-80e7a6edf077
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b37ac976-2337-487e-a1ed-80e7a6edf077 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b37ac976-2337-487e-a1ed-80e7a6edf077
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b37ac976-2337-487e-a1ed-80e7a6edf077 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
/dev/sda2 /home ext3 nodev,nosuid 0 2
# Windows Partition
/dev/sda3 /windows ntfs 0 0
# /dev/sda5
UUID=93064781-041b-423c-8179-85b6c0312b20 none            swap    sw              0
# DVD Writer
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


================================== sda1/boot: ==================================

total 24388
drwxr-xr-x  3 root root    4096 2009-01-10 19:50 .
drwxr-xr-x 22 root root    4096 2009-01-13 16:42 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2009-01-11 19:34 grub
-rw-r--r--  1 root root 8496755 2008-12-22 08:33 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8497050 2008-12-24 04:53 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sda1/boot/grub: ===============================

total 236
drwxr-xr-x 3 root root   4096 2009-01-11 19:34 .
drwxr-xr-x 3 root root   4096 2009-01-10 19:50 ..
-rw-r--r-- 1 root root    197 2008-12-21 20:58 default
-rw-r--r-- 1 root root     15 2008-12-21 20:58 device.map
-rw-r--r-- 1 root root   8108 2008-12-21 20:58 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-21 20:58 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-21 20:58 installed-version
-rw-r--r-- 1 root root   8712 2008-12-21 20:58 jfs_stage1_5
-rw-r--r-- 1 root root   5122 2009-01-11 19:34 menu.lst
-rw-r--r-- 1 root root   5122 2009-01-11 19:34 menu.lst~
-rw-r--r-- 1 root root   5103 2008-12-22 08:30 menu.lst.backup
-rw-r--r-- 1 root root   7352 2008-12-21 20:58 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-21 20:58 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-12-22 08:31 splashimages
-rw-r--r-- 1 root root    512 2008-12-21 20:58 stage1
-rw-r--r-- 1 root root 121460 2008-12-21 20:58 stage2
-rw-r--r-- 1 root root   9556 2008-12-21 20:58 xfs_stage1_5

================================ sda3/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=73642897-89ba-402a-b690-b89404139ebe ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=73642897-89ba-402a-b690-b89404139ebe

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
uuid		73642897-89ba-402a-b690-b89404139ebe
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=73642897-89ba-402a-b690-b89404139ebe ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		73642897-89ba-402a-b690-b89404139ebe
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=73642897-89ba-402a-b690-b89404139ebe ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		73642897-89ba-402a-b690-b89404139ebe
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=73642897-89ba-402a-b690-b89404139ebe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=51833f72-36ec-49dc-a53b-73a0597b3e1b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 12104
drwxr-xr-x  3 root root    4096 2009-01-14 03:36 .
drwxr-xr-x 20 root root    4096 2009-01-13 19:25 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-14 03:37 grub
-rw-r--r--  1 root root 8338965 2009-01-14 03:33 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sdb1/boot/grub: ===============================

total 336
drwxr-xr-x 2 root root   4096 2009-01-14 03:37 .
drwxr-xr-x 3 root root   4096 2009-01-14 03:36 ..
-rw-r--r-- 1 root root    191 2009-01-14 03:37 default
-rw-r--r-- 1 root root     15 2009-01-14 03:36 device.map
-rw-r--r-- 1 root root   8108 2009-01-14 03:36 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-14 03:36 fat_stage1_5
-rw-r--r-- 1 root root   8712 2009-01-14 03:36 jfs_stage1_5
-rw-r--r-- 1 root root   4298 2009-01-14 03:37 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-14 03:36 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-14 03:36 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-14 03:36 stage1
-rw-r--r-- 1 root root 121460 2009-01-14 03:36 stage2
-rw-r--r-- 1 root root 121460 2009-01-14 03:36 stage2_eltorito
-rw-r--r-- 1 root root   9556 2009-01-14 03:36 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-14
It looks like you have a standard Ubuntu install on your USB drive, yet your USB drive has the "syslinux" boot loader instead of Grub in the MBR; that's probably a remnant of your previous persistent USB install. How about trying:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Reboot, make sure your BIOS is set to boot the USB drive, and let me know what happens. We can work from there if you want.

---

### Post by theozzlives on 2009-01-15
> **caljohnsmith said:**
> It looks like you have a standard Ubuntu install on your USB drive, yet your USB drive has the "syslinux" boot loader instead of Grub in the MBR; that's probably a remnant of your previous persistent USB install. How about trying:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Reboot, make sure your BIOS is set to boot the USB drive, and let me know what happens. We can work from there if you want.

Thanks (who got rid of the thank you button), but I decided to go with persistence since I can install from it. In my line of work it'll be easier to demo and install in one shot. I just can't install MP3 support for Amarock, or run Startup Manager. As far as upgrades, I'll just backup my casper-rw before re-doing it.

---

