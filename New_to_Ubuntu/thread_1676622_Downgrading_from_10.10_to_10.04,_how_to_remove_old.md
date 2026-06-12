---
title: "Downgrading from 10.10 to 10.04, how to remove old o/s..??"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by JDM_SOHC on 2011-01-27
I still have the 10.10 but I want to get rid of it, 1. because I'm not using it anymore, and 2. because it clutters up my grub menu... I've searched around and found the Synaptic way of searching for "linux-image-2" but the 10.10 version isn't listed there for some reason... Anyway care to shine some light on this, thanks in advance...

---

### Post by Kirboosy on 2011-01-27
Did you fresh install 10.10 or upgrade to it?

---

### Post by Nickjpost on 2011-01-27
You could use Simple Backup to backup all the stuff you want to save; I'm certain the only way you can downgrade is to do a clean install of the version you wish to run. See this post:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1607499](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1607499)

---

### Post by Kirboosy on 2011-01-27
Yeah there is no way you can roll back, but I was just wondering if you had installed it on a different partition. If you did you will be able to delete the 10.10 data off the partition.

But make sure you run in a terminal ```
sudo update-grub
``` otherwise your GRUB will fry...If you want that partition back you will have to reinstall everything.

---

### Post by QLee on 2011-01-27
[QUOTE=JDM_SOHC]I still have the 10.10 but I want to get rid of it, 1. because I'm not using it anymore, and 2. because it clutters up my grub menu... I've searched around and found the Synaptic way of searching for "linux-image-2" but the 10.10 version isn't listed there for some reason... Anyway care to shine some light on this, thanks in advance...[/QUOTE]

If 10.10 was the last operating system you installed there is a chance that GRUB in the MBR looks for the rest of the needed files on the partition where 10.10 is installed (if it was installed that way). If that is the situation and you follow the advice to delete the files from that partition then your system will not have a GRUB menu to find and it will not be able to boot any operating system.

To be sure we actually know the way your system is organised so we can give the best advice, please run this program following the directions and post the results.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by JDM_SOHC on 2011-01-27
Sry guys, should have elaborated a little bit more...

I started off with 9.10 a while back, an just yesterday had the urge to update to 10.10 since I know a few updates have been released since 9.10 came out... 

Well 10.10 was a nightmare, codecs missing, screen not working, etc etc so after doing all the backdoor hacks to get 10.10 running right it still didn't feel smooth to me @ all so I downloaded 10.04 LTS from [www.ubuntu.com](www.ubuntu.com) and installed it last night using the LiveCD method... 

Well now I have 10.04 running awesome, and just wanna get rid of 10.10 since I'm not gonna use it anymore and I can't figure out how... Make sense..??

---

### Post by JDM_SOHC on 2011-01-27
> **QLee said:**
> If 10.10 was the last operating system you installed there is a chance that GRUB in the MBR looks for the rest of the needed files on the partition where 10.10 is installed (if it was installed that way). If that is the situation and you follow the advice to delete the files from that partition then your system will not have a GRUB menu to find and it will not be able to boot any operating system.

To be sure we actually know the way your system is organised so we can give the best advice, please run this program following the directions and post the results.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Here it is, it's very long..

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   227,322,998   227,322,936   7 HPFS/NTFS
/dev/sda2         227,323,902   612,012,239   384,688,338   f W95 Ext d (LBA)
/dev/sda5         371,441,664   612,012,239   240,570,576   7 HPFS/NTFS
/dev/sda6         275,159,040   367,409,151    92,250,112  83 Linux
/dev/sda7         367,411,200   371,439,615     4,028,416  82 Linux swap / Solaris
/dev/sda8         227,323,904   273,084,415    45,760,512  83 Linux
/dev/sda9         273,086,464   275,144,703     2,058,240  82 Linux swap / Solaris
/dev/sda3         612,012,240   625,136,399    13,124,160   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        54846B84846B6786                       ntfs       HP                            
/dev/sda2: PTTYPE="dos" 
/dev/sda3        2C88743C8874071C                       ntfs       Recovery                      
/dev/sda5        769894B598947579                       ntfs       Windows 7                     
/dev/sda6        600cfac2-94e7-4f24-a845-ca914a213f60   ext4                                     
/dev/sda7        263193a3-4d09-41e6-93e6-c56f5d4493e3   swap                                     
/dev/sda8        01b08c69-0189-4152-ad83-926b08699503   ext4                                     
/dev/sda9        2372688a-4f51-4da7-b9ee-9992d694c33f   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Ubuntu 10.04.1 LTS i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 600cfac2-94e7-4f24-a845-ca914a213f60
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 600cfac2-94e7-4f24-a845-ca914a213f60
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 600cfac2-94e7-4f24-a845-ca914a213f60
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=600cfac2-94e7-4f24-a845-ca914a213f60 ro   quiet splash nomodeset
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 600cfac2-94e7-4f24-a845-ca914a213f60
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=600cfac2-94e7-4f24-a845-ca914a213f60 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 600cfac2-94e7-4f24-a845-ca914a213f60
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 600cfac2-94e7-4f24-a845-ca914a213f60
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 54846b84846b6786
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=600cfac2-94e7-4f24-a845-ca914a213f60 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=263193a3-4d09-41e6-93e6-c56f5d4493e3 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 149.6GB: boot/grub/core.img
 149.6GB: boot/grub/grub.cfg
 142.0GB: boot/initrd.img-2.6.35-24-generic
 149.7GB: boot/vmlinuz-2.6.35-24-generic
 142.0GB: initrd.img
 149.7GB: vmlinuz

