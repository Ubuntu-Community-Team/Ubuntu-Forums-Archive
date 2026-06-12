---
title: "HELP!!! Stuck at Grub&gt;"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Doug W on 2011-01-31
HELP!!! I have an xp machine. 64bit. I installed Ubunto (partioned my drive with the live cd method) then rebooted. Discovered grub didn't load so I follwed some other advice and long story short, now when I reboot from my hard disk I get this
 
MinimaL BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.
grub>
 
And I have absolutely NO idea what to do next!!! All I wanted to do was try Ubuntu 10.10 alongside my xp. I believe I installed the 32 bit Ubuntu because I only had 2 gigs ram. I am TOTALLY lost now and can't even get windows XP to load now. I don't know what I did wrong! HELP!!!

---

### Post by drs305 on 2011-01-31
Doug W,

Welcome to Ubuntu and the Ubuntu forums.

You can either visit the following thread or go to the 'boot info script' link, run the script, and post the contents of RESULTS.txt. Either way, we should be able to help you get your system booting again.

[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

or:

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Doug W on 2011-01-31
> **drs305 said:**
> Doug W,

Welcome to Ubuntu and the Ubuntu forums.

You can either visit the following thread or go to the 'boot info script' link, run the script, and post the contents of RESULTS.txt. Either way, we should be able to help you get your system booting again.

[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

or:

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)


Thank you drs305

I think I did it right, here is the results from the boot script.
```

    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   754,008,286   754,008,224   7 HPFS/NTFS
/dev/sda2         754,010,110   976,771,071   222,760,962   5 Extended
/dev/sda5         754,010,112   967,628,799   213,618,688  83 Linux
/dev/sda6         967,630,848   976,771,071     9,140,224  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3AA46FBCA46F78F1                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e9f22594-759c-4722-95c0-a5ef3ed29853   ext4                                     
/dev/sda6        0188ef7c-d6d1-4e72-964b-0cea6cc323cc   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set e9f22594-759c-4722-95c0-a5ef3ed29853
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set e9f22594-759c-4722-95c0-a5ef3ed29853
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set e9f22594-759c-4722-95c0-a5ef3ed29853
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e9f22594-759c-4722-95c0-a5ef3ed29853 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set e9f22594-759c-4722-95c0-a5ef3ed29853
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e9f22594-759c-4722-95c0-a5ef3ed29853 ro single 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set e9f22594-759c-4722-95c0-a5ef3ed29853
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set e9f22594-759c-4722-95c0-a5ef3ed29853
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Professional x64 Edition (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 3aa46fbca46f78f1
    drivemap -s (hd0) ${root}
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=e9f22594-759c-4722-95c0-a5ef3ed29853 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=0188ef7c-d6d1-4e72-964b-0cea6cc323cc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 461.3GB: boot/grub/core.img
 437.7GB: boot/grub/grub.cfg
 437.9GB: boot/initrd.img-2.6.35-22-generic
 461.3GB: boot/vmlinuz-2.6.35-22-generic
 437.9GB: initrd.img
 461.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  d4 28 06 f7 71 31 08 49  bd 62 b2 2d d1 55 08 c8  |.(..q1.I.b.-.U..|
00000010  39 6c 20 3b 46 32 ae 49  29 ca 52 6d fa 82 0d 5b  |9l ;F2.I).Rm...[|
00000020  72 ef 9f 56 3d db aa ad  a4 b5 6d a8 30 bf 95 ad  |r..V=.....m.0...|
00000030  a3 10 c8 d3 f3 3a 54 6a  bd 40 fc 56 6a 55 8f 9c  |.....:Tj.@.VjU..|
00000040  52 75 20 d9 c3 a6 d5 50  bf 22 74 33 cc 4b cc 73  |Ru ....P."t3.K.s|
00000050  04 f1 c6 a4 28 5b e7 07  e3 92 36 df 65 21 9b 97  |....([....6.e!..|
00000060  89 5a 38 7c 29 80 b1 e6  e1 7e e2 ef c3 3f c8 43  |.Z8|)....~...?.C|
00000070  70 0a 85 7d af de c1 f7  df 52 e2 80 37 8e 04 4d  |p..}.....R..7..M|
00000080  39 18 71 3a 27 38 53 f3  98 70 5d 5f 17 f8 fc 99  |9.q:'8S..p]_....|
00000090  a8 d6 aa d2 69 35 e1 da  c7 cf d9 2c 0d 0e 7a f5  |....i5.....,..z.|
000000a0  17 1f a0 0d 3a 3c 13 c8  ba 47 ad a8 f0 f3 64 f3  |....:<...G....d.|
000000b0  37 08 65 a8 be 30 fa b3  43 e4 bb 45 55 8d a7 12  |7.e..0..C..EU...|
000000c0  d7 63 73 57 1f 49 e5 ab  71 bf c4 7f ed 30 f7 94  |.csW.I..q....0..|
000000d0  4c f2 0f f6 b8 e2 af 24  f4 eb 2f 27 39 60 5e 25  |L......$../'9`^%|
000000e0  de 88 a9 fb 95 3f 87 b6  a6 8e 4a 47 ba f3 79 10  |.....?....JG..y.|
000000f0  e5 3c 38 05 d9 1b 90 61  17 c0 73 a8 7c d9 8e ed  |.<8....a..s.|...|
00000100  b8 7a 64 1b 3a 38 c0 b1  55 66 4f 9a 73 b0 d4 40  |.zd.:8..UfO.s..@|
00000110  e4 55 16 d0 e8 36 be c6  f1 05 a9 6b b6 21 40 94  |.U...6.....k.!@.|
00000120  fb ca f9 e6 f7 80 cd bc  56 1b 7f 5e 28 ea 3e c6  |........V..^(.>.|
00000130  9c 84 54 94 92 54 70 45  78 8d 13 a6 51 12 50 17  |..T..TpEx...Q.P.|
00000140  7d 2e 1a c0 bd db 0c c3  f6 c2 ec 73 5e 78 97 3f  |}..........s^x.?|
00000150  5a 35 e2 8f 37 c0 5f 81  f6 f3 68 31 c4 6b 60 27  |Z5..7._...h1.k`'|
00000160  9b e3 2b c0 af 19 03 60  e3 cb 8f 40 64 6d 41 1c  |..+....`...@dmA.|
00000170  5a 1b 7d 18 75 f3 98 d6  31 2c 18 1f 13 2c 03 84  |Z.}.u...1,...,..|
00000180  2d 2c 83 98 45 8d b3 dc  c2 e0 19 00 7c ec a2 14  |-,..E.......|...|
00000190  1a 9f ed ff b0 94 6d a1  ae 78 05 6a 76 fe b5 96  |......m..x.jv...|
000001a0  fa dd ba 44 24 47 17 5a  78 66 d2 0a 16 5b 0c 92  |...D$G.Zxf...[..|
000001b0  44 06 dd 50 62 82 cc d1  78 06 86 bd e4 f4 00 fe  |D..Pb...x.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 bb 0c 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 90  bb 0c 00 80 8b 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by Doug W on 2011-01-31
> **drs305 said:**
> Doug W,

Welcome to Ubuntu and the Ubuntu forums.

You can either visit the following thread or go to the 'boot info script' link, run the script, and post the contents of RESULTS.txt. Either way, we should be able to help you get your system booting again.

[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

or:

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

```

    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   754,008,286   754,008,224   7 HPFS/NTFS
/dev/sda2         754,010,110   976,771,071   222,760,962   5 Extended
/dev/sda5         754,010,112   967,628,799   213,618,688  83 Linux
/dev/sda6         967,630,848   976,771,071     9,140,224  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3AA46FBCA46F78F1                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e9f22594-759c-4722-95c0-a5ef3ed29853   ext4                                     
/dev/sda6        0188ef7c-d6d1-4e72-964b-0cea6cc323cc   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set e9f22594-759c-4722-95c0-a5ef3ed29853
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set e9f22594-759c-4722-95c0-a5ef3ed29853
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set e9f22594-759c-4722-95c0-a5ef3ed29853
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e9f22594-759c-4722-95c0-a5ef3ed29853 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set e9f22594-759c-4722-95c0-a5ef3ed29853
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e9f22594-759c-4722-95c0-a5ef3ed29853 ro single 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set e9f22594-759c-4722-95c0-a5ef3ed29853
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set e9f22594-759c-4722-95c0-a5ef3ed29853
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Professional x64 Edition (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 3aa46fbca46f78f1
    drivemap -s (hd0) ${root}
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=e9f22594-759c-4722-95c0-a5ef3ed29853 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=0188ef7c-d6d1-4e72-964b-0cea6cc323cc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 461.3GB: boot/grub/core.img
 437.7GB: boot/grub/grub.cfg
 437.9GB: boot/initrd.img-2.6.35-22-generic
 461.3GB: boot/vmlinuz-2.6.35-22-generic
 437.9GB: initrd.img
 461.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  d4 28 06 f7 71 31 08 49  bd 62 b2 2d d1 55 08 c8  |.(..q1.I.b.-.U..|
00000010  39 6c 20 3b 46 32 ae 49  29 ca 52 6d fa 82 0d 5b  |9l ;F2.I).Rm...[|
00000020  72 ef 9f 56 3d db aa ad  a4 b5 6d a8 30 bf 95 ad  |r..V=.....m.0...|
00000030  a3 10 c8 d3 f3 3a 54 6a  bd 40 fc 56 6a 55 8f 9c  |.....:Tj.@.VjU..|
00000040  52 75 20 d9 c3 a6 d5 50  bf 22 74 33 cc 4b cc 73  |Ru ....P."t3.K.s|
00000050  04 f1 c6 a4 28 5b e7 07  e3 92 36 df 65 21 9b 97  |....([....6.e!..|
00000060  89 5a 38 7c 29 80 b1 e6  e1 7e e2 ef c3 3f c8 43  |.Z8|)....~...?.C|
00000070  70 0a 85 7d af de c1 f7  df 52 e2 80 37 8e 04 4d  |p..}.....R..7..M|
00000080  39 18 71 3a 27 38 53 f3  98 70 5d 5f 17 f8 fc 99  |9.q:'8S..p]_....|
00000090  a8 d6 aa d2 69 35 e1 da  c7 cf d9 2c 0d 0e 7a f5  |....i5.....,..z.|
000000a0  17 1f a0 0d 3a 3c 13 c8  ba 47 ad a8 f0 f3 64 f3  |....:<...G....d.|
000000b0  37 08 65 a8 be 30 fa b3  43 e4 bb 45 55 8d a7 12  |7.e..0..C..EU...|
000000c0  d7 63 73 57 1f 49 e5 ab  71 bf c4 7f ed 30 f7 94  |.csW.I..q....0..|
000000d0  4c f2 0f f6 b8 e2 af 24  f4 eb 2f 27 39 60 5e 25  |L......$../'9`^%|
000000e0  de 88 a9 fb 95 3f 87 b6  a6 8e 4a 47 ba f3 79 10  |.....?....JG..y.|
000000f0  e5 3c 38 05 d9 1b 90 61  17 c0 73 a8 7c d9 8e ed  |.<8....a..s.|...|
00000100  b8 7a 64 1b 3a 38 c0 b1  55 66 4f 9a 73 b0 d4 40  |.zd.:8..UfO.s..@|
00000110  e4 55 16 d0 e8 36 be c6  f1 05 a9 6b b6 21 40 94  |.U...6.....k.!@.|
00000120  fb ca f9 e6 f7 80 cd bc  56 1b 7f 5e 28 ea 3e c6  |........V..^(.>.|
00000130  9c 84 54 94 92 54 70 45  78 8d 13 a6 51 12 50 17  |..T..TpEx...Q.P.|
00000140  7d 2e 1a c0 bd db 0c c3  f6 c2 ec 73 5e 78 97 3f  |}..........s^x.?|
00000150  5a 35 e2 8f 37 c0 5f 81  f6 f3 68 31 c4 6b 60 27  |Z5..7._...h1.k`'|
00000160  9b e3 2b c0 af 19 03 60  e3 cb 8f 40 64 6d 41 1c  |..+....`...@dmA.|
00000170  5a 1b 7d 18 75 f3 98 d6  31 2c 18 1f 13 2c 03 84  |Z.}.u...1,...,..|
00000180  2d 2c 83 98 45 8d b3 dc  c2 e0 19 00 7c ec a2 14  |-,..E.......|...|
00000190  1a 9f ed ff b0 94 6d a1  ae 78 05 6a 76 fe b5 96  |......m..x.jv...|
000001a0  fa dd ba 44 24 47 17 5a  78 66 d2 0a 16 5b 0c 92  |...D$G.Zxf...[..|
000001b0  44 06 dd 50 62 82 cc d1  78 06 86 bd e4 f4 00 fe  |D..Pb...x.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 bb 0c 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 90  bb 0c 00 80 8b 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by drs305 on 2011-01-31
Ok, this should be easily fixable.

Boot the LiveCD, then open a terminal (Applications, Accessories, Terminal).

Mount the Ubuntu partition. When you run the command, it will ask for a password. Use your password. You won't see it as it's entered.

The first command will mount your real Ubuntu partition onto "/mnt". The second command will point Grub to your Ubuntu partition - do NOT include the partition number in the second command, only "sda".

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

You should also remove the "/boot" folder containing the grub files in sda1 (your Windows partition). But let's get Ubuntu booting first...

That should be all you need to get Ubuntu booting. Once you remove the LiveCD and reboot you should see the Grub2 menu. "Windows" has been found by Grub2 and will be in the menu.

Added: I see you found the code tags for the second attempt, but they appeared at the very end of the post. You would paste the contents between the [noparse]```
 and 
``` tags [/noparse].

---

### Post by Doug W on 2011-01-31
> **drs305 said:**
> Ok, this should be easily fixable.

Boot the LiveCD, then open a terminal (Applications, Accessories, Terminal).

Mount the Ubuntu partition. When you run the command, it will ask for a password. Use your password. You won't see it as it's entered.

The first command will mount your real Ubuntu partition onto "/mnt". The second command will point Grub to your Ubuntu partition - do NOT include the partition number in the second command, only "sda".

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```You should also remove the "/boot" folder containing the grub files in sda1 (your Windows partition). But let's get Ubuntu booting first...

That should be all you need to get Ubuntu booting. Once you remove the LiveCD and reboot you should see the Grub2 menu. "Windows" has been found by Grub2 and will be in the menu.

Added: I see you found the code tags for the second attempt, but they appeared at the very end of the post. You would paste the contents between the [noparse]```
 and 
``` tags [/noparse].

ok, here is what I did and what happened. I am currently writing you from the live CD I will now reboot and we'll see what happens. lol Thanks. :)

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root directory=/mnt /dev/sda
Unrecognized option `--root'
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.
ubuntu@ubuntu:~$

---

### Post by hansolo4949 on 2011-01-31
Please note, Doug, that in this, I am a bit long-winded, but please read it, since this is probably the solution you need.

First of all, we don't need to "fix" Ubuntu for doug w guys, we just need to fix windows.

 I have seen so many different threads about this, and every one just about, the person has had to reinstall Windows because they tried to "fix" Ubuntu and just messed everything up. I mean no offense to anybody, but let's just stick to the basics just in case we might mess things up:). 

Now, what you need, Doug, is a XP recovery CD. If you can make on from another XP installation, great. If not, you need to find an XP recovery cd ISO, that you can burn to CD. There are several good applications for doing that, so you should be good to go. Now, if you have Windows 7, you MIGHT be able to use one of those recovery CD's, but it might not work. 

Recovery cd lecture over, you need to boot into the cd after you make it. You will have to change the boot order of some stuff in your bios to do that, which is a lot easier than it sounds. Pay close attention to your boot screen when it first flashes up. What does it say, in something like "to access bios press ___", in the blank part. The text you want should be in one of the lower corners of your screen. you usually have to press F12, ESC, or some other common key. Then, just go to the section entitled boot, (if you don't have one titled like that, tell us what the options are), and follow the instructions. You want your cd drive to be on the top. 

Then insert the cd if you haven't already, then reboot. You should go into the cd. You need to open a CMD, or command line prompt. There should be an option for that. Once that is open, type ```
BOOTREC/ fixmbr
``` (notice the space), then ```
BOOTREC/ fixboot
``` If BOOTREC guves an error, try subsituting BOOTREC.exe, or bootrec.exe. If you don't get any errors, reboot, and you should have windows! 

Then, right-click my computer, them manage. uncollapse storage, and click disk management. You should see your C drive. You should delete the partitions that don't have any files names in their descriptions (like NTFS, FAT, etc.) Another way to make sure you aren't going to mess up anything, is to delete the partitions that have the same size as the amount you allocated to Ubuntu (if you remember it). The 3+/- partition is the Ubuntu swap file, you shoudl delete that as well. 

The, if you want to reinstall Ubuntu (it isn't always this scary!) install the 64 bit version. This time, all you need to do is install it to the "free space" or the "unallocated space", which it should do automatically. If you don't want to, just right-click on your largest partition, click "expand" and add the free space onto it! You might not be able to do that, since windows is very finicky about resizing it's own partitions while there on a drive it's using.

That's all folks!

I have subscribed, so I will be able to continue to help. I could write another book for you, if you need it ;).

---

### Post by davidmohammed on 2011-01-31
sudo grub-install --root-directory=/mnt /dev/sda

there is a dash between root and directory...

---

### Post by drs305 on 2011-01-31
hansolo4949,

I may have missed something, but I think you are making this more complicated than it needs to be. If you look at the boot info results, Grub2 is controlling the boot but is looking in the wrong place for the grub files. It's looking at the Windows partition and not the Ubuntu partition. Pointing the MBR to the correct partition should be all that is necessary to get Ubuntu to boot.

Now, Windows may have a problem since there is now a /boot folder (containing a grub core.img file) which shouldn't be there. Windows may or may not boot from the Grub menu with this additional /boot folder (I don't know because I don't use Windows much). But Ubuntu will boot, and from Ubuntu the appropriate /boot folder can then be removed.

I have to step out for a bit but there are others around who undoubtedly will assist.

---

### Post by Doug W on 2011-01-31
drs305, that didn't work. Still getting the minimal BASH thing again. grub>(and a blinking cursor next to it like I need to type something there.  Hansolo, I don't have a recovery cd. Bought the machine from somebody who built it and installed xp 64bit and told me I would never need a recovery cd. I hate it when they tell me that btw. I don't know where to get a recovery cd legally and free. Can you tell me?

---

### Post by Doug W on 2011-01-31
@David, I will reboot from live cd and try again WITH the dash. lol Thanks you guys for helping me. I hope this works. Pretty nervous right about now. lol

---

### Post by ubername on 2011-01-31
Just to make sure Doug W, did you re-run the command with the dash between 'root' and 'directory'?

i.e. ```
sudo grub-install --root-directory=/mnt /dev/sda
```

p.s. a good trick to avoid typo's when executing commands is to click three times on the line of code (this should highlight the entire line) then, in the terminal window, press the middle mouse button (or wheel). This will paste what  you have highlighted.

---

### Post by hansolo4949 on 2011-01-31
Your friend? Just kidding:D. From my quick google search, there didn't seem to be any obvious answers. You might have to either borrow one from someone, or buy it....

drs305, I know I might be making it a bit complicated, but I think it's better to go with the option that will work, but is a bit more complex, than the one that is a bit less complex, yet may completely mess everything up. Since Doug doesn't have any "critical" files on his Ubuntu partition, we can safely remove it without any data loss for him (pictures, documents, etc.). If we try to fix Ubuntu, We may completely mess up Windows and/or GRUB, and he probably does have a lot of critical files on Windows. So, I thought we may as well go with keeping data. Plus, when I was new to Ubuntu, I remember not wanting to type ANY code, because it was too "complex";). Please remember that I am not trying to insult anyone, it's just my personal opinion, from seeing all fo those threads, and personal experience:).

---

### Post by Doug W on 2011-01-31
Well, ok the story is it was my cousin and we aren't speaking anymore so I can't get a disk from him and I don't know ANYONE still using XP 64 bit. 
I retried the solution with the dash btween root and directory and this is what happened. 

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$

---

### Post by davidmohammed on 2011-01-31
... looks ok -  and what  happens on a reboot?

---

### Post by Doug W on 2011-01-31
I got a menu to select which system. I was in the middle of reading it when apparently I ran out of time and it booted Ubuntu. I am going to reboot and see if I can boot into xp now. I think I may have fixed it thanks to all of you awesome people helping this nube. lol. Thank you all so much! If it works, I promise I will post and mark solved! :)

---

### Post by Doug W on 2011-01-31
Ok, I rebooted into my XP and am writing from it now. Seems fixed. THANK you guys so much! I must say, when I have a MS issue and post in their forums, I get little or no help or they tell me I need to buy this or that. In under an hour you guys fixed it for me! I am so impressed by the Ubuntu community! You guys ROCK! I hope I can learn to navigate this OS as well as all of you! Cause I like everything I have seen so far so much! I can't thank you all enough! Saved me so much headache! Marking as SOLVED now. :)

---

### Post by ubername on 2011-01-31
Great!! Well done, enjoy Ubuntu!

---

### Post by drs305 on 2011-01-31
Doug W,

Glad it's working. While you are in Windows, since this is the easiest place to do it, remove the folders and file highlighted below. It may confuse Grub2 or Windows down the road, and that folder and it's file isn't of any use where it is in any case.

> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM **[COLOR="DarkRed"]/boot/grub/core.img[/COLOR]**

Happy Ubuntu-ing !



---

### Post by Doug W on 2011-01-31
I searched for **[COLOR=DarkRed]/boot/grub/core.img[/COLOR]**. Forgive me for my nube-ness. I can't find anything like that. Found a boot folder under C directory, but all it had was a subfolder "locale" and a bunch of image and media files. Not the one you highlighted, drs305. What am I doing wrong? lol

---

### Post by drs305 on 2011-02-01
> **Doug W said:**
> I searched for **[COLOR=DarkRed]/boot/grub/core.img[/COLOR]**. Forgive me for my nube-ness. I can't find anything like that. Found a boot folder under C directory, but all it had was a subfolder "locale" and a bunch of image and media files. Not the one you highlighted, drs305. What am I doing wrong? lol

I don't know my way around Windows any longer, but it should be located under /. *Make sure you have Windows Explorer set to view system files.* You could also do a search for "core.img". 

From Ubuntu, you can mount the Windows partition and then use Nautilus as root to delete it:
```
sudo mount -t ntfs /dev/sda1 /mnt
gksu nautilus /mnt
```

Before you delete anything, note there is a difference between /Boot and /boot. The first is a Windows folder. The boot info script didn't see it, so it shouldn't exist on your system. If it does, do *not* delete it, as that is a Windows folder. You are looking only for a lowercase "/boot" folder.

Via either method, look for /boot, then inspect the contents and ensure it has the /grub folder and within /boot/grub the core.img file. You can definitely delete **sda1's** /boot/grub/ folder and should also delete the /boot folder once you confirm there are no Windows files in it.

---

### Post by runeh76 on 2011-02-01
> **Doug W said:**
> I searched for **[COLOR=DarkRed]/boot/grub/core.img[/COLOR]**. Forgive me for my nube-ness. 

:lolflag:  U learn fast this, just stay on the forums and read these posts. 
Make backup, now when its working. Create second account (user) and then u can play around.

---

### Post by Doug W on 2011-02-01
Ok, I think I found it. I ran a search with XP for core.img and it showed up. Now drs305, you are telling me I need to delete the whole containing folder? How far back do I delete? What I mean is, the file core.img is in a folder named "grub" and it is the only folder that shows up inside the folder "boot". So do I just delete "boot" with all of it's contents? and is this because I am now using grub2 which makes grub one obsolete? I am confused. Sorry.

---

### Post by Doug W on 2011-02-01
Nevermind. got it. Thanks. :)

---

### Post by hansolo4949 on 2011-02-01
Oh, good, that solution worked for you. Now, I guess I have to eat a bit of crow:p. Well, now that you're in XP, I suggest IMMEDATELY making a recovery cd, and backing everything up, just in case something happens again, if something doesn't "work" in Ubuntu for instance, and when you try to "fix" it, XP/GRUB/both end up crashing. I was opposed to the terminal fixes, because I was afraid you would get GRUB fixed, then it wouldn't see XP, which is when most incidents occur, because, if GRUB doesn't see Windows, you pretty much have two (successful) choices in my experience: recovery CD or reinstall.

So, drs305, you were right, I just was a little hesitant because I thought something might go wrong.


Enjoy Ubuntu!

---

### Post by drs305 on 2011-02-01
hansolo4949,

Having a backup disk is excellent advice and many helpers on the forum wish all Windows users would follow it. Fortunately for us Ubuntu users can use the LiveCD to sort out many problems without making another disk.

In this case fixing Grub2 was just a quicker way of getting bootloader back. The advantage is that it allows the use of both Ubuntu and Windows. Your recommendation would have worked to restore Windows, but that isn't the main OS we are interested in around these parts if we can help it.  ;-)

Thanks for helping.

---

### Post by Doug W on 2011-02-01
Thank you both so much. I realize this is a Ubuntu forum and windows is somewhat of a dirty word here, but I have another question. (Now TELL me you didn't see that coming? lol) Hansolo4949, forgive me, but what's the best, easiest way to make a recovery disk? XP 64 bit.

---

### Post by davidmohammed on 2011-02-01
> **Doug W said:**
> Thank you both so much. I realize this is a Ubuntu forum and windows is somewhat of a dirty word here, but I have another question. (Now TELL me you didn't see that coming? lol) Hansolo4949, forgive me, but what's the best, easiest way to make a recovery disk? XP 64 bit.

[http://www.ehow.com/how_4815476_make-disk-windows-xp-backup.html]("http://www.ehow.com/how_4815476_make-disk-windows-xp-backup.html")

---

### Post by hansolo4949 on 2011-02-01
drs305, thank you for the advice. Unfortunately for me, I still have all of my critical files on Windows, and I know most others do, so I was mainly focusing on fixing Windows, to mimimise data loss:redface:. Plus, I am not extremely familiar with the Terminal yet (i'm competent/new, I only started a month and a half ago, but I am learning very fast!), so I would naturally want someone to do the "fix" that I thought would work "best". Well, enjoy Ubuntu, Doug!

---

