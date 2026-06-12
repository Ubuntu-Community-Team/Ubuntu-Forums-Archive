---
title: "grub rescue"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by Ichwardort on 2010-06-15
I just installed ubuntu via liveCD and configured it to run in dual boot mode with windows XP
I have installed XP and Ubuntu on different drives. However when I now take out the liveCD I do not see the bootloader menu which lets me chose between ubuntu and xp but rather I get an error

error> no such device (and then a long number)
grub rescue>

following a different post within this board I executed the boot info script which returned the following information

[HTML]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   103,426,469   103,426,407   7 HPFS/NTFS
/dev/sda2         103,426,470   390,716,864   287,290,395   f W95 Ext d (LBA)
/dev/sda5         103,426,533   390,716,864   287,290,332   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4218 MB, 4218421248 bytes
2 heads, 63 sectors/track, 65389 cylinders, total 8239104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             64     8,239,103     8,239,040   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 32.2 GB, 32195477504 bytes
255 heads, 63 sectors/track, 3914 cylinders, total 62881792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    42,395,534    42,395,472  83 Linux
/dev/sdc2          42,395,535    62,878,409    20,482,875   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D06031196031082C                       ntfs       System                        
/dev/sda2: PTTYPE="dos" 
/dev/sda5        01C9548FF00D9BD0                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7C85-ADD0                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        a9f50c58-3cac-4204-93bd-cf05aa521dc0   ext3                                     
/dev/sdc2        265C7FB55C7F7DFD                       ntfs       SSD-NTFS                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/a9f50c58-3cac-4204-93bd-cf05aa521dc0 ext3       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a9f50c58-3cac-4204-93bd-cf05aa521dc0
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set a9f50c58-3cac-4204-93bd-cf05aa521dc0
set locale_dir=($root)/boot/grub/locale
set lang=de
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
menuentry 'Ubuntu, mit Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a9f50c58-3cac-4204-93bd-cf05aa521dc0
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a9f50c58-3cac-4204-93bd-cf05aa521dc0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, mit Linux 2.6.32-22-generic-pae (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a9f50c58-3cac-4204-93bd-cf05aa521dc0
    echo    'Linux 2.6.32-22-generic-pae wird geladen …'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=a9f50c58-3cac-4204-93bd-cf05aa521dc0 ro single 
    echo    'Initiale Ramdisk wird geladen …'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a9f50c58-3cac-4204-93bd-cf05aa521dc0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set a9f50c58-3cac-4204-93bd-cf05aa521dc0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d06031196031082c
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext3    errors=remount-ro 0       1

=================== sdc1: Location of files loaded by Grub: ===================


  11.0GB: boot/grub/core.img
  11.0GB: boot/grub/grub.cfg
  11.0GB: boot/initrd.img-2.6.32-22-generic-pae
  11.0GB: boot/vmlinuz-2.6.32-22-generic-pae
  11.0GB: initrd.img
  11.0GB: vmlinuz
[/HTML]I really need to be able to execute windows XP again and I would love to get ubuntu working in dual boot. Thanks for your help! I really appreciate!

---

### Post by Ichwardort on 2010-06-15
At the moment I am stuck at my LiveCD image :-?
I have installed Ubuntu on a SSD disk which is inserted in the express card slot of my pc ... is it possible that that disk is not available when booting? Sorry, I am a complete newby and do not understand the results when running the boot info script :confused:

Thanks for your help,
I am stuck

---

