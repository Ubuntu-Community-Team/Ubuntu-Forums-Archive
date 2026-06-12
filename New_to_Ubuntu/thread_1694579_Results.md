---
title: "Results"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by KingLex on 2011-02-24
Can someone help me ? And point me in the right direction 
i dont understand why my grub wont start and such - its confusing to explain :confused:```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
 => Grub 2 is installed in the MBR of /dev/sdf and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sde2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sde3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdf1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4098 MB, 4098883584 bytes
128 heads, 63 sectors/track, 992 cylinders, total 8005632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *            190     7,999,487     7,999,298   c W95 FAT32 (LBA)


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63       112,454       112,392  de Dell Utility
/dev/sde2             112,640    31,569,919    31,457,280   7 HPFS/NTFS
/dev/sde3    *     31,569,920 1,250,260,991 1,218,691,072   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63   515,869,177   515,869,115   7 HPFS/NTFS
/dev/sdf2         515,870,718   976,771,071   460,900,354   5 Extended
/dev/sdf5         515,870,720   964,485,119   448,614,400  83 Linux
/dev/sdf6         964,487,168   976,771,071    12,283,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       b0960811-5c4c-44f9-9edb-87a65d08d1e0   ext4                                     
/dev/sdd1        1912-1B21                              vfat       PENDRIVE                      
/dev/sdd: PTTYPE="dos" 
/dev/sde1        07D9-0A10                              vfat       DellUtility                   
/dev/sde2        F222DCA622DC70D9                       ntfs       RECOVERY                      
/dev/sde3        E0FADFBDFADF8E62                       ntfs       OS                            
/dev/sde: PTTYPE="dos" 
/dev/sdf1        A0123EB8123E9370                       ntfs       Lex Drive_HDD                 
/dev/sdf2: PTTYPE="dos" 
/dev/sdf5        105ebc4e-262b-417b-9ac3-849a6060abc8   ext4                                     
/dev/sdf6        d56cb88c-b4d9-4308-a255-60c43e37eb10   swap                                     
/dev/sdf: PTTYPE="dos" 
error: /dev/sda: No medium found
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdf1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdf5        /media/105ebc4e-262b-417b-9ac3-849a6060abc8 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sde3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sdf1/Wubi/boot/grub/grub.cfg: ========================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-25-generic-pae" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a0123eb8123e9370
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=/dev/sdf1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, Linux 2.6.35-25-generic-pae (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a0123eb8123e9370
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=/dev/sdf1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sde3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set e0fadfbdfadf8e62
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdf5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sdf5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdf5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdf5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

============================= sdf1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sdf1/Wubi: Location of files loaded by Grub: =================


  25.9GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-25-generic-pae
  28.0GB: boot/vmlinuz-2.6.35-25-generic-pae
    .5GB: initrd.img
  28.0GB: vmlinuz

=========================== sdf5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 105ebc4e-262b-417b-9ac3-849a6060abc8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f4f688b2f68876a0
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 4ebaae53baae36fd
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set bc4ed40d4ed3bdf8
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

=============================== sdf5/etc/fstab: ===============================

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=105ebc4e-262b-417b-9ac3-849a6060abc8 /               ext4    errors=remount-ro 0       1
UUID=d56cb88c-b4d9-4308-a255-60c43e37eb10 none            swap    sw              0       0

=================== sdf5: Location of files loaded by Grub: ===================


 487.6GB: boot/grub/core.img
 380.3GB: boot/grub/grub.cfg
 265.3GB: boot/initrd.img-2.6.35-22-generic
 267.1GB: boot/initrd.img-2.6.35-25-generic
 487.6GB: boot/vmlinuz-2.6.35-22-generic
 487.6GB: boot/vmlinuz-2.6.35-25-generic
 267.1GB: initrd.img
 265.3GB: initrd.img.old
 487.6GB: vmlinuz
 487.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdd1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 be 00 00 00  |........?.......|
00000020  42 0f 7a 00 cb 3c 00 00  00 00 00 00 02 00 00 00  |B.z..<..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 21 1b 12 19 4e  4f 20 4e 41 4d 45 20 20  |..)!...NO NAME  |
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
00000100  7d 00 66 b8 ba 79 00 00  66 ba 00 00 00 00 bb 00  |}.f..y..f.......|
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

Unknown BootLoader  on sdf2

00000000  5e 85 98 b4 55 97 d3 58  95 16 64 eb 7b fe ca 7f  |^...U..X..d.{...|
00000010  ff 7c b8 6f 5a 2e 22 d6  ef ad 6b 8f a4 3d 34 8b  |.|.oZ."...k..=4.|
00000020  74 10 d5 95 a5 cb eb bd  0a 9b aa d2 9a 9b db b1  |t...............|
00000030  24 b0 88 71 e8 57 55 bf  cb 6a 97 e6 b9 72 ff 08  |$..q.WU..j...r..|
00000040  94 5d 7c f0 15 dc 56 2b  86 25 00 89 35 f8 7f c3  |.]|...V+.%..5...|
00000050  2f 88 6b ff d7 81 45 08  23 55 50 b2 a9 40 7e 97  |/.k...E.#UP..@~.|
00000060  5d f8 14 4c 3f e2 b1 f7  7c 09 1c 0b e2 fe 65 5b  |]..L?...|.....e[|
00000070  bf 7b c5 f4 af 42 55 ab  2e 65 aa 5c 77 07 f9 15  |.{...BU..e.\w...|
00000080  dc 57 b1 9a fd ff f4 c8  96 2b 48 bd ed de 2b 2e  |.W.......+H...+.|
00000090  65 8f 66 34 40 58 34 08  72 98 bd f3 0b fc 46 12  |e.f4@X4.r.....F.|
000000a0  d1 21 29 2c b8 fa bd 63  2b df 46 30 64 08 60 a2  |.!),...c+.F0d.`.|
000000b0  22 d8 8e 45 6f 77 ac 58  a0 90 23 05 7c 61 6f 8b  |"..Eow.X..#.|ao.|
000000c0  93 45 6f 72 86 39 82 bb  29 58 50 50 81 86 bd c6  |.Eor.9..)XPP....|
000000d0  72 dc a5 c4 d8 7a a5 de  ce 46 52 eb ea 12 2d 56  |r....z...FR...-V|
000000e0  2e 4e 2a 50 be e9 d7 ec  56 39 ec b0 ea bc 91 84  |.N*P....V9......|
000000f0  aa aa aa 43 19 52 65 b9  aa d6 96 09 29 5a 5c bc  |...C.Re.....)Z\.|
00000100  91 93 30 3c ad ba 0c 6a  73 4b 53 75 58 1f 92 11  |..0<...jsKSuX...|
00000110  97 db 8a ee 5c bd df 30  0b a0 12 40 9c e2 be fa  |....\..0...@....|
00000120  be 21 40 37 2d 4f 1c 02  84 07 04 44 77 30 fe f2  |.!@7-O.....Dw0..|
00000130  f7 d7 77 8c aa 53 d4 57  ee 66 de f3 8f f6 b1 0a  |..w..S.W.f......|
00000140  e2 ba 57 de ff b3 5e f8  07 f5 68 e7 cb 89 c5 65  |..W...^...h....e|
00000150  fb d7 17 97 a3 b9 88 8b  08 34 56 05 61 0c 47 34  |.........4V.a.G4|
00000160  bb 4f ac bf d7 24 0e 40  9b 8a ef 7a 0d 2a 58 23  |.O...$.@...z.*X#|
00000170  02 25 65 f1 d8 c8 d1 64  cb f1 f8 d0 b3 20 c3 36  |.%e....d..... .6|
00000180  9e f6 33 a4 84 60 b6 89  a5 6b 1f af d0 e2 b5 4b  |..3..`...k.....K|
00000190  77 49 cb 0e fc 63 11 99  8b ed 9b 2f 13 c2 04 52  |wI...c...../...R|
000001a0  cb b5 26 68 af 2f cb d6  3e ba a9 8c 46 b2 74 24  |..&h./..>...F.t$|
000001b0  be b7 f6 32 a9 b2 12 82  55 0f 91 f8 b8 a6 00 fe  |...2....U.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 50 bd 1a 00 fe  |...........P....|
000001d0  ff ff 05 fe ff ff 02 50  bd 1a 00 78 bb 00 00 00  |.......P...x....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sda sdb sdc 
```

---

