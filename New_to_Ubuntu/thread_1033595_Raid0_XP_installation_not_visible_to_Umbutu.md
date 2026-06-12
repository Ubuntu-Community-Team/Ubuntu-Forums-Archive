---
title: "Raid0 XP installation not visible to Umbutu"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by ronparent on 2009-01-07
Because of prior Linux installations destroying my XP installation (admittedly through my own ignorance), I no longer trust installing Linux to the same drive as XP. I have, currently, a working XP install on a raid0 pair, and, a working Ubuntu 8.10 install on a separate 80Gb ide drive. XP of course doesn't see the linux drive, but, neither does Ubuntu see the XP drives.

So my two part question is: 1) what do I have to do to see and mount the Raid0 drives (I currently see two unformatted drives when booted in 8.10)? 2) How do I get grub to present me with the XP raid0 as a boot alternative?

Incidentally, I currently "dual boot" the system using the BIOS to access the desired boot drive.

---

### Post by RobsterUK on 2009-01-08
I'm not sure what the solution would be here, but an important question is, is it a hardware or software RAID?

---

### Post by caljohnsmith on 2009-01-08
As far as booting XP from your Ubuntu install, I think I can help with that, but in order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Windows from Grub.

Also, if you are using software RAID, you will probably want to look at installing the "mdadm" package in Ubuntu. I don't know the details of how to configure it, but that should allow you to access your XP RAID partition in Ubuntu.

---

### Post by ronparent on 2009-01-08
a

---

