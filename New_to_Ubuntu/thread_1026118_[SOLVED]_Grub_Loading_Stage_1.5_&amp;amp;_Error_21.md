---
title: "[SOLVED] Grub Loading Stage 1.5 &amp;amp; Error 21"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by briankcred on 2008-12-30
Newbie help, first attempt at loading an operating system (chose Unbuntu), I need some advice about how to finish off the installation.

Started out by de-fragmenting and repairing any bad sectors on my computers hard drive.

Originally I tried to use an Unbuntu 8.10 live disc that I got from a magazine, however it wouldn't load either as a live disc or full install. It kept giving me the message;
Busybox V1.10.2 (unbuntu 1.1:10.2-1unbuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

I created further live discs for Kunbuntu8:10, Xunbuntu8:10, Xunbuntu8:1 Alternate, the alternate version couldn't find my CD driver and the Kunbuntu8:10 & Xunbuntu8:10 gave the same message as above 'Busybox etc'.

At one point I tried the third option on the live disc about 'help to boot on start up' from this point on every time I start up I get the choice of Windows XP Home edition or Unbuntu (only windows works, Unbuntu gives an error message about 'Busybox etc' as above.

After reading one of this forums thread's about 8.04 working while 8.10 did not for someone, I created an Unbuntu 8.04 LT live disc.

Installed Unbuntu 8.04 LT after giving the 'try it out without changing your settings' option a go from with in the live disc. All my hard ware seams to work, wireless network, DVD players, files etc.
The Unbuntu installer chose to load onto an USB hard drive, I assigned a third of the available space (30Gb assigned).
Once installed, I was given the option to continue using the live disc or work from the installed version.
I chose the installed version and ejected the disc.
When the computer rebooted I got the following message.

Grub loading stage 1.5
Grub loading
ERROR 21

(borrowed a lap top to access the internet)
After reading some threads on this forum I down loaded Super Grub and can now boot Windows XP from the Super Grub Live Disc, (still getting an option to load Unbuntu (that still doesn't work, with same 'Busybox etc' message as above)).
Windows only shows a reduction in size of the USB hard drive not the partition with Unbuntu on it.
Using the Unbuntu Live disc I can see my internal hard drive as well as  both partitions of my USB drive including the one with Unbuntu in it.

I've tried changing the start up settings in the computers BIO to start anything before HD0 first but I cant get my USB hard drive to activate, it always goes to the same Grub loading stage 1.5 and ERROR 21 message (as above).

Tried installing Unbuntu again but inside my computers internal hard drive, get as far as the partitioning section. Tried all options apart from taking up the whole drive, keep getting a message about 'Input/Output error during read on /dev/sda'. I always choose cancel or retry, never ignore, there is a message about not enough free space created to install Unbuntu and I cancel the installation.

I don't have a windows XP recovery disc any more after moving house (old computer, I've added more RAM, Wireless and graphics cards to it over a period of time)
I would really like to dual boot without using the Super Grub live disc all the time and I'm really interested in an alternative to Windows and have been impressed by Unbuntu so far and would like to persevere with getting it running properly, however I've a number of programs on windows XP that I'm not willing to throw out yet. 
If anyone could help with links to forum threads or could advise me directly it would be appreciated. I've stalled as to where to go from here other than to try and use Grub to make only Windows boot, along with an windows based commercial partition manager to delete the partition containing Unbuntu from my USB drive and re-size the remaining partition on it. I'd prefer the dual boot and an working Unbuntu if possible.

---

### Post by caljohnsmith on 2008-12-30
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by briankcred on 2008-12-31
Here's the results text file, hope there is something in it that will help. 


```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #5 for its boot files.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /ubuntu/disks 
                       /ubuntu/disks/boot/ /ubuntu/disks/boot/grub 
                       /ubuntu/disks/boot/grub

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9f719f71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   153227969    76613953+   c  W95 FAT32 (LBA)

sfdisk -V /dev/sda:

partition 1: end: (c,h,s) expected (1023,254,63) found (1022,254,63)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders, total 234493056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b1c6224

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   170096219    85048078+   c  W95 FAT32 (LBA)
/dev/sdb2       170096220   234484739    32194260    5  Extended
/dev/sdb5       170096283   231737624    30820671   83  Linux
/dev/sdb6       231737688   234484739     1373526   82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="ML18G4" UUID="A8E5-E897" TYPE="vfat" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="FHD-1" UUID="0DF0-164E" TYPE="vfat" 
/dev/sdb5: UUID="03272390-6f77-4b38-a91e-d0d4cd3ddda1" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="b697a3b0-e8f4-4372-be82-56ed0d736e74" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/FHD-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

c:\wubildr.mbr="Ubuntu"


============================== sda1/ubuntu/disks: ==============================

total 128
drwxr-xr-x 4 root root 32768 2008-12-29 19:38 .
drwxr-xr-x 6 root root 32768 2008-12-29 19:38 ..
drwxr-xr-x 3 root root 32768 2008-12-29 19:38 boot
drwxr-xr-x 2 root root 32768 2008-12-29 19:38 shared

=========================== sda1/ubuntu/disks/boot/: ===========================

total 96
drwxr-xr-x 3 root root 32768 2008-12-29 19:38 .
drwxr-xr-x 4 root root 32768 2008-12-29 19:38 ..
drwxr-xr-x 2 root root 32768 2008-12-29 19:38 grub

========================= sda1/ubuntu/disks/boot/grub: =========================

total 64
drwxr-xr-x 2 root root 32768 2008-12-29 19:38 .
drwxr-xr-x 3 root root 32768 2008-12-29 19:38 ..

========================= sda1/ubuntu/disks/boot/grub: =========================

total 64
drwxr-xr-x 2 root root 32768 2008-12-29 19:38 .
drwxr-xr-x 3 root root 32768 2008-12-29 19:38 ..

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=03272390-6f77-4b38-a91e-d0d4cd3ddda1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,4)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=03272390-6f77-4b38-a91e-d0d4cd3ddda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=03272390-6f77-4b38-a91e-d0d4cd3ddda1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc5
UUID=03272390-6f77-4b38-a91e-d0d4cd3ddda1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc6
UUID=b697a3b0-e8f4-4372-be82-56ed0d736e74 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================== sdb5/boot: ==================================

total 11112
drwxr-xr-x  3 root root      4096 2008-12-30 01:11 .
drwxr-xr-x 21 root root      4096 2008-12-30 01:11 ..
-rw-r--r--  1 root root    422667 2008-06-18 18:11 abi-2.6.24-19-generic
-rw-r--r--  1 root root     80049 2008-06-18 18:11 config-2.6.24-19-generic
drwxr-xr-x  2 root ubuntu    4096 2008-12-30 01:11 grub
-rw-r--r--  1 root ubuntu 7892736 2008-12-30 01:11 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root    103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r--  1 root root    905146 2008-06-18 18:11 System.map-2.6.24-19-generic
-rw-r--r--  1 root root   1920472 2008-06-18 18:11 vmlinuz-2.6.24-19-generic

=============================== sdb5/boot/grub: ===============================

total 204
drwxr-xr-x 2 root ubuntu   4096 2008-12-30 01:11 .
drwxr-xr-x 3 root root     4096 2008-12-30 01:11 ..
-rw-r--r-- 1 root ubuntu    197 2008-12-30 01:11 default
-rw-r--r-- 1 root ubuntu     45 2008-12-30 01:11 device.map
-rw-r--r-- 1 root ubuntu   8056 2008-12-30 01:11 e2fs_stage1_5
-rw-r--r-- 1 root ubuntu   7904 2008-12-30 01:11 fat_stage1_5
-rw-r--r-- 1 root ubuntu     16 2008-12-30 01:11 installed-version
-rw-r--r-- 1 root ubuntu   8608 2008-12-30 01:11 jfs_stage1_5
-rw-r--r-- 1 root root     4582 2008-12-30 01:11 menu.lst
-rw-r--r-- 1 root ubuntu   7324 2008-12-30 01:11 minix_stage1_5
-rw-r--r-- 1 root ubuntu   9632 2008-12-30 01:11 reiserfs_stage1_5
-rw-r--r-- 1 root ubuntu    512 2008-12-30 01:11 stage1
-rw-r--r-- 1 root ubuntu 108356 2008-12-30 01:11 stage2
-rw-r--r-- 1 root ubuntu   9276 2008-12-30 01:11 xfs_stage1_5

=============================== StdErr Messages: ===============================

Unknown BootLoader  on /dev/sdb1

00000000  eb 5a 90 4d 53 57 49 4e  34 2e 31 00 02 40 3a 00  |.Z.MSWIN4.1..@:.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  1d 76 23 0a 1a 51 00 00  00 00 00 00 e0 03 00 00  |.v#..Q..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 4e 16 f0 0d 4e  4f 20 4e 41 4d 45 20 20  |..)N...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 f1 7d fa 33 c9 8e  |  FAT32   .}.3..|
00000060  d1 bc f8 7b 8e c1 bd 78  00 c5 76 00 1e 56 16 55  |...{...x..v..V.U|
00000070  bf 22 05 89 7e 00 89 4e  02 b1 0b fc f3 a4 8e d9  |."..~..N........|
00000080  bd 00 7c c6 45 fe 0f 8b  46 18 88 45 f9 fb 38 66  |..|.E...F..E..8f|
00000090  40 7c 04 cd 13 72 4e bf  02 00 83 7e 16 00 75 71  |@|...rN....~..uq|
000000a0  66 83 7e 24 00 74 6a 8b  46 1c 8b 56 1e b9 03 00  |f.~$.tj.F..V....|
000000b0  49 40 75 01 42 bb 00 7e  e8 90 00 73 2a b0 f8 4f  |I@u.B..~...s*..O|
000000c0  74 21 8b 46 32 33 d2 b9  03 00 3b c8 77 43 8b 76  |t!.F23....;.wC.v|
000000d0  0e 3b ce 73 3c 2b f1 3b  c6 77 36 03 46 1c 13 56  |.;.s<+.;.w6.F..V|
000000e0  1e eb cd 73 2c eb 49 66  81 be 00 02 52 52 61 41  |...s,.If....RRaA|
000000f0  75 cc 66 81 be fc 03 00  00 55 aa 75 c1 66 81 be  |u.f......U.u.f..|
00000100  fc 05 00 00 55 aa 75 b6  83 7e 2a 00 77 03 e9 ef  |....U.u..~*.w...|
00000110  02 be 80 7d fb ac 98 03  f0 ac 84 c0 74 17 3c ff  |...}........t.<.|
00000120  74 09 b4 0e bb 07 00 cd  10 eb ee be 83 7d eb e4  |t............}..|
00000130  be 81 7d eb df 33 c0 cd  16 5e 1f 8f 04 8f 44 02  |..}..3...^....D.|
00000140  cd 19 00 00 00 00 00 00  00 00 00 50 52 51 91 92  |...........PRQ..|
00000150  33 d2 f7 76 18 91 f7 76  18 42 87 ca f7 76 1a 8a  |3..v...v.B...v..|
00000160  f2 8a 56 40 8a e8 d0 cc  d0 cc 0a cc b8 01 02 cd  |..V@............|
00000170  13 59 5a 58 72 09 40 75  01 42 03 5e 0b e2 cc c3  |.YZXr.@u.B.^....|
00000180  03 18 01 27 0d 0a 55 6e  67 75 65 6c 74 69 67 65  |...'..Ungueltige|
00000190  73 20 53 79 73 74 65 6d  20 ff 0d 0a 45 2f 41 2d  |s System ...E/A-|
000001a0  46 65 68 6c 65 72 20 20  20 20 ff 0d 0a 44 61 74  |Fehler    ...Dat|
000001b0  65 6e 74 72 61 65 67 65  72 20 77 65 63 68 73 65  |entraeger wechse|
000001c0  6c 6e 20 75 6e 64 20 54  61 73 74 65 20 64 72 75  |ln und Taste dru|
000001d0  65 63 6b 65 6e 0d 0a 00  49 4f 20 20 20 20 20 20  |ecken...IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 80 01  |SYSMSDOS   SYS..|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

No errors were reported.
```

---

### Post by billgoldberg on 2008-12-31
I don't have the time to read the whole thing.

I see you say Unbuntu.

Are you sure you are using Ubuntu (Unbuntu might be some knock off distro)?

---

I would say:

Reinstall Ubuntu.

After installation you should be able to dual boot without problems.

If for some reason it doesn't work again, I suggest you take a look at Wubi.

[http://wubi-installer.org/](http://wubi-installer.org/)

> Wubi is an officially supported Ubuntu installer for Windows users that can bring you to the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other Windows application, in a simple and safe way. Are you curious about Linux and Ubuntu? Trying them out has never been easier!

---

### Post by toni_uk on 2008-12-31
It looks like your hardware really doesn't like Ubuntu if you have tried to install so many times with so many different live images. Have you thought about using a different distro? I have recently installed Mandriva and Fedora on different machines and was happy with the result of both. Mandriva video plays up a bit under KDE 4 as Compiz is enabled but works happily with Gnome desktop. Setting up dual boot on Fedora was easy but required use of terminal (Grub & menu.lst). 
Hope you can sort out your problems

---

### Post by caljohnsmith on 2008-12-31
Can you change your BIOS to boot your 120 GB sdb drive before the 80 GB Windows drive? If so, I think the solution to your problem could be really simple. If you can set the 120 GB drive to boot first, you could install Grub to its MBR so that it's bootable, and you should be able to boot into Ubuntu without any more Grub errors if all goes well. So if that sounds OK with you, to install Grub to the MBR of your sdb drive do:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
Then do the following to correct your Grub's menu.lst:
```
sudo mount /dev/sdb5 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change all the Ubuntu entries to use (hd0,4) instead of (hd2,4) similar to:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Blue"](hd0,4)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=03272390-6f77-4b38-a91e-d0d4cd3ddda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Also change the "# groot=(hd2,4)" line to:
```
# groot=[COLOR="Blue"](hd0,4)[/COLOR]
```
Next change the Windows entry at the bottom of your menu.lst to:
```

title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Save, reboot, set your BIOS to boot the sdb drive, and if all goes well you should be able to boot Ubuntu or Windows from your Grub menu. Let me know how it goes or if you run into problems.

---

### Post by briankcred on 2009-01-03
I couldn't get the USB drive to boot before my internal hard drive (HD0), so I installed a second internal hard drive (HD1) and -installed Ubuntu onto a 100Gb worth of that (I initialized and partitioned the new (second/slave hard drive) using windows).
I've changed my bio to start the second (HD1) hard drive before the first (HD0), and I now have a different error message as follows;
Grub loading stage 1.5
Grub loading, please wait
ERROR 5.

I'm also back to using the Super Grub live disk to boot windows.

Because I've changed my set up I ran the set up report again i.e. removed the USB hard drive and installed a second (slave) internal hard drive, see below.

Hope this makes this an easier problem to solve, as I cant add anymore hard ware to my computer.


```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for its boot files.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       409544968 sectors, but according to the info from 
                       fdisk, it has 409544982 sectors.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9f719f71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   153227969    76613953+   c  W95 FAT32 (LBA)

sfdisk -V /dev/sda:

partition 1: end: (c,h,s) expected (1023,254,63) found (1022,254,63)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6da4f729

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   409545044   204772491    7  HPFS/NTFS
/dev/sdb2       409545045   625137344   107796150    5  Extended
/dev/sdb5       409545108   617554664   104004778+  83  Linux
/dev/sdb6       617554728   625137344     3791308+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________
blkid -c /dev/null

=============================== "mount" output: ===============================
mount

================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=c04c6377-3268-41d2-87de-c3646427a8bc ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c04c6377-3268-41d2-87de-c3646427a8bc ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c04c6377-3268-41d2-87de-c3646427a8bc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=c04c6377-3268-41d2-87de-c3646427a8bc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=40cd3fc7-3133-4a59-ae56-8583edb509a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================== sdb5/boot: ==================================

total 11108
drwxr-xr-x  3 root root    4096 2009-01-03 15:52 .
drwxr-xr-x 21 root root    4096 2009-01-03 15:52 ..
-rw-r--r--  1 root root  422667 2008-06-18 18:11 abi-2.6.24-19-generic
-rw-r--r--  1 root root   80049 2008-06-18 18:11 config-2.6.24-19-generic
drwxr-xr-x  2 root root    4096 2009-01-03 15:53 grub
-rw-r--r--  1 root root 7886388 2009-01-03 15:52 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r--  1 root root  905146 2008-06-18 18:11 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1920472 2008-06-18 18:11 vmlinuz-2.6.24-19-generic

=============================== sdb5/boot/grub: ===============================

total 204
drwxr-xr-x 2 root root   4096 2009-01-03 15:53 .
drwxr-xr-x 3 root root   4096 2009-01-03 15:52 ..
-rw-r--r-- 1 root root    197 2009-01-03 15:52 default
-rw-r--r-- 1 root root     30 2009-01-03 15:52 device.map
-rw-r--r-- 1 root root   8056 2009-01-03 15:52 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2009-01-03 15:52 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-03 15:53 installed-version
-rw-r--r-- 1 root root   8608 2009-01-03 15:52 jfs_stage1_5
-rw-r--r-- 1 root root   4582 2009-01-03 15:53 menu.lst
-rw-r--r-- 1 root root   7324 2009-01-03 15:52 minix_stage1_5
-rw-r--r-- 1 root root   9632 2009-01-03 15:52 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-03 15:52 stage1
-rw-r--r-- 1 root root 108356 2009-01-03 15:52 stage2
-rw-r--r-- 1 root root   9276 2009-01-03 15:52 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-03
OK, you actually have Grub installed to your Windows sda drive at present, so how about doing the following to install Grub to the Ubuntu sdb drive:
```
sudo grub
grub> root (hd1,0)
grub> makeactive
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
And please post the output of all the above commands. Next reboot, make sure your BIOS is set to boot the sdb drive, and then you should at least get the Grub menu on start up. Booting any of the Ubuntu entries in the Grub menu won't work yet, but we can fix that if you can just get the Grub menu; how about trying that and let me know how far you get.

---

### Post by briankcred on 2009-01-03
I've ran the code which is shown below and set the BIOS to start HDD1 before HDD0. 
The same Grub loading stage 1.5
ERROR 5 is coming up when I boot the computer.

```
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> grub> root (hd1,0)

Error 27: Unrecognized command

grub> root (hd1,0)

grub> makeactive

grub> root (hd1,4)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> quit

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ 
```

---

### Post by caljohnsmith on 2009-01-03
OK, from your Live CD, how about doing:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
That will restore a Windows MBR to your sda Windows drive, so when you reboot, we can make sure you are booting the sdb drive if you get the Grub error. Please let me know if you get the same Grub error upon rebooting, and we can go from there.

---

### Post by briankcred on 2009-01-03
Still getting the same ERROR 5 message.

When I put in the first line of code a separate window came up wanting LILO to be run as it looked like it had never been used before. Though it didn't say how to go about running it.

```
ubuntu@ubuntu:~$ sudo apt-get install lilo 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following extra packages will be installed: 
  mbr 
Suggested packages: 
  lilo-doc 
The following NEW packages will be installed: 
  lilo mbr 
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded. 
Need to get 387kB of archives. 
After this operation, 1253kB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Get:1 http://archive.ubuntu.com hardy/main mbr 1.1.9-3ubuntu1 [23.4kB] 
Get:2 http://archive.ubuntu.com hardy/main lilo 1:22.8-3.1ubuntu1 [364kB] 
Fetched 387kB in 1s (195kB/s) 
Preconfiguring packages ... 
Selecting previously deselected package mbr. 
(Reading database ... 98477 files and directories currently installed.) 
Unpacking mbr (from .../mbr_1.1.9-3ubuntu1_i386.deb) ... 
Selecting previously deselected package lilo. 
Unpacking lilo (from .../lilo_1%3a22.8-3.1ubuntu1_i386.deb) ... 
Setting up mbr (1.1.9-3ubuntu1) ... 
Setting up lilo (1:22.8-3.1ubuntu1) ... 

ubuntu@ubuntu:~$ sudo lilo -M  /dev/sda mbr 
Backup copy of /dev/sda in /boot/boot.0800 
The Master Boot Record of  /dev/sda  has been updated. 
ubuntu@ubuntu:~$ 
```

---

### Post by caljohnsmith on 2009-01-03
That's really strange you would get a Grub error 5, because a Grub error 5 is:
[QUOTE=Official Grub Manual]**Error 5**: Partition table invalid or corrupt
This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign.[/QUOTE]
And after carefully looking over your sdb drive's partition table, I don't see anything wrong with it (but maybe I'm missing something). Can you boot into Ubuntu using the Super Grub Disk? Also, try using the option on the Super Grub Disk to install Grub to your sdb drive's MBR and point to the Ubuntu installation for its boot files. Unfortunately I don't remember exactly how to do it with Super Grub, so I can't give you specific directions. And lastly, one more thing to try from the Super Grub Disk is to press "c" at the main menu to get the Grub CLI, and then do:
```
grub> geometry (hd0)
```
That should show three partitions since your Ubuntu drive should be first in your BIOS boot order or (hd0). If it does, try:
```
grub> rootnoverify (hd0)
grub> chainloader +1
grub> boot
```
And then see if it boots the Ubuntu drive. Let me know what happens and we can work from there.

---

### Post by briankcred on 2009-01-04
My laptop has been returned to me unexpectadly and I've loaded Ubuntu straight onto it with no drama or issues.
I've returned my desktop back to Windows as the installation shouldn't be this hard and would like to thank particularly caljohnsmith for his help.
Work is about to get busy so I will be taking a break from trying to install a duel boot system on my desk top and enjoy Ubuntu on my laptop.
I've marked this thread as solved to save anyone trying to review it as an ongoing issue.

Thanks again,
Brian

---

