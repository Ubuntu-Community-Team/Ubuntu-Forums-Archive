---
title: "gave up waiting for root device ubuntu 10.10"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by lun7200 on 2010-11-30
hello,

just installed ubuntu 10.10 on my external usb hdd from my 8gb flash drive

doing this on a laptop, my primary hdd (internal) is running windows (230gb of 250gb used) so i got an external hdd (2tb) and I decided to install ubuntu on it

on that same 2tb external:
1.80GB NTFS partition for various files
17gb extended with
      15gb ex2 partition in which i installed ubuntu 10.10
      2gb linux swap space

after installing from usb flash drive, everything was successful and i received the message that the system was going to rebot. after reboot i selected from my initial boot, to boot to my external hdd (my flash drive was disconnected by this point) and my system gets to the grub screen and I select to run ubuntu and after a few minutes i get an error message:

```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/a0c70102-b5d8-4b82-a14c-225330e1c4d4 does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _ 
``` 

i ran a quick search for similar problems but nothing seemed to help me

i type exit at the time of error (as a previous thread suggested) but that did not seem to help. I read that editing the grub/menu.lst can solve the problem but 10.10 does not have a menu.lst (so i have read) 

i am running 10.10 currently from my flash drive (as a live user) and at the same time my external hdd is also plugged in and i can access most of the files. my external is called media/f326d7c8-357c-4517-87c5-233ab8556f75 according to linux

is there any fix for this? any help is appreciated, i apologise for my bad english. thank you

extra info

```
**sudo gedit /etc/default/grub **

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

```
 **sudo fdisk -l**

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
126 heads, 3 sectors/track, 1292056 cylinders
Units = cylinders of 378 * 512 = 193536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd03d783

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1     1237366   233862112+   7  HPFS/NTFS

Disk /dev/sdc: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders
Units = cylinders of 3040 * 512 = 1556480 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5140     7812592    b  W95 FAT32

Disk /dev/sdd: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bef84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      240892  1934963966    7  HPFS/NTFS
/dev/sdd2          240893      243201    18547012    5  Extended
/dev/sdd5          240893      242932    16386268+  83  Linux
/dev/sdd6          242933      243201     2160711   82  Linux swap / Solaris

```

---

### Post by lun7200 on 2010-11-30
*bump*

---

### Post by Elfy on 2010-11-30
Please follow the instructions here - including the code tags bit - an paste the output here.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Edit - also please do not bump your threads so quickly - that also includes not posting duplicates.

---

### Post by lun7200 on 2010-11-30
hello,

thanks for your reply, i didnt mean to bump too early I posted it early in the morning and thought people skipped it since many new threads were posted ahead of mine. anyways, i downloaded the file and moved it to my desktop (since firefox saves it to downloads by default). I am running 10.10 on my flash drive. i type the following commands and i get unwanted results

```
ubuntu@ubuntu:~$ sudo bash ~/desktop/boot_info_script*.sh
bash: /home/ubuntu/desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/desktop/boot_info_script055.sh
bash: /home/ubuntu/desktop/boot_info_script055.sh: No such file or directory
```

am i doing something wrong? sorry if i sound like a total newb

---

### Post by banjo man on 2010-12-01
I haven't run this script (running Windows ATM) but you could try:

download the file to your desktop, then in a terminal go to that directory (if user isn't ubuntu change that)
```
cd /home/ubuntu/Desktop
```

do a "dir" and see if the file is there (just to be sure).

then, try: (this will make the file executable if it needs to be)
```
chmod a+x boot_info_script055.sh
```

then try:
```
./boot_info_script055.sh
```
or
```
sh boot_info_script055.sh
```

This may all be wrong, but it is how I run certain scripts when I need. (don't know what the script does, maybe it needs to be run like it says /shrug)

---

### Post by lun7200 on 2010-12-01
@ forestpiskie: here are the contents of the .txt file

@ banjo man: thanks alot man, worked like a charm

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
126 heads, 3 sectors/track, 1292056 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   467,724,287   467,724,225   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8000 MB, 8000110592 bytes
160 heads, 19 sectors/track, 5139 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32    15,625,215    15,625,184   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048 3,869,929,979 3,869,927,932   7 HPFS/NTFS
/dev/sdd2       3,869,930,041 3,907,024,064    37,094,024   5 Extended
/dev/sdd5       3,869,930,043 3,902,702,579    32,772,537  83 Linux
/dev/sdd6       3,902,702,643 3,907,024,064     4,321,422  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        286CC2A6397A0F2A                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        57A2-88C0                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        5AEA7306EA72DE27                       ntfs       Elements                      
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        f326d7c8-357c-4517-87c5-233ab8556f75   ext2                                     
/dev/sdd6        98cf9e2d-3cdb-45e4-8dca-df27b31fadd0   swap                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd5        /media/f326d7c8-357c-4517-87c5-233ab8556f75 ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /media/Elements          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdd5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set f326d7c8-357c-4517-87c5-233ab8556f75
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set f326d7c8-357c-4517-87c5-233ab8556f75
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu 10.10' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set f326d7c8-357c-4517-87c5-233ab8556f75
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sdd5 ro   quiet splash rootdelay=90
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu 10.10 (Recovery Mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set f326d7c8-357c-4517-87c5-233ab8556f75
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sdd5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set f326d7c8-357c-4517-87c5-233ab8556f75
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set f326d7c8-357c-4517-87c5-233ab8556f75
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista " {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 286cc2a6397a0f2a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdd5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd5 during installation
UUID=f326d7c8-357c-4517-87c5-233ab8556f75 /               ext2    errors=remount-ro 0       1
# swap was on /dev/sdd6 during installation
UUID=98cf9e2d-3cdb-45e4-8dca-df27b31fadd0 none            swap    sw              0       0

=================== sdd5: Location of files loaded by Grub: ===================


1993.1GB: boot/grub/core.img
1993.1GB: boot/grub/grub.cfg
1992.9GB: boot/initrd.img-2.6.35-22-generic
1993.0GB: boot/vmlinuz-2.6.35-22-generic
1992.9GB: initrd.img
1993.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 16 00  |.X.SYSLINUX.. ..|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 6b ee 00 e5 0e 00 00  00 00 00 00 02 00 00 00  |.k..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 c0 88 a2 57 4e  4f 20 4e 41 4d 45 20 20  |..)...WNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 40 48 27 00  66 ba 00 00 00 00 bb 00  |}.f.@H'.f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by Elfy on 2010-12-02
Have a look and see if this helps 

[http://ubuntuforums.org/showpost.php?p=10058668&postcount=2](http://ubuntuforums.org/showpost.php?p=10058668&postcount=2)

Change your linux /vmlinuz root=/ line to 

linux /vmlinuz root=/dev/sdd5

---

### Post by namdude0373 on 2012-02-25
I have my ubuntu on my D: Partition on my laptop (which is 33GB, but in the setup i made it to 30GB for ubuntu) and when i try```
cd /home/ubuntu/Desktop
``` it doesnt work. Also this post: [http://ubuntuforums.org/showpost.php?p=10058668&postcount=2](http://ubuntuforums.org/showpost.php?p=10058668&postcount=2)

I have no idea what he is saying, do i do this on Windows command prompt?

---

