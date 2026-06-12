---
title: "Read error when attempting to boot"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by kaboose72 on 2011-06-07
Hi everyone, upon booting my PC and manually selecting the hard drive to boot from (as standard) I obtain a READ ERROR message.  My system has 4 separate hard drives installed: 1 with Windows, 2 x storing files (ntfs) and my Linux installation. 

Looking around on the web I have been able to boot from a live disk and obtain the following output from the boot input script...

```
                  

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc.
 => No known boot loader is installed in the MBR of /dev/sdd.
 => FreeDOS (eXtended FDisk) is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   149,843,967   149,841,920  83 Linux
/dev/sdb2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sdb5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdc2             206,848   390,719,487   390,512,640   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 320.1 GB, 320069031424 bytes
16 heads, 63 sectors/track, 620173 cylinders, total 625134827 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63   625,134,383   625,134,321   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 16.0 GB, 16001036288 bytes
32 heads, 63 sectors/track, 15501 cylinders, total 31252024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             63    31,250,015    31,249,953   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        160470F90470DD65                       ntfs       
/dev/sdb1        8d13449a-b2d4-49eb-87a2-ac7a7eb7b864   ext4       
/dev/sdb5        be9baab4-e498-4f82-8a39-7fdc34426ddd   swap       
/dev/sdc1        A0B84F93B84F673E                       ntfs       System Reserved
/dev/sdc2        EA70592F705903AB                       ntfs       
/dev/sdd1        04700D09700D0362                       ntfs       
/dev/sde1        7FED-2FE5                              vfat       G-16GB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /media/G-16GB            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
if loadfont /usr/share/grub/ascii.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
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
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8d13449a-b2d4-49eb-87a2-ac7a7eb7b864 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8d13449a-b2d4-49eb-87a2-ac7a7eb7b864
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid                  0  0  
/dev/sdb1                                  /               ext4  errors=remount-ro                    0  1  
# swap was on /dev/sdb5 during installation
UUID=be9baab4-e498-4f82-8a39-7fdc34426ddd  none            swap  sw                                   0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8             0  0  
/dev/sda1                                  /media/1TB      ntfs  nls=iso8859-1,umask=0,uid=graeme  0  0  
/dev/sdd1                                  /media/320GB    ntfs  nls=iso8859-1,umask=0,uid=graeme     0  0  


--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  52.132259369 = 55.976587264   boot/grub/core.img                             1
  52.159191132 = 56.005505024   boot/grub/grub.cfg                             1
  52.337978363 = 56.197476352   boot/initrd.img-2.6.32-21-generic              1
  52.274799347 = 56.129638400   boot/initrd.img-2.6.32-23-generic              1
  46.062156677 = 49.458864128   boot/initrd.img-2.6.32-24-generic              2
  65.510505676 = 70.341369856   boot/initrd.img-2.6.32-25-generic              2
  65.636306763 = 70.476447744   boot/initrd.img-2.6.32-26-generic              2
   5.451152802 = 5.853130752    boot/initrd.img-2.6.32-27-generic              2
  47.025493622 = 50.493239296   boot/initrd.img-2.6.32-28-generic              2
  47.219726562 = 50.701795328   boot/initrd.img-2.6.32-29-generic              2
  71.167026520 = 76.415012864   boot/initrd.img-2.6.32-30-generic              2
  26.935134888 = 28.921380864   boot/initrd.img-2.6.32-31-generic              2
  52.132167816 = 55.976488960   boot/vmlinuz-2.6.32-21-generic                 1
  52.262546539 = 56.116482048   boot/vmlinuz-2.6.32-23-generic                 1
  52.341739655 = 56.201515008   boot/vmlinuz-2.6.32-24-generic                 1
  52.297328949 = 56.153829376   boot/vmlinuz-2.6.32-25-generic                 1
  52.254737854 = 56.108097536   boot/vmlinuz-2.6.32-26-generic                 1
  52.325050354 = 56.183595008   boot/vmlinuz-2.6.32-27-generic                 1
  52.258502960 = 56.112140288   boot/vmlinuz-2.6.32-28-generic                 1
  52.317241669 = 56.175210496   boot/vmlinuz-2.6.32-29-generic                 1
  52.321010590 = 56.179257344   boot/vmlinuz-2.6.32-30-generic                 1
  52.286735535 = 56.142454784   boot/vmlinuz-2.6.32-31-generic                 1
  26.935134888 = 28.921380864   initrd.img                                     2
  71.167026520 = 76.415012864   initrd.img.old                                 2
  52.286735535 = 56.142454784   vmlinuz                                        1
  52.321010590 = 56.179257344   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdd

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  b9 b0 81 08 00 00 80 01  |................|
000001c0  01 00 07 0f ff ff 3f 00  00 00 f1 ca 42 25 00 00  |......?.....B%..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```Any ideas as to what is causing the problem? I've attempted various fixs and seem to have come full circle in the error messages I've seen.

---

### Post by Mark Phelps on 2011-06-07
From my read of the script results, you have TWO Windows installations (not ONE as you claim):
Windows XP is on sda
Windows 7 is on sdc

What MIGHT work is the following:
1) disconnect all but the Ubuntu drive -- try booting it alone.  If it doesn't work, reinstall GRUB to that drive from the Ubuntu CD.  Should boot into Ubuntu now.
2) Reconnect the other drives -- but continue to boot from the Ubuntu drive.  THIS is IMPORTANT.
3) Boot into Ubuntu, open a terminal and enter "sudo update-grub".  Should regenerate the GRUB menu and add an entry for Windows 7 (or XP -- don't know which one it will find). Since you have boot manager files on sdc, it might actually find BOTH.

Reboot -- should get a GRUB menu now with entries for all your OSs.

---

### Post by kaboose72 on 2011-06-08
Worked first time! Cheers for the instructions.

- Disconnected all hard drives except the one with Linux on and could boot correctly. 
- Re-installed Grub
- Plugged other drives in (had to swap the Linux hard drive to SATA1 to avoid error messages) and could boot into Ubuntu
- Updated Grub and confirmed boot list worked as expected

Just got to reconfigure my mounts I had set-up and all is well again.

Thanks

---