### Post by caljohnsmith on 2009-01-08
So are you using hardware RAID? The script you ran didn't find the sdc drive, so I'm just wondering how you have your RAID set up. But about booting Windows from Grub, how about opening your Grub's menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom add:
```
title       Windows XP (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows XP (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Most likely the first entry above should work to boot Windows from Grub, and the second entry is just in case Grub sees your RAID drives as separate on start up. If neither entry works, let me know exactly what happens when you try each of them from the Grub menu. We can work from there.

---

### Post by ronparent on 2009-01-08
My apologies caljohnsmith, I failed to enter root PW and only my prior results were posted to my desktop! Disregard prior post. Results.txt show a different lineup as follows: 

Results.txt

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy

sda3: _________________________________________________________________________

    File system:       Extended Partition

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdc2: _________________________________________________________________________

    File system:       swap

sdc3: _________________________________________________________________________

    File system:       Extended Partition

sdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf150f150

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    48227129    24113533+   7  HPFS/NTFS
/dev/sda3        66589425   643338989   288374782+   f  W95 Ext'd (LBA)
/dev/sda5   ?  3771970889  2708522321  1615759364+  51  OnTrack DM6 Aux1

sfdisk -V /dev/sda:


sfdisk: ERROR: sector 66589425 does not have an msdos signature
Warning: partition 3 extends past end of disk

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00027c0a


sfdisk -V /dev/sdb:


sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type

sfdisk: no partition table present.

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders, total 156355584 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x19741973

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    58589054    29294496   83  Linux
/dev/sdc2        58589055    58605119        8032+  82  Linux swap / Solaris
/dev/sdc3        58605120   156344579    48869730    f  W95 Ext'd (LBA)
/dev/sdc5        58605183   156344579    48869698+   b  W95 FAT32

sfdisk -V /dev/sdc:

/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sdc1: UUID="52657931-0801-4d2d-8c52-bfdf64259dad" TYPE="ext3" 
/dev/sdc2: UUID="b2ad95ee-fad5-4cd5-9d69-60328c998d43" TYPE="swap" 
/dev/sdc5: LABEL="PICTURES" UUID="4813-3271" TYPE="vfat" 
/dev/mapper/nvidia_aebhdfib1: UUID="00000000BEC3E4C9" LABEL="WIN XP HOME1" TYPE="ntfs" 
/dev/mapper/nvidia_aebhdfib5: UUID="47AACD69F0A43684" LABEL="SWAP" TYPE="ntfs" 
/dev/mapper/nvidia_aebhdfib6: UUID="A1404E37E38CC769" LABEL="PROGRAMS1" TYPE="ntfs" 
/dev/mapper/nvidia_aebhdfib7: UUID="00DE0830B0FA4610" LABEL="FILES1" TYPE="ntfs" 
/dev/mapper/nvidia_aebhdfib8: LABEL="GAMES" UUID="52A0-3C7F" TYPE="vfat" 
/dev/mapper/nvidia_aebhdfib9: UUID="584D74A1A6A051C4" LABEL="INTERNET" TYPE="ntfs" 
/dev/mapper/nvidia_aebhdfib10: LABEL="DATA 1" UUID="DA13-87F3" TYPE="vfat" 
/dev/mapper/nvidia_aebhdfib11: LABEL="DATA2" UUID="1DCD-2DB8" TYPE="vfat" 
/dev/mapper/nvidia_aebhdfib12: LABEL="BACKUP" UUID="6186-D381" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ron/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ron)

=========================== sdc1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=52657931-0801-4d2d-8c52-bfdf64259dad ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=52657931-0801-4d2d-8c52-bfdf64259dad

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
uuid		52657931-0801-4d2d-8c52-bfdf64259dad
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=52657931-0801-4d2d-8c52-bfdf64259dad ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		52657931-0801-4d2d-8c52-bfdf64259dad
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=52657931-0801-4d2d-8c52-bfdf64259dad ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		52657931-0801-4d2d-8c52-bfdf64259dad
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=52657931-0801-4d2d-8c52-bfdf64259dad ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		52657931-0801-4d2d-8c52-bfdf64259dad
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=52657931-0801-4d2d-8c52-bfdf64259dad ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		52657931-0801-4d2d-8c52-bfdf64259dad
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=52657931-0801-4d2d-8c52-bfdf64259dad /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc2
UUID=b2ad95ee-fad5-4cd5-9d69-60328c998d43 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdc1/boot: ==================================

total 23948
drwxr-xr-x  3 root root    4096 2009-01-06 15:45 .
drwxr-xr-x 20 root root    4096 2009-01-07 19:04 ..
-rw-r--r--  1 root root  507665 2008-11-04 16:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 18:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 16:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 18:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-03 19:48 grub
-rw-r--r--  1 root root 8196228 2009-01-03 19:47 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8353834 2009-01-06 15:45 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 16:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 18:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 16:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 18:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 16:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 18:46 vmlinuz-2.6.27-9-generic

=============================== sdc1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2009-01-03 19:48 .
drwxr-xr-x 3 root root   4096 2009-01-06 15:45 ..
-rw-r--r-- 1 root root    197 2009-01-03 19:31 default
-rw-r--r-- 1 root root     45 2009-01-03 19:31 device.map
-rw-r--r-- 1 root root   8108 2009-01-03 19:31 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-03 19:31 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-03 19:31 installed-version
-rw-r--r-- 1 root root   8712 2009-01-03 19:31 jfs_stage1_5
-rw-r--r-- 1 root root   4792 2009-01-03 19:48 menu.lst
-rw-r--r-- 1 root root   4708 2009-01-03 19:48 menu.lst~
-rw-r--r-- 1 root root   7352 2009-01-03 19:31 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-03 19:31 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-03 19:31 stage1
-rw-r--r-- 1 root root 121460 2009-01-03 19:31 stage2
-rw-r--r-- 1 root root   9556 2009-01-03 19:31 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown MBR on /dev/sdb

00000000  18 7b 18 7b 02 00 1a 7b  1a 7b 02 00 1d 7b 1d 7b  |.{.{...{.{...{.{|
00000010  02 00 22 7b 23 7b 02 00  2d 7b 2d 7b 02 00 2f 7b  |.."{#{..-{-{../{|
00000020  30 7b 02 00 32 7b 32 7b  02 00 34 7b 35 7b 01 00  |0{..2{2{..4{5{..|
00000030  3a 7b 3a 7b 02 00 3b 7b  3b 7b 01 00 3c 7b 3c 7b  |:{:{..;{;{..<{<{|
00000040  01 00 3e 7b 3e 7b 02 00  40 7b 40 7b 02 00 44 7b  |..>{>{..@{@{..D{|
00000050  44 7b 02 00 46 7b 46 7b  02 00 48 7b 48 7b 02 00  |D{..F{F{..H{H{..|
00000060  4a 7b 4a 7b 02 00 4d 7b  4e 7b 01 00 5a 7b 5b 7b  |J{J{..M{N{..Z{[{|
00000070  01 00 5d 7b 5d 7b 02 00  61 7b 61 7b 01 00 62 7b  |..]{]{..a{a{..b{|
00000080  62 7b 02 00 63 7b 67 7b  02 00 69 7b 69 7b 02 00  |b{..c{g{..i{i{..|
00000090  6d 7b 6d 7b 02 00 70 7b  70 7b 02 00 73 7b 74 7b  |m{m{..p{p{..s{t{|
000000a0  02 00 76 7b 76 7b 02 00  78 7b 78 7b 01 00 79 7b  |..v{v{..x{x{..y{|
000000b0  79 7b 01 00 7b 7b 7b 7b  01 00 7e 7b 7e 7b 01 00  |y{..{{{{..~{~{..|
000000c0  80 7b 80 7b 02 00 82 7b  82 7b 02 00 84 7b 84 7b  |.{.{...{.{...{.{|
000000d0  02 00 87 7b 88 7b 02 00  8a 7b 8c 7b 02 00 8e 7b  |...{.{...{.{...{|
000000e0  8f 7b 02 00 91 7b 91 7b  02 00 96 7b 96 7b 02 00  |.{...{.{...{.{..|
000000f0  98 7b 99 7b 02 00 9b 7b  9b 7b 02 00 a0 7b a0 7b  |.{.{...{.{...{.{|
00000100  01 00 a2 7b a2 7b 02 00  a4 7b a4 7b 01 00 a6 7b  |...{.{...{.{...{|
00000110  ab 7b 02 00 af 7b af 7b  02 00 b5 7b b5 7b 02 00  |.{...{.{...{.{..|
00000120  b7 7b b7 7b 02 00 b9 7b  b9 7b 02 00 be 7b be 7b  |.{.{...{.{...{.{|
00000130  02 00 c0 7b c0 7b 02 00  c4 7b c4 7b 02 00 c9 7b  |...{.{...{.{...{|
00000140  cb 7b 02 00 ce 7b ce 7b  01 00 d1 7b d1 7b 01 00  |.{...{.{...{.{..|
00000150  d3 7b d3 7b 02 00 d4 7b  d5 7b 02 00 d8 7b d8 7b  |.{.{...{.{...{.{|
00000160  02 00 db 7b dc 7b 02 00  de 7b e0 7b 02 00 e2 7b  |...{.{...{.{...{|
00000170  e4 7b 02 00 e7 7b e9 7b  02 00 eb 7b eb 7b 01 00  |.{...{.{...{.{..|
00000180  ee 7b ee 7b 02 00 f0 7b  f0 7b 02 00 f2 7b f4 7b  |.{.{...{.{...{.{|
00000190  02 00 f8 7b f9 7b 02 00  fb 7b fb 7b 01 00 fc 7b  |...{.{...{.{...{|
000001a0  fc 7b 02 00 fd 7b fd 7b  02 00 ff 7b 03 7c 02 00  |.{...{.{...{.|..|
000001b0  05 7c 06 7c 02 00 09 7c  0a 7c 02 00 0d 7c 0e 7c  |.|.|...|.|...|.||
000001c0  02 00 10 7c 11 7c 01 00  16 7c 16 7c 02 00 19 7c  |...|.|...|.|...||
000001d0  19 7c 02 00 1c 7c 1e 7c  02 00 20 7c 23 7c 02 00  |.|...|.|.. |#|..|
000001e0  25 7c 25 7c 02 00 28 7c  29 7c 02 00 2b 7c 2d 7c  |%|%|..(|)|..+|-||
000001f0  02 00 30 7c 30 7c 02 00  33 7c 33 7c 02 00 37 7c  |..0|0|..3|3|..7||
00000200


=============================== StdErr Messages: ===============================


sfdisk: ERROR: sector 66589425 does not have an msdos signature

sfdisk: ERROR: sector 66589425 does not have an msdos signature
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x70ba of partition table 5 will be corrected by w(rite)
Disk /dev/sdb doesn't contain a valid partition table


My comments: Boy am I embarassed:redface:. Win XP, now seems, is installed on /dev/sda & /dev/sdb used as a raid0 containig approx. 10 partions, of which the first partition is the XP installation. Much appreciate any help you can give me.

---

### Post by ronparent on 2009-01-08
The grub menu add-on directing to hd1 works!!! That problem solved. Many, many thanks.

Unfortunately still cannot see XP drives in Ubuntu. Will try your other suggestion immediately.

---

### Post by ronparent on 2009-01-08
The grub menu add-on directing to hd1 works!!! That problem solved. Many, many thanks.

Unfortunately still cannot see XP drives in Ubuntu. Will try your other suggestion immediately.:popcorn:

---

### Post by ronparent on 2009-01-09
This is difficult, because, the more I dig, the more I find only the foggiest information to lead me where I need to go. With that b___h out of the way, this is where I am trying to go - I would like to be able to mount drives containing my raid0 xp install to see and work on data stored on them.

This is where I am currently at - inadvertently using dmraid -ay, I have activated the raid0 striped array and can see them all and presumeably modify them with any of the disk partioning utilities. Although I have gotten close to being able to replicate all of my Win based activities in Ubuntu, I DO NOT WANT TO ALTER OR MODIFY MY WINDOWS INSTALL IN ANY WAY!!! I have lost too many previous Window installations trying to put various Linux installs in the same box. With that said, the file browser still doesn't see any of the raid0 drives. Now that these drives are active, could reinstalling the file browser make them visible? If so, how?

---

### Post by caljohnsmith on 2009-01-09
I don't have much experience with RAID setups, but have your tried installing and using the "mdadm" package? That might help. Also, do you have any devices listed in the /dev/mapper directory? I think that is where the RAID drives get mapped to, but I'm going from memory so I could be wrong. Let me know how that goes.

---

### Post by ronparent on 2009-01-09
The answer is yes in all three cases. I'm not sure, but, I suspect that the dmraid package mapped the drive and made them active. And the two sata drive are seen in dmraid as a good raid0 array. They also now show up in the gnome partition editor as one drive with all the partions properly identified! But they still don't appear in the Nautilus file browser and thus can't be mounted in the gnome environment. That environment was apparently set on installation and I don't know the fix to get the array seen. I've tried reinstalling Nautilus to no avail.

The problem I have with both dmraid and mdadm is that they seem to be useful tools to format and create raid arrays, but if you don't use the formating capabilities to create the array (thus erasing existing partitions), setting the drives active seems insufficient to get the system to recognize them. I am too much afraid of destroying the working XP install to experiment without better understanding of the command syntax of either or the intended uses.

Your info on grub was extremely helpful. Thank you very much.

---

### Post by ronparent on 2009-01-09
This didn't post 2hrs ago, so here it is again?

The answer is yes in all three cases. I'm not sure, but, I suspect that 
the dmraid package mapped the drive and made them active. And the two sata drive are seen in dmraid as a good raid0 array. They also now show up in the gnome partion editor as one drive with all the partions properly identified! But they still don't appear in the Nautilus file browser and thus can't be mounted in the gnome environment. That environment was apparently set on installation and I don't know the fix to get the array seen. I've tried reinstalling Nautilus to no avail.

The problem I have with both dmraid and mdadm is that they seem to be useful tools to format and create raid arrays, but if you don't use the formating capabilities to create the array (thus erasing existing partions), setting the drives active seems insufficient to get the system to recognize them. I am too much afraid of destroying the working XP install to experiment without better understanding of the command syntax of either or the intended uses.

Your info on grub was extremely helpful. Thank you very much.

---

### Post by ronparent on 2009-01-10
to caljohnsmith.  I don't know why, but, thia repsonse was not posted yestarday when written. 

The answer is yes in all three cases. I'm not sure, but, I suspect that the dmraid package mapped the drive and made them active. And the two sata drive are seen in dmraid as a good raid0 array. They also now show up in the gnome partion editor as one drive with all the partions properly identified! But they still don't appear in the Nautilus file browser and thus can't be mounted in the gnome environment. That environment was apparently set on installation and I don't know the fix to get the array seen. I've tried reinstalling Nautilus to no avail.

The problem I have with both dmraid and mdadm is that they seem to be useful tools to format and create raid arrays, but if you don't use the formating capabilities to create the array (thus erasing existing partions), setting the drives active seems insufficient to get the system to recognize them. I am too much afraid of destroying the working XP install to experiment without better understanding of the command syntax of either or the intended uses.

Your info on grub was extremely helpful. Thank you very much.


I've since dug a bit and get the sense I will have to hand code the mdadm.conf file for mdadm to function properly. If the file is recognized on boot, it may not be neccsary to actually run mdadm for the installed file systems to be recognized??? I is still unclear to me which mdadm commands and options can be run without wiping the XP install on the array, so I will have to proceed carefully.

---

