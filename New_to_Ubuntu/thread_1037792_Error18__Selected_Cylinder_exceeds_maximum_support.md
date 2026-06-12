---
title: "Error18 : Selected Cylinder exceeds maximum supported by BIOS"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by MrQuangnd on 2009-01-12
I installed Ubuntu 8.10 on desktop PC 2 days ago and I've just updated it. While update, it missed some packages and I canceled. Then system updated and required restart. 
Oh my god! :confused: Then restarted my PC show error message: **Error18: Selected Cylinder exceeds maximum supported by BIOS**

I tried to boot from menu but all of them not successful:
Here is menu:

U 8.10, kernel 2.6.27-9-generic
....(recovery mode)
U 8.10, kernel 2.6.27-7-generic
....(recovery mode)

I searched to resolve this problem but it may be complexed so I need some helps step by step to restore original state (or anything can fix this problem).

Thanks for support...

---

### Post by louieb on 2009-01-12
Is this an older PC?   How much Ram? How big a hard drive? 
The usual fix for this is to create a separate partition near the front of the disk and use it to mount  /boot.  

Try to boot to the older 2.6.27-7-generic kernel and see if that works.  

You may have to re partition the hard drive. If the older kernel works - i think it should. Then post the partition table  by  running
```
sudo fdisk -l 
```(lowercase L at the end)

---

### Post by egalvan on 2009-01-12
Did the system ever start correctly during or after the install?

Or did this error start showing after the updates?

---

### Post by MrQuangnd on 2009-01-12
> **egalvan said:**
> Did the system ever start correctly during or after the install?

Or did this error start showing after the updates?

error occured then I updated. Before updated, system still run normally!

kernel 2.6.27-7-generic didn't work! (it has mess: Error 16 : Incosistent filesystem structure)

I tried use command-line as : **grub> *sudo fdisk -l* **
but it's unrecognized command

So, what must i do?

---

### Post by caljohnsmith on 2009-01-12
If you are also getting a Grub error 16, you might have more serious problems then just having your kernels and boot files out-of-reach of your BIOS, which is what a Grub error 18 usually means. Do you have a Live CD you can use for troubleshooting? If so, how about booting that, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by MrQuangnd on 2009-01-13
Here is Result.txt : 

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 20.8 GB, 20847697920 bytes
255 heads, 63 sectors/track, 2534 cylinders, total 40718160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa818a818

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    38925494    19462716   83  Linux
/dev/sda2        38925495    40708709      891607+   5  Extended
/dev/sda5        38925558    40708709      891576   82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 513 MB, 513614336 bytes
16 heads, 63 sectors/track, 995 cylinders, total 1003153 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     1003152      501545    e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(994, 15, 63) logical=(995, 3, 4)

sfdisk -V /dev/sdb:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="b75e71d0-516e-40c9-a939-fb4a5f6ee718" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="12775bc6-7965-4408-bc8f-ae7dcc1be425" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="BEST GUY" UUID="2D97-00A9" TYPE="vfat" 

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
/dev/sdb1 on /media/BEST GUY type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

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
# kopt=root=UUID=b75e71d0-516e-40c9-a939-fb4a5f6ee718 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b75e71d0-516e-40c9-a939-fb4a5f6ee718

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
uuid		b75e71d0-516e-40c9-a939-fb4a5f6ee718
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b75e71d0-516e-40c9-a939-fb4a5f6ee718 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		b75e71d0-516e-40c9-a939-fb4a5f6ee718
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b75e71d0-516e-40c9-a939-fb4a5f6ee718 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b75e71d0-516e-40c9-a939-fb4a5f6ee718
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b75e71d0-516e-40c9-a939-fb4a5f6ee718 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b75e71d0-516e-40c9-a939-fb4a5f6ee718
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b75e71d0-516e-40c9-a939-fb4a5f6ee718 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b75e71d0-516e-40c9-a939-fb4a5f6ee718
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b75e71d0-516e-40c9-a939-fb4a5f6ee718 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=12775bc6-7965-4408-bc8f-ae7dcc1be425 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 23780
drwxr-xr-x  3 root root    4096 2009-01-12 10:32 .
drwxr-xr-x 20 root root    4096 2009-01-12 10:29 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-12 10:29 grub
-rw-r--r--  1 root root 8189390 2009-01-12 10:28 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8189415 2009-01-12 10:32 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-12 10:29 .
drwxr-xr-x 3 root root   4096 2009-01-12 10:32 ..
-rw-r--r-- 1 root root    197 2002-01-01 00:42 default
-rw-r--r-- 1 root root     15 2002-01-01 00:42 device.map
-rw-r--r-- 1 root root   8108 2002-01-01 00:42 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2002-01-01 00:42 fat_stage1_5
-rw-r--r-- 1 root root     16 2002-01-01 00:42 installed-version
-rw-r--r-- 1 root root   8712 2002-01-01 00:42 jfs_stage1_5
-rw-r--r-- 1 root root   4792 2009-01-12 10:29 menu.lst
-rw-r--r-- 1 root root   4708 2009-01-12 10:29 menu.lst~
-rw-r--r-- 1 root root   7352 2002-01-01 00:42 minix_stage1_5
-rw-r--r-- 1 root root   9756 2002-01-01 00:42 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2002-01-01 00:42 stage1
-rw-r--r-- 1 root root 121460 2002-01-01 00:42 stage2
-rw-r--r-- 1 root root   9556 2002-01-01 00:42 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sdb1

00000000  eb 3c 90 44 4f 4b 30 31  2e 30 32 00 02 10 01 00  |.<.DOK01.02.....|
00000010  02 00 02 00 00 f8 f5 00  3f 00 10 00 3f 00 00 00  |........?...?...|
00000020  52 4e 0f 00 80 01 29 a9  00 97 2d 00 00 00 00 00  |RN....)...-.....|
00000030  00 00 00 00 00 00 46 41  54 31 36 20 20 20 33 c9  |......FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


=============================== StdErr Messages: ===============================

No errors were reported.

```

Hoping replied soon...

---

### Post by MrQuangnd on 2009-01-14
somebody help me :(

---

### Post by caljohnsmith on 2009-01-14
OK, how about posting the output of:
```
sudo grub
grub> root (hd0,0)
grub> blocklist /boot/grub/stage2
grub> blocklist /boot/grub/menu.lst
grub> quit
```
And we can work from there.

---

