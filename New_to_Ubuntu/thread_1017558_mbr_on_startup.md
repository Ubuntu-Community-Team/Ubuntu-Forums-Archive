---
title: "mbr on startup"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by jackgu1988 on 2008-12-21
hi! i used as root the commands > install-mbr /dev/sda and > install-mbr /dev/sda1 and when i turn on my pc the only thing that i can see is MBR and i can't do anything... i am using a dual boot debian-ubuntu machine... what can i do to fix that? :confused::confused::confused:

---

### Post by natirips on 2008-12-21
If there's nothing of great importance on your computer, try restoring it with supergrub disk [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) .

---

### Post by caljohnsmith on 2008-12-21
What are you trying to do? Are you trying to restore a Windows style MBR that will allow you to boot directly into Windows? I think you may be in trouble though since you tried to install to /dev/sda1, which is a partition, not your MBR; if you have Windows, sda1 is likely your Windows partition, and you won't be able to boot it now.

In order to get a clearer picture of your setup, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup.

---

### Post by jackgu1988 on 2008-12-21
on the 1st partition i have debian and on the second ubuntu... the output from the command is:

> Testdisk is installed in the MBR of /dev/sda

sda1:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Debian GNU/Linux 4.0 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2:
    File system:  Extended Partition

sda5:
    File system:  swap

sda6:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda7:
    File system:  swap


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   113434964    56717451   83  Linux
/dev/sda2       113434965   234436544    60500790    5  Extended
/dev/sda5       229135158   234436544     2650693+  82  Linux swap / Solaris
/dev/sda6       113435091   224315594    55440252   83  Linux
/dev/sda7       224315658   229135094     2409718+  82  Linux swap / Solaris

Partition table entries are not in disk order
/dev/sda1: UUID="55370255-51e4-4dc7-88cc-c4dd0a5e0a90" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="e6b2ebc0-2c33-416b-962a-60ff785dbe32" TYPE="swap" 
/dev/sda6: UUID="284f98cd-8e86-43cd-8432-b1b61d052848" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="61a9c912-ccbc-4eca-b0e0-5a9f3f91ab61" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=113434902, Id=83, bootable
/dev/sda2 : start=113434965, size=121001580, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=229135158, size=  5301387, Id=82
/dev/sda6 : start=113435091, size=110880504, Id=83
/dev/sda7 : start=224315658, size=  4819437, Id=82

