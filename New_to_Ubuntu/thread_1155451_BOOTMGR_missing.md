---
title: "BOOTMGR missing?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by cynserino on 2009-05-10
Hey guys.
I'm seeing only a few of these BOOTMGR missing problems, so I thought I'd start off right. I already ran the bootinfo script and pasted my results here. If there's anything else needed, just ask. The problem is simple, the error comes up when I try to boot into XP. Now to get the computer to boot into XP the first time, I had to change my device.map in the grub directory. Could this of caused it?

Results.txt:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2efdca1d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02b3ffe0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   581,874,299   581,874,237   7 HPFS/NTFS
/dev/sdb2         581,874,300   586,067,264     4,192,965  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc97ac97a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    37,383,254    37,383,192  83 Linux
/dev/sdc2          37,383,255    39,102,209     1,718,955   5 Extended
/dev/sdc5          37,383,318    39,102,209     1,718,892  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="323E14E95BC87802" LABEL="Storage" TYPE="ntfs" 
/dev/sdb1: UUID="60F4C9CFF4C9A81C" TYPE="ntfs" 
/dev/sdb2: LABEL="swap" UUID="3c13be07-48df-4f40-b33f-28c55b8a425e" TYPE="swap" 
/dev/sdc1: UUID="2e5a31df-5cdf-46e6-81c5-e611f2c4738b" TYPE="ext3" 
/dev/sdc5: UUID="02b39792-773a-4062-94e8-ed6b88402add" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/daniel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=daniel)
/dev/sda1 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

splashimage=(hd2,0)/boot/grub/splash12.xpm

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=2e5a31df-5cdf-46e6-81c5-e611f2c4738b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2e5a31df-5cdf-46e6-81c5-e611f2c4738b

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2e5a31df-5cdf-46e6-81c5-e611f2c4738b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2e5a31df-5cdf-46e6-81c5-e611f2c4738b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2e5a31df-5cdf-46e6-81c5-e611f2c4738b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2e5a31df-5cdf-46e6-81c5-e611f2c4738b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        2e5a31df-5cdf-46e6-81c5-e611f2c4738b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=2e5a31df-5cdf-46e6-81c5-e611f2c4738b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=02b39792-773a-4062-94e8-ed6b88402add none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  11.7GB: boot/grub/menu.lst
  11.7GB: boot/grub/stage2
  11.7GB: boot/initrd.img-2.6.28-11-generic
  11.7GB: boot/vmlinuz-2.6.28-11-generic
  11.7GB: initrd.img
  11.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  93 1d 24 5d 91 df 7d ce  0a 5c 7b 66 5d b5 cb 48  |..$]..}..\{f]..H|
00000010  dc 8d 07 b5 83 ee b6 8a  66 6d 55 46 5e 5b bc 56  |........fmUF^[.V|
00000020  5c a7 a1 ba c2 11 7b 3a  6d b4 c0 aa d6 79 65 34  |\.....{:m....ye4|
00000030  86 04 e6 2a 05 98 e2 6f  f4 09 fd de 80 e0 13 1e  |...*...o........|
00000040  e1 0e 2c e8 6a 7b 93 e7  6d 85 5f 2c 5b c3 50 06  |..,.j{..m._,[.P.|
00000050  96 03 29 2d e2 c5 67 da  44 b6 67 a8 2b 88 01 7c  |..)-..g.D.g.+..||
00000060  17 46 4a f8 63 73 22 ac  2b 05 ae 8f 56 07 c4 9a  |.FJ.cs".+...V...|
00000070  54 41 57 09 ae a9 a5 90  c5 03 cf c6 ae 3a 52 3d  |TAW..........:R=|
00000080  d9 2e 68 93 b7 f0 c9 73  05 19 2f cf ca ab cd 5c  |..h....s../....\|
00000090  da 1d 29 4d 80 d6 d1 4f  53 27 06 84 24 3a 91 be  |..)M...OS'..$:..|
000000a0  79 d3 9e 83 1d df a7 28  24 9c 9b 18 49 0c 3f 57  |y......($...I.?W|
000000b0  61 f5 e8 3c 2f 7d b2 57  07 2f 70 f7 f0 73 ce ef  |a..</}.W./p..s..|
000000c0  97 20 4b 77 3b 4b ce 31  93 2c 1a 9c 04 c5 54 87  |. Kw;K.1.,....T.|
000000d0  39 8c 34 8d 7c 63 55 04  53 39 37 22 15 e1 6e ac  |9.4.|cU.S97"..n.|
000000e0  fa 8f ab b2 fb 78 db 9c  44 0a 2a 94 6c 84 d6 f2  |.....x..D.*.l...|
000000f0  28 bd 38 8a 34 f0 46 2f  cf b1 94 6b a4 79 fc 3f  |(.8.4.F/...k.y.?|
00000100  16 d7 c9 03 6b ac c3 bb  ce 3a 0c a9 8d 70 8c b0  |....k....:...p..|
00000110  6a 51 ac af 6b ae c7 dd  25 d3 47 45 cc 9f 63 a5  |jQ..k...%.GE..c.|
00000120  57 82 36 98 9d f2 8c 6a  0c 48 be 4d 47 6e f9 7d  |W.6....j.H.MGn.}|
00000130  ef 8d 43 2e 13 84 93 97  4d 18 5c db fa 8e 1b df  |..C.....M.\.....|
00000140  23 cd 2f ca 02 98 8e 57  a9 82 1a 78 31 88 68 f6  |#./....W...x1.h.|
00000150  6f 8c 36 db c2 6c 58 d4  4d c2 2f da d2 87 e4 fe  |o.6..lX.M./.....|
00000160  c8 3e c6 f4 94 a6 ab d4  bf 2c 2e 44 c7 c6 09 f5  |.>.......,.D....|
00000170  5f 27 7d 84 78 7d cb 8f  30 1d e6 b4 d4 ec 1e 82  |_'}.x}..0.......|
00000180  00 05 5d 30 34 43 38 63  a9 93 da 77 e3 3b f7 9e  |..]04C8c...w.;..|
00000190  ec b9 8c 58 df 49 ca 4a  a2 48 0a 45 f1 8f 7d ba  |...X.I.J.H.E..}.|
000001a0  6c 1e 37 45 c1 dc 06 25  de c3 c8 7f bb 7a a6 71  |l.7E...%.....z.q|
000001b0  84 43 4d 3e 3c 11 a1 69  7c 66 42 02 4b 39 02 ef  |.CM><..i|fB.K9..|
000001c0  8a 03 5e 61 78 b1 7c 31  4f 19 7a d3 d9 91 2d 99  |..^ax.|1O.z...-.|
000001d0  eb 4c 6f c2 d0 52 60 ab  19 8a 91 73 4c 4d a7 6f  |.Lo..R`....sLM.o|
000001e0  77 04 22 7e 5e ba df 55  1b 5e a9 73 8f 86 2e 3d  |w."~^..U.^.s...=|
000001f0  07 af 61 91 59 47 30 a0  3d b0 3f 07 ee a3 f1 93  |..a.YG0.=.?.....|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```Here's my device.map:
```

(hd0)    /dev/sdb
(hd1)    /dev/sda
(hd2)    /dev/sdc
```

---

### Post by glennric on 2009-05-10
You have not been particularly clear about what your problem is.  Is the problem that Windows XP is not booting, and it gives some error about "BOOTMGR missing"?  You said you changed the device map to get Windows XP to boot.  Did you try changing it back?

---

