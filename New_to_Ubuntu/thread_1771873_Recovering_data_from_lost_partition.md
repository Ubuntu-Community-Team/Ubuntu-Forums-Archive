---
title: "Recovering data from lost partition"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by lcflwt on 2011-05-30
As a newbie, I need some help recovering data from a lost partition.

Initially I need to know what order to perform some tasks to avoid losing/overwriting data that may still exist. See [http://ubuntuforums.org/showthread.php?t=1771759](http://ubuntuforums.org/showthread.php?t=1771759) for info about HOW it occurred.

Tasks I wish to accomplish include:
a. reloading grub, or deleting altogether if I decide to chuck Vista
b. deleting Mint
c. reinstalling Ubuntu UNE
d. recovering the lost partition, specifically a gnucash file, email accounts and misc files.

I have been reading on photo rec, but have not found anything that may recover the gnucash files. I have not made further changes to my system, but I also do not know the size of the partition that was lost, and I am new enough to not be able to make an educated guess.

Please offer opinions and direction.

---

### Post by jtarin on 2011-05-30
Can you boot into Ubuntu normally now?

---

### Post by lcflwt on 2011-05-30
I have not reloaded Ubuntu because I do not want to risk overwriting any recoverable data. I do have Mint that won't allow me to connect to internet. I have another internet enabled computer though and a USB drive.

---

### Post by jtarin on 2011-05-30
Look to [here ]("http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/")and see if there is something you can use in your situation.
TestDisk could be the answer.

---

### Post by lcflwt on 2011-05-31
Testdisk is indeed the answer. I was able to return my partition after seeing that my data did exist! So then that recreated the problem and whack! back to same grub-rescue prompt that started this whole thing off.

A rerun of the bootinfoscript shows the partition is still there and I returned to the previous advice for restoring grub on partition sda5, previously an unused Mint, now labeled with my desired Ubuntu 10.10. Alas, all I got on reboot was an abnormally wide blinking cursor.

I am ready for more direction, please.

---

### Post by lcflwt on 2011-05-31
```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:   Syslinux looks at sector 15234896 of /dev/sdb1 for 
                       its second stage. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    27,265,023    27,262,976   7 NTFS / exFAT / HPFS
/dev/sda2          27,265,024    27,469,823       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          27,469,824   116,579,816    89,109,993   7 NTFS / exFAT / HPFS
/dev/sda4         116,579,862   312,592,769   196,012,908   f W95 Extended (LBA)
/dev/sda5         116,580,352   179,257,343    62,676,992  83 Linux
/dev/sda6         179,259,392   182,032,367     2,772,976  82 Linux swap / Solaris
/dev/sda7         182,044,672   307,165,183   125,120,512  83 Linux
/dev/sda8         307,167,232   312,580,079     5,412,848  82 Linux swap / Solaris

/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62    15,650,907    15,650,846   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FA024C4D024C1155                       ntfs       PQSERVICE
/dev/sda2        0A324CA9324C9B97                       ntfs       SYSTEM RESERVED
/dev/sda3        1C4C4E3A4C4E0EC8                       ntfs       Acer
/dev/sda5        e622a1e6-0bd1-4111-b725-d298eec27874   ext4       
/dev/sda6        342b9f2b-15a1-4daf-9159-2534a6a42a7b   swap       
/dev/sda7        f6b9894a-6b2e-494c-be13-2f3083b4f4af   ext4       
/dev/sda8        0eade7cd-11c7-4569-a2fd-48ee270d309b   swap       
/dev/sdb1        80C3-F877                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=e622a1e6-0bd1-4111-b725-d298eec27874 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=e622a1e6-0bd1-4111-b725-d298eec27874 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=e622a1e6-0bd1-4111-b725-d298eec27874 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=e622a1e6-0bd1-4111-b725-d298eec27874 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=e622a1e6-0bd1-4111-b725-d298eec27874 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=e622a1e6-0bd1-4111-b725-d298eec27874 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=e622a1e6-0bd1-4111-b725-d298eec27874 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=e622a1e6-0bd1-4111-b725-d298eec27874 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e622a1e6-0bd1-4111-b725-d298eec27874 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e622a1e6-0bd1-4111-b725-d298eec27874 ro single 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set e622a1e6-0bd1-4111-b725-d298eec27874
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa024c4d024c1155
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 0a324ca9324c9b97
    chainloader +1
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f6b9894a-6b2e-494c-be13-2f3083b4f4af ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5) -- recovery mode (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f6b9894a-6b2e-494c-be13-2f3083b4f4af ro single
    initrd /boot/initrd.img-2.6.32-21-generic
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=e622a1e6-0bd1-4111-b725-d298eec27874 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=342b9f2b-15a1-4daf-9159-2534a6a42a7b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  61.721149445 = 66.272579584   boot/grub/core.img                             1
  84.017795563 = 90.213421056   boot/grub/grub.cfg                             1
  56.545135498 = 60.714876928   boot/initrd.img-2.6.35-22-generic              1
  56.638935089 = 60.815593472   boot/initrd.img-2.6.35-23-generic              1
  78.220970154 = 83.989127168   boot/initrd.img-2.6.35-24-generic              3
  58.342060089 = 62.644310016   boot/initrd.img-2.6.35-25-generic              2
  57.373817444 = 61.604667392   boot/initrd.img-2.6.35-28-generic              2
  61.843841553 = 66.404319232   boot/vmlinuz-2.6.35-22-generic                 1
  61.847843170 = 66.408615936   boot/vmlinuz-2.6.35-23-generic                 1
  61.851844788 = 66.412912640   boot/vmlinuz-2.6.35-24-generic                 1
  61.855846405 = 66.417209344   boot/vmlinuz-2.6.35-25-generic                 1
  61.863849640 = 66.425802752   boot/vmlinuz-2.6.35-28-generic                 1
  57.373817444 = 61.604667392   initrd.img                                     2
  58.342060089 = 62.644310016   initrd.img.old                                 2
  61.863849640 = 66.425802752   vmlinuz                                        1
  61.855846405 = 66.417209344   vmlinuz.old                                    1

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f6b9894a-6b2e-494c-be13-2f3083b4f4af ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f6b9894a-6b2e-494c-be13-2f3083b4f4af ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f6b9894a-6b2e-494c-be13-2f3083b4f4af
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fa024c4d024c1155
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0a324ca9324c9b97
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f6b9894a-6b2e-494c-be13-2f3083b4f4af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0eade7cd-11c7-4569-a2fd-48ee270d309b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 106.933792114 = 114.819284992  boot/grub/core.img                             1
  90.980461121 = 97.689526272   boot/grub/grub.cfg                             1
 107.068435669 = 114.963857408  boot/initrd.img-2.6.32-21-generic              1
 106.961761475 = 114.849316864  boot/vmlinuz-2.6.32-21-generic                 1
 107.068435669 = 114.963857408  initrd.img                                     1
 106.961761475 = 114.849316864  vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

```This is my bootinfoscript right now. Is there a way to bypass grub and boot into sda5 Ubuntu 10.10 to verify my data is intact then I am willing to get rid of the offending grub and all other OS as opposed to trying to figure out what the problem is.

---

### Post by jtarin on 2011-05-31
[I prefer the CHROOT method. You will need an Ubuntu Live CD.]("https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT")
Or you can follow the less formal instructions [here]("http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/").

---

### Post by oldfred on 2011-05-31
Did you at some point use windows partitioning tools? 
> 
/dev/sda4 ends after the last sector of /dev/sda

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

Fixparts - Repair broken partition tables (not overlapping issues)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Another way:
Use sfdisk to edit partitions and links to how to convert primary/logical
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
sfdisk to fix extended beyond end -partition outside the disk!
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)

---