sda1/boot/grub/menu.lst

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=/dev/sda1 ro

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
# defoptions=

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
# altoptions=(single-user mode) single

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

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.18-6-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.18-6-686 root=/dev/sda1 ro 
initrd		/boot/initrd.img-2.6.18-6-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-6-686 (single-user mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.18-6-686 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.18-6-686
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

sda1/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

sda1/boot

total 11696
drwxr-xr-x  3 root root    4096 2008-11-09 11:46 .
drwxr-xr-x 22 root root    4096 2008-11-13 16:19 ..
-rw-r--r--  1 root root   70682 2008-10-13 15:29 config-2.6.18-6-686
drwxr-xr-x  2 root root    4096 2008-11-09 12:51 grub
-rw-r--r--  1 root root 5369822 2008-11-09 11:46 initrd.img-2.6.18-6-686
-rw-r--r--  1 root root 4495337 2008-11-09 01:00 initrd.img-2.6.18-6-686.bak
-rw-r--r--  1 root root  723233 2008-10-13 21:34 System.map-2.6.18-6-686
-rw-r--r--  1 root root 1260081 2008-10-13 21:34 vmlinuz-2.6.18-6-686

sda1/boot/grub

total 192
drwxr-xr-x 2 root root   4096 2008-11-09 12:51 .
drwxr-xr-x 3 root root   4096 2008-11-09 11:46 ..
-rw-r--r-- 1 root root    197 2008-11-09 01:12 default
-rw-r--r-- 1 root root     15 2008-11-09 01:12 device.map
-rw-r--r-- 1 root root   7552 2008-11-09 01:12 e2fs_stage1_5
-rw-r--r-- 1 root root   7424 2008-11-09 01:12 fat_stage1_5
-rw-r--r-- 1 root root   8192 2008-11-09 01:12 jfs_stage1_5
-rw-r--r-- 1 root root   3826 2008-11-09 01:12 menu.lst
-rw-r--r-- 1 root root   6848 2008-11-09 01:12 minix_stage1_5
-rw-r--r-- 1 root root   9248 2008-11-09 01:12 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-09 01:12 stage1
-rw-r--r-- 1 root root 108328 2008-11-09 01:12 stage2
-rw-r--r-- 1 root root   8872 2008-11-09 01:12 xfs_stage1_5

sda6/boot/grub/menu.lst

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
# kopt=root=UUID=284f98cd-8e86-43cd-8432-b1b61d052848 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=284f98cd-8e86-43cd-8432-b1b61d052848

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
uuid		284f98cd-8e86-43cd-8432-b1b61d052848
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=284f98cd-8e86-43cd-8432-b1b61d052848 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		284f98cd-8e86-43cd-8432-b1b61d052848
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=284f98cd-8e86-43cd-8432-b1b61d052848 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		284f98cd-8e86-43cd-8432-b1b61d052848
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=284f98cd-8e86-43cd-8432-b1b61d052848 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		284f98cd-8e86-43cd-8432-b1b61d052848
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=284f98cd-8e86-43cd-8432-b1b61d052848 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		284f98cd-8e86-43cd-8432-b1b61d052848
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Debian GNU/Linux, kernel 2.6.18-6-686 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.18-6-686 root=/dev/sda1 ro 
initrd		/boot/initrd.img-2.6.18-6-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Debian GNU/Linux, kernel 2.6.18-6-686 (single-user mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.18-6-686 root=/dev/sda1 ro single 
initrd		/boot/initrd.img-2.6.18-6-686
savedefault
boot


sda6/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=284f98cd-8e86-43cd-8432-b1b61d052848 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=61a9c912-ccbc-4eca-b0e0-5a9f3f91ab61 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda6/boot

total 23788
drwxr-xr-x  3 root root    4096 2008-12-16 10:51 .
drwxr-xr-x 20 root root    4096 2008-11-27 18:49 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-20 03:27 grub
-rw-r--r--  1 root root 8193316 2008-11-26 11:18 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8194486 2008-12-16 10:51 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

sda6/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-20 03:27 .
drwxr-xr-x 3 root root   4096 2008-12-16 10:51 ..
-rw-r--r-- 1 root root    197 2008-12-20 03:26 default
-rw-r--r-- 1 root root     15 2008-11-13 16:33 device.map
-rw-r--r-- 1 root root   8108 2008-12-20 03:26 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-20 03:26 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-20 03:26 installed-version
-rw-r--r-- 1 root root   8712 2008-12-20 03:26 jfs_stage1_5
-rw-r--r-- 1 root root   5529 2008-12-20 03:27 menu.lst
-rw-r--r-- 1 root root   5529 2008-12-20 03:27 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-20 03:26 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-20 03:26 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-20 03:26 stage1
-rw-r--r-- 1 root root 121460 2008-12-20 03:26 stage2
-rw-r--r-- 1 root root   9556 2008-12-20 03:26 xfs_stage1_5

StdErr Messages 

Unknown BootLoader  on /dev/sda1

00000000  fc 31 c0 8e d0 31 e4 8e  d8 8e c0 be 00 7c bf 00  |.1...1.......|..|
00000010  06 b9 00 01 f3 a5 be ee  07 b0 08 ea 20 06 00 00  |............ ...|
00000020  80 3e b6 07 ff 75 04 88  16 b6 07 80 3c 00 74 04  |.>...u......<.t.|
00000030  08 06 b2 07 83 ee 10 d0  e8 73 f0 cd 1a 89 16 00  |.........s......|
00000040  08 e8 33 01 81 3e b4 07  ff ff 74 46 f6 06 b3 07  |..3..>....tF....|
00000050  80 74 06 b4 01 cd 16 75  39 f6 06 b3 07 40 74 07  |.t.....u9....@t.|
00000060  f6 06 17 04 0f 75 2b 31  c0 cd 1a 2b 16 00 08 2b  |.....u+1...+...+|
00000070  16 b4 07 72 d7 a0 b3 07  24 07 3c 07 75 0b be be  |...r....$.<.u...|
00000080  07 b0 00 b9 04 00 80 3c  00 75 66 fe c0 83 c6 10  |.......<.uf.....|
00000090  e2 f4 e8 e2 00 b4 0e be  a0 07 8a 0e b2 07 ac d0  |................|
000000a0  e9 73 02 cd 10 08 c9 75  f5 b0 3a cd 10 31 c0 cd  |.s.....u..:..1..|
000000b0  16 3c 00 74 f8 3c 0d 74  bc 3c 61 72 06 3c 7a 77  |.<.t.<.t.<ar.<zw|
000000c0  02 2c 20 88 c3 be a0 07  8a 0e b2 07 ac d0 e9 73  |., ............s|
000000d0  04 38 c3 74 06 08 c9 75  f3 eb d2 b8 0d 0e 31 db  |.8.t...u......1.|
000000e0  cd 10 8d 84 5f 00 3c 07  75 07 b0 1f a2 b2 07 eb  |...._.<.u.......|
000000f0  a1 e8 83 00 31 d2 b9 01  00 3c 04 74 11 73 f0 30  |....1....<.t.s.0|
00000100  e4 b1 04 d2 e0 be be 07  01 c6 8a 16 b6 07 bf 05  |................|
00000110  00 56 f6 c2 80 74 2b b4  41 bb aa 55 52 cd 13 5a  |.V...t+.A..UR..Z|
00000120  5e 56 72 1e 81 fb 55 aa  75 18 f6 c1 01 74 13 8b  |^Vr...U.u....t..|
00000130  44 08 8b 5c 0a be 90 07  89 44 08 89 5c 0a b4 42  |D..\.....D..\..B|
00000140  eb 0c 8a 74 01 8b 4c 02  b8 01 02 bb 00 7c 50 c6  |...t..L......|P.|
00000150  06 92 07 01 cd 13 58 5e  73 05 4f 75 b4 eb 90 81  |......X^s.Ou....|
00000160  3e fe 7d 55 aa 75 f6 31  db b8 0d 0e cd 10 b0 0a  |>.}U.u.1........|
00000170  cd 10 ea 00 7c 00 00 50  b8 0d 0e 31 db cd 10 be  |....|..P...1....|
00000180  8c 07 b9 04 00 ac cd 10  e2 fb 58 c3 4d 42 52 20  |..........X.MBR |
00000190  10 00 01 00 00 7c 00 00  00 00 00 00 00 00 00 00  |.....|..........|
000001a0  31 32 33 34 46 00 00 41  4e 44 54 6d 62 72 00 02  |1234F..ANDTmbr..|
000001b0  00 02 90 c7 12 00 80 00  00 00 00 00 a8 01 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


---

### Post by caljohnsmith on 2008-12-21
OK, but what are you trying to do? If you want to be able to boot both Debian and Ubuntu, how about restoring Grub to the MBR, have Grub point to the Ubuntu partition for its boot files, and then add an entry in your Ubuntu menu.lst to boot Debian? Does that sound like what you might want to do? Or why are you trying to use the install-mbr from the mbr package?

---

### Post by jackgu1988 on 2008-12-21
yeah that's exactly what i want to do! :)

---

### Post by caljohnsmith on 2008-12-21
OK, great, I'm glad I understand your goal now. :) How about doing:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
And then you should get the Ubuntu Grub menu on start up and be able to boot into Ubuntu. If that works OK, then once you are in Ubuntu, do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom add:
```
title Debian Grub Menu
root (hd0,0)
configfile /boot/grub/menu.lst
```
Reboot, select "Debian Grub Menu" from Ubuntu's Grub menu, and see if you can boot into Debian. Let me know how it goes or if you run into problems.

---

### Post by jackgu1988 on 2008-12-21
cool! it worked just perfect! the only thing i changed is that because i was using a live cd to do everything instead of ```
gksudo gedit /boot/grub/menu.lst
``` i mounted the volume where i had ubuntu and did ```
gksudo gedit /media/disk/boot/grub/menu.lst
``` as root. THANK YOU!!!!!!!:):):)

---

### Post by caljohnsmith on 2008-12-21
Glad to hear that worked; cheers and have fun with Debian and Ubuntu. :)

---

