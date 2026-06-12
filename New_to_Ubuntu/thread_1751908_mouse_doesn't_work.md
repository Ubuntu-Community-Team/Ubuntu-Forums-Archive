---
title: "mouse doesn't work"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by goodbyemrevans on 2011-05-07
I'm running Maverick Meerkat 10.10 netbook remix on an asus 1015PE eeepc.

This problem started yesterday.  When I start the computer, during the period where there's just the black screen with the blinking cursor in the top-left, strange text begins to fill the 
screen: > ^[[2~^[[2~^[[2~^[[2~^[[2~^[[2~^[[2~^[[2~^[[2~^[[2~etc.  sometimes it shifts for a moment to a new black screen  where this text appears in the center.  After this, ubuntu loads, but the mouse trackpad doesn't respond.  I login and shutdown using ```
sudo shutdown -h now
```After a few tries it will boot with a functional trackpad, but it's basically a crapshoot.

I'm an ubuntu newbie so please assume no prior knowledge.

Thanks for your help.

---

### Post by goodbyemrevans on 2011-05-08
maybe I misnamed this thread, and it should be "weird startup issue".  I went and bought a mouse, which seems to work even though the touchpad doesn't.  that's not such an issue; i'm more concerned about this loading text, and worried maybe other things will start to malfunction later.

---

### Post by Not unique on 2011-05-08
I had some mouse issues when I updated to Ubu 11.04 but they where video card related I think.
This sounds like it could be a driver issue have you tried to install drivers for the offending pad??

---

### Post by goodbyemrevans on 2011-05-14
as time passes, it becomes increasingly less likely that ubuntu will start when I turn on the computer.

occasionally, after the "[[2~^[[2~^" text I described before, I see the ubuntu black loading screen alternating quickly between a page of blocks of identical text:

> * set sensors limits                        21131572/77374720 
fsck from util-linux-ng 2.17.2/dev/sda1: clean, 33091/19349504 files, (check in 5 mounts)
*starting apparmor profiles                                
                                                                                 skipping profile in 
                                                                                 /etc/apparmor.d/disable:
                                                                                 usr.bin.firefox
                                   it will continue flashing this text until I shut down using the power button.

just today, I received a screenful of this message:

> fsck from util-linux-ng 2.17.2
/dev/sda1 has been mounted 36 times   without being checked, check forcedwhat do these messages mean?  does it still sound like a driver issue?  if so, how do i reinstall them?  I've already had ubuntu installed for around six months and the re haven't really been any problems - can a driver issue pop up like that, out of the blue?

---

### Post by goodbyemrevans on 2011-05-14
here are the results of the bootinfoscript:

              ```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   618,999,807   618,997,760  83 Linux
/dev/sda2         619,001,854   625,141,759     6,139,906   5 Extended
/dev/sda5         619,001,856   625,141,759     6,139,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 3984 MB, 3984588800 bytes
128 heads, 10 sectors/track, 6080 cylinders, total 7782400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,782,399     7,782,337   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        56e38eba-61cc-4e26-9433-a3ad582683ba   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        70af3c48-4f1c-4fe9-9c9f-013f526769a3   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D48E-124D                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=56e38eba-61cc-4e26-9433-a3ad582683ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=56e38eba-61cc-4e26-9433-a3ad582683ba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=56e38eba-61cc-4e26-9433-a3ad582683ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=56e38eba-61cc-4e26-9433-a3ad582683ba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=56e38eba-61cc-4e26-9433-a3ad582683ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=56e38eba-61cc-4e26-9433-a3ad582683ba ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=70af3c48-4f1c-4fe9-9c9f-013f526769a3 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 259.9GB: boot/grub/core.img
  69.9GB: boot/grub/grub.cfg
  30.8GB: boot/initrd.img-2.6.35-22-generic
  30.8GB: boot/initrd.img-2.6.35-23-generic
  69.9GB: boot/initrd.img-2.6.35-24-generic
 260.1GB: boot/vmlinuz-2.6.35-22-generic
 260.1GB: boot/vmlinuz-2.6.35-23-generic
 260.1GB: boot/vmlinuz-2.6.35-24-generic
  69.9GB: initrd.img
  30.8GB: initrd.img.old
 260.1GB: vmlinuz
 260.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 24 00  |.X.SYSLINUX...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 bf 76 00 a2 1d 00 00  00 00 00 00 02 00 00 00  |..v.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 4d 12 8e d4 4e  4f 20 4e 41 4d 45 20 20  |..)M...NO NAME  |
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
00000100  7d 00 66 b8 e0 74 0f 00  66 ba 00 00 00 00 bb 00  |}.f..t..f.......|
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

```perhaps it will mean something to someone...

---

### Post by wildmanne39 on 2011-05-14
> **goodbyemrevans said:**
> as time passes, it becomes increasingly less likely that ubuntu will start when I turn on the computer.

occasionally, after the "[[2~^[[2~^" text I described before, I see the ubuntu black loading screen alternating quickly between a page of blocks of identical text:

                                  it will continue flashing this text until I shut down using the power button.

just today, I received a screenful of this message:

what do these messages mean?  does it still sound like a driver issue?  if so, how do i reinstall them?  I've already had ubuntu installed for around six months and the re haven't really been any problems - can a driver issue pop up like that, out of the blue?

That message just means that it has booted more then 30 times and ubuntu runs a disk check automatically at boot after 30 boot ups, it is nothing to worry about. I wander if you have a key sticking on your keyboard that is causing those symbols during boot.:)

---

### Post by wildmanne39 on 2011-05-15
> **goodbyemrevans said:**
> here are the results of the bootinfoscript:

              ```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   618,999,807   618,997,760  83 Linux
/dev/sda2         619,001,854   625,141,759     6,139,906   5 Extended
/dev/sda5         619,001,856   625,141,759     6,139,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 3984 MB, 3984588800 bytes
128 heads, 10 sectors/track, 6080 cylinders, total 7782400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,782,399     7,782,337   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        56e38eba-61cc-4e26-9433-a3ad582683ba   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        70af3c48-4f1c-4fe9-9c9f-013f526769a3   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D48E-124D                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=56e38eba-61cc-4e26-9433-a3ad582683ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=56e38eba-61cc-4e26-9433-a3ad582683ba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=56e38eba-61cc-4e26-9433-a3ad582683ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=56e38eba-61cc-4e26-9433-a3ad582683ba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=56e38eba-61cc-4e26-9433-a3ad582683ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=56e38eba-61cc-4e26-9433-a3ad582683ba ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 56e38eba-61cc-4e26-9433-a3ad582683ba
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=70af3c48-4f1c-4fe9-9c9f-013f526769a3 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 259.9GB: boot/grub/core.img
  69.9GB: boot/grub/grub.cfg
  30.8GB: boot/initrd.img-2.6.35-22-generic
  30.8GB: boot/initrd.img-2.6.35-23-generic
  69.9GB: boot/initrd.img-2.6.35-24-generic
 260.1GB: boot/vmlinuz-2.6.35-22-generic
 260.1GB: boot/vmlinuz-2.6.35-23-generic
 260.1GB: boot/vmlinuz-2.6.35-24-generic
  69.9GB: initrd.img
  30.8GB: initrd.img.old
 260.1GB: vmlinuz
 260.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 24 00  |.X.SYSLINUX...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 bf 76 00 a2 1d 00 00  00 00 00 00 02 00 00 00  |..v.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 4d 12 8e d4 4e  4f 20 4e 41 4d 45 20 20  |..)M...NO NAME  |
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
00000100  7d 00 66 b8 e0 74 0f 00  66 ba 00 00 00 00 bb 00  |}.f..t..f.......|
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

```perhaps it will mean something to someone...

Hi, if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.:D

---

### Post by goodbyemrevans on 2011-05-17
well, I can't say I'm sure it's fixed.  I still get that text on startup, the meaningless repeating text.  when that text appears, the touchpad doesn't work.  if it's a stuck key wouldn't it also manifest at other times, like in firefox or a word processor?  it never does.

interestingly enough, yesterday it hung during startup in the manner i previously described.  i restarted using ```
Alt + PrtSc + R S E I U B
```  and it restarted with no problems.  no symbols during boot, no trackpad problems.  however, after i shut it down and restarted it again, we're back to symbols and no trackpad.  

any ideas?

---

### Post by goodbyemrevans on 2011-05-26
i've been tinkering around a bit.  the '~^[[2' symbol seems to come from the numpad 0 in certain command prompt environments.  sometimes it pops up in the gnome terminal but usually just at startup or in the virtual terminal.  on my keyboard numpad 0 is produced by```
 fn + M
``` so i spent awhile with a pipet puffing away under those two keys.  i think it made the problem worse.  now the right fn key seems to be completely locked, or something is causing the numpad to lock.  this renders my keyboard unusable since the nupad includes J, K L U I O p and M, as well as messing with some of my punctuation in that area of the keyboard.  so, in response, i wrote my first, highly inelegant script!  I looked at the[ bash beginner's guide]("http://tldp.org/LDP/Bash-Beginners-Guide/html/")
and[ this old forum thread]("http://ubuntuforums.org/showthread.php?t=842970") and cobbled together this stopgap script that i have to run each time i start ubuntu;
```
#!
xmodmap -e 'keycode 90 = m M m M'
echo "M key fixed"
echo

xmodmap -e 'keycode 63 = p P p P'
echo "p key [half] fixed"
echo

xmodmap -e 'keycode 106 = 0 parenright 0 parenright'
echo "0 key [half] fixed"
echo
 
xmodmap -e 'keycode 83 = u U u U'
echo "U key fixed"
echo
 
xmodmap -e 'keycode 84 = i I i I'
echo "I key fixed"
echo

xmodmap -e 'keycode 85 = o O o O'
echo "O key fixed"
echo
 
xmodmap -e 'keycode 87 = j J j J'
echo "J key fixed"
echo
 
xmodmap -e 'keycode 88 = k K k K'
echo "K key fixed"
echo

xmodmap -e 'keycode 89 = l L l L'
echo "L key fixed"
echo
 
xmodmap -e 'keycode 82 = semicolon colon semicolon colon'
echo "; key fixed"
echo
 
xmodmap -e 'keycode 91 = period greater period greater'
echo ". key fixed"
echo

xmodmap -e 'keycode 86 = slash question question slash'
echo "/ key [half] fixed"
echo
```this makes my computer usable, but i still don't get SHIFT functionality on all the keys.  does anyone have any suggestions for me to improve what i've written, or perhaps a solution rather than a cosmetic fix?

---