=========================== sda8/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 01b08c69-0189-4152-ad83-926b08699503
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 01b08c69-0189-4152-ad83-926b08699503
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 01b08c69-0189-4152-ad83-926b08699503
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=01b08c69-0189-4152-ad83-926b08699503 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 01b08c69-0189-4152-ad83-926b08699503
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=01b08c69-0189-4152-ad83-926b08699503 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 01b08c69-0189-4152-ad83-926b08699503
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 01b08c69-0189-4152-ad83-926b08699503
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 54846b84846b6786
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 600cfac2-94e7-4f24-a845-ca914a213f60
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=600cfac2-94e7-4f24-a845-ca914a213f60 ro quiet splash nomodeset
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 600cfac2-94e7-4f24-a845-ca914a213f60
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=600cfac2-94e7-4f24-a845-ca914a213f60 ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=01b08c69-0189-4152-ad83-926b08699503 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=2372688a-4f51-4da7-b9ee-9992d694c33f none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 122.9GB: boot/grub/core.img
 127.5GB: boot/grub/grub.cfg
 123.3GB: boot/initrd.img-2.6.32-28-generic
 123.2GB: boot/vmlinuz-2.6.32-28-generic
 123.3GB: initrd.img
 123.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  f9 c4 dd ef 73 86 3c c1  d7 1d 76 61 45 79 75 e7  |....s.<...vaEyu.|
00000010  d4 0f 8b db 1e 54 f3 04  4d 37 a3 44 16 d2 cc 70  |.....T..M7.D...p|
00000020  39 4b ba be 04 e6 b8 31  41 70 a8 80 14 e3 e7 3d  |9K.....1Ap.....=|
00000030  3a e7 39 c2 b4 8e 38 42  93 9c 19 1d 03 88 15 af  |:.9...8B........|
00000040  7d a9 0d 44 e0 37 31 f1  08 99 8a 0b 6b f8 46 a9  |}..D.71.....k.F.|
00000050  84 92 38 62 53 c6 72 3d  c0 2a ca 0d f5 77 44 89  |..8bS.r=.*...wD.|
00000060  5b c9 1c 0c 25 8f a5 f8  07 0f d3 52 a7 7d ca ae  |[...%......R.}..|
00000070  d8 92 c7 82 9c 24 81 a1  2b 7e 98 3d b5 f4 c7 cc  |.....$..+~.=....|
00000080  89 79 8e f4 38 05 30 1a  20 22 15 53 1f 97 09 22  |.y..8.0. ".S..."|
00000090  58 07 50 3e 24 2b aa bf  07 67 07 e1 00 1a 8f f3  |X.P>$+...g......|
000000a0  df ff 75 ba 43 ff 88 b6  81 8a eb 58 5e 49 05 9e  |..u.C......X^I..|
000000b0  bd 7d 9f b0 c8 0a 62 36  d9 99 46 41 98 41 2f c1  |.}....b6..FA.A/.|
000000c0  9a b2 fb bf 16 2a 96 93  09 3f f4 e9 11 4b a4 bb  |.....*...?...K..|
000000d0  ed ac cb 32 b8 0a 44 87  0b 99 29 ba d1 c2 e6 f7  |...2..D...).....|
000000e0  a7 b8 e9 03 30 c8 05 38  a2 56 d8 af e5 cb 5f c3  |....0..8.V...._.|
000000f0  f4 10 b8 e8 af d3 c3 f1  fd b9 d1 f9 7c 41 f7 d0  |............|A..|
00000100  3e 41 ea 74 7f ec f4 eb  32 6e 3c 29 86 3f 17 ce  |>A.t....2n<).?..|
00000110  89 00 a9 83 f3 e2 54 e2  b6 32 c7 fa f6 89 49 bc  |......T..2....I.|
00000120  ac b5 e5 df 9b 98 d9 d9  86 95 ed a6 80 26 02 79  |.............&.y|
00000130  ab 59 e7 d0 73 a1 53 49  bd a5 1b 46 8a 24 f9 63  |.Y..s.SI...F.$.c|
00000140  0c 30 86 2f a6 fa fc a8  a9 2f e1 be 51 ad e1 ca  |.0./...../..Q...|
00000150  b8 9c 0d a0 ce a8 f5 a0  b6 3f ea 37 a6 f5 ea 0e  |.........?.7....|
00000160  f4 1f 0a 00 bf 87 f8 44  af 32 4d d7 29 ef 4d a4  |.......D.2M.).M.|
00000170  9c 25 29 4b 4d f1 70 c4  94 e4 68 9c e1 3b 75 5d  |.%)KM.p...h..;u]|
00000180  79 b2 f6 bb 0b cf 5c 70  74 cc 33 30 6b 71 8a b4  |y.....\pt.30kq..|
00000190  b1 ea cb ac 8a 75 a5 07  40 51 96 45 fb e8 22 34  |.....u..@Q.E.."4|
000001a0  f7 3f a7 c1 48 d6 ad bb  c6 15 35 86 29 e1 a1 4e  |.?..H.....5.)..N|
000001b0  53 ce 51 b7 bc 2e 6f c7  c3 30 43 9d da 51 00 ef  |S.Q...o..0C..Q..|
000001c0  ff ff 07 ef ff ff 02 10  97 08 d0 d0 56 0e 00 fe  |............V...|
000001d0  ff ff 05 fe ff ff 29 b2  d9 02 d9 d5 7f 05 00 00  |......).........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 
```

---

### Post by oldfred on 2011-01-27
If you have backed up any data you want out of sda6, you should be able to delete sda6 & sda7(swap) as you have a new swap for the install in sda8.Grub is booting from sda8 so a sudo update-grub after deletion of the partitions should remove the entries.

You can use gparted to delete the partitions, you will have to use swap off on the swap partition(s) as the liveCD will probably mount them. I would just create a new data partition or save the space for your next install to test.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by JDM_SOHC on 2011-01-27
Thanks bro I'll check that out... I just heard a few bad things about Gparted so I was kinda nervous...

---

### Post by Sef on 2011-01-28
> Thanks bro I'll check that out... I just heard a few bad things about Gparted so I was kinda nervous...

GParted is very good. It is the partitioner that Ubuntu uses.

---

### Post by Jonny87 on 2011-01-28
> **Sef said:**
> GParted is very good. It is the partitioner that Ubuntu uses.

I second that. Gparted is by far my number 1 pic for partitioning.

---

### Post by darthspringbok on 2011-01-28
> **JDM_SOHC said:**
> Thanks bro I'll check that out... I just heard a few bad things about Gparted so I was kinda nervous...
 
It's not always the software that's the problem. More often than not it is the interface between the chair and the keyboard that we have to worry about.

---

### Post by JDM_SOHC on 2011-01-28
Haha thanks for input guys, I'm gonna use GParted right now and see how it goes.. Also, in Gparted, how do I know which one is 10.10, it seems like a buncha letters & numbers that define what's what..

---

### Post by oldfred on 2011-01-28
You kinda have to know what you installed where. I always have to run boot info script before and after installs to make sure I installed to where I thought I did.

Your boot script says windows boot loader in sda1, windows in sda5, (do not ever delete bootloader partition as windows cannot directly boot from logical partition), 10.10 in sda6, and 10.04.1 LTS in sda8.

---

### Post by bhaverkamp on 2011-01-28
Assuming you have installed 10.10 to it's own partition's you can just delete these partitions. Synaptic will not remove operating systems it manipulates the packages installed into the current OS instance. Getting rid of the GRUB instances is a bigger deal; I have still not made friend with GRUB2, but i am sure there is a wiki on this somewhere...

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by JDM_SOHC on 2011-02-01
> **bhaverkamp said:**
> Assuming you have installed 10.10 to it's own partition's you can just delete these partitions. Synaptic will not remove operating systems it manipulates the packages installed into the current OS instance. Getting rid of the GRUB instances is a bigger deal; I have still not made friend with GRUB2, but i am sure there is a wiki on this somewhere...

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


Thanks for input guys.. I still am a bit confused but we'll see how it goes, I just wanna delete 10.10 and give 10.04 the space that was being used by 10.10 but like I said I'm not really using any space yet cuz I'm still learning Ubuntu... So once I start utilizing 10.04 for it's true colors I'll than definitely wanna get rid of 10.10 since I don't plan on upgrading my video card for an OS that's almost the same as I have now...

---

### Post by kroq-gar78 on 2011-02-01
you could back up all of your work/documents onto an external disk (e.g. flash drive, other computer) and then reformat the whole disk (erase EVERYTHING), but that would also erase 10.04. If you haven't done much in 10.04 (no special tweaks that you don't remember how to do anymore), then maybe you should go that way and erase the whole disk.

---

### Post by JDM_SOHC on 2011-02-08
> **kroq-gar78 said:**
> you could back up all of your work/documents onto an external disk (e.g. flash drive, other computer) and then reformat the whole disk (erase EVERYTHING), but that would also erase 10.04. If you haven't done much in 10.04 (no special tweaks that you don't remember how to do anymore), then maybe you should go that way and erase the whole disk.

i still have win7, vista, & osX on this drive as well so I don't wanna erase everything just to remove one partition of ubuntu.. thanks for idea, but just can't do that (wayyyy to much backing up required)..

---

