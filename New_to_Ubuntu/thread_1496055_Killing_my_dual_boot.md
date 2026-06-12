---
title: "Killing my dual boot?"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by Astroe on 2010-05-28
Ok, I finally installed Linux. Dual booted Ubuntu 10.04 with Windows 7.

I only dual booted it so that I could transfer about a hundred gigs of video and music from Windows to Ubuntu. The problem now is that if I delete the partition with Windows on it, my computer won't run. And if I reinstall Ubuntu using the whole disk then I lose all the media I've been trying to save. 

So am I ****ed here? I really don't want to lose everything I have now, I just want to be able to use my entire hard drive for linux...

---

### Post by jerenept on 2010-05-28
Why won't it run?
I think that ubuntu will work just fine.

---

### Post by Astroe on 2010-05-28
If I delete the useless windows partition my computer won't boot. Windows runs the boot loader and I don't know how to change that.

---

### Post by oldfred on 2010-05-28
So we can see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by Astroe on 2010-05-28
Ok, I ran that. It makes zero sense to me but here it is.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /menu.lst /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   339,630,164   336,556,117   7 HPFS/NTFS
/dev/sda3         339,632,126   625,141,759   285,509,634   5 Extended
/dev/sda5         579,373,056   623,151,103    43,778,048  83 Linux
/dev/sda6         623,153,152   625,141,759     1,988,608  82 Linux swap / Solaris
/dev/sda7         339,632,128   569,544,703   229,912,576  83 Linux
/dev/sda8         569,546,752   579,368,959     9,822,208  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        FEE6E817E6E7CDC9                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        0A4616B94616A60B                       ntfs       SQ004980V02                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        c7821c36-fec0-4354-a47f-793d41b36c8c   ext4                                     
/dev/sda6        5137ef31-1fde-4519-9ba4-b3ec94047031   swap                                     
/dev/sda7        764658f4-de67-4604-8c7a-cb27823f971c   ext4                                     
/dev/sda8        4c2afd5e-d64a-4cd8-b4ef-e42f8331fa64   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/SQ004980V02       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/c7821c36-fec0-4354-a47f-793d41b36c8c ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda2/menu.lst: ================================

# This grldr.lst menu is for the new topologilinux bootloader 
# it is of the same syntax as grub's menu.lst with the addition of  
# the --set-root option to the find command. "find --set-root" is a 
# new command that finds the filename passed to it and sets the 
# first drive that file is found on as the root drive.  
# The filename passed to findroot must be unique on all partitions  
# and drives so if you would like to boot a version of 
# linux on a later drive /boot/bzImage would not be a good value for findroot. 
# the file can be a dummy file created only for the purpose of identifying the  
# partiton. 
# 
# Sample boot menu configuration file for Topologilinux 
# This is a sample to show new initrd options 
# This file can be placed on any partition but must be in the root of the drive 
 
# Boot automatically after 12 secs. 
timeout 12 
 
# By default, boot the first entry. 
default 0 
 
# Fallback to the second entry. 
fallback 1 
 
# this is the normal way to boot with new initrd  
# frame buffer options can be added too 
title Run Topologilinux in 1024x768 256color mode 
find --set-root /tlinux6/initrd.gz 
kernel /tlinux6/bzImage root=/dev/ram0 vga=773 init=/linuxrc rw 
initrd /tlinux6/initrd.gz 
 
# this is the normal way to boot with new initrd  
# frame buffer options can be added too 
title Run Topologilinux 
find --set-root /tlinux6/initrd.gz 
kernel /tlinux6/bzImage root=/dev/ram0 init=/linuxrc rw 
initrd /tlinux6/initrd.gz 
 
# this is the normal way to boot with new initrd  
# frame buffer options can be added too  
title Run Topologilinux (hdc as scssi cdrom) 
find --set-root /tlinux6/initrd.gz 
kernel /tlinux6/bzImage root=/dev/ram0 hdc=ide-scsi vga=773 init=/linuxrc rw 
initrd /tlinux6/initrd.gz 
 
# this is the normal way to boot with new initrd  
# frame buffer options can be added too 
title Run Topologilinux (hdd as scssi cdrom) 
find --set-root /tlinux6/initrd.gz 
kernel /tlinux6/bzImage root=/dev/ram0 hdd=ide-scsi vga=773 init=/linuxrc rw 
initrd /tlinux6/initrd.gz 
 
#by passing the keyword Tsetup here we tell initrd to act as setup.gz 
title Install Topologilinux (only once for installation) 
find --set-root /tlinux6/setup.gz  
kernel /tlinux6/bzImage root=/dev/ram0 init=/linuxrc Tsetup rw 
initrd /tlinux6/setup.gz 
 
title Back to ntldr 
find --set-root /ntldr 
chainloader +1 
 
 

================================ sda2/boot.ini: ================================

  
C:\grldr="Topologilinux 6.1.0"  

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: menu.lst

=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set c7821c36-fec0-4354-a47f-793d41b36c8c
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
search --no-floppy --fs-uuid --set c7821c36-fec0-4354-a47f-793d41b36c8c
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c7821c36-fec0-4354-a47f-793d41b36c8c
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=c7821c36-fec0-4354-a47f-793d41b36c8c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c7821c36-fec0-4354-a47f-793d41b36c8c
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=c7821c36-fec0-4354-a47f-793d41b36c8c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c7821c36-fec0-4354-a47f-793d41b36c8c
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c7821c36-fec0-4354-a47f-793d41b36c8c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c7821c36-fec0-4354-a47f-793d41b36c8c
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c7821c36-fec0-4354-a47f-793d41b36c8c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c7821c36-fec0-4354-a47f-793d41b36c8c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c7821c36-fec0-4354-a47f-793d41b36c8c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0a4616b94616a60b
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c7821c36-fec0-4354-a47f-793d41b36c8c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5137ef31-1fde-4519-9ba4-b3ec94047031 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 311.8GB: boot/grub/core.img
 303.5GB: boot/grub/grub.cfg
 311.8GB: boot/initrd.img-2.6.32-21-generic
 313.8GB: boot/initrd.img-2.6.32-22-generic
 296.7GB: boot/vmlinuz-2.6.32-21-generic
 308.6GB: boot/vmlinuz-2.6.32-22-generic
 313.8GB: initrd.img
 311.8GB: initrd.img.old
 308.6GB: vmlinuz
 296.7GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 764658f4-de67-4604-8c7a-cb27823f971c
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 764658f4-de67-4604-8c7a-cb27823f971c
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 764658f4-de67-4604-8c7a-cb27823f971c
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=764658f4-de67-4604-8c7a-cb27823f971c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 764658f4-de67-4604-8c7a-cb27823f971c
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=764658f4-de67-4604-8c7a-cb27823f971c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 764658f4-de67-4604-8c7a-cb27823f971c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 764658f4-de67-4604-8c7a-cb27823f971c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0a4616b94616a60b
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c7821c36-fec0-4354-a47f-793d41b36c8c
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=c7821c36-fec0-4354-a47f-793d41b36c8c ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c7821c36-fec0-4354-a47f-793d41b36c8c
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=c7821c36-fec0-4354-a47f-793d41b36c8c ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c7821c36-fec0-4354-a47f-793d41b36c8c
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=c7821c36-fec0-4354-a47f-793d41b36c8c ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c7821c36-fec0-4354-a47f-793d41b36c8c
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=c7821c36-fec0-4354-a47f-793d41b36c8c ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=764658f4-de67-4604-8c7a-cb27823f971c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=4c2afd5e-d64a-4cd8-b4ef-e42f8331fa64 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 225.5GB: boot/grub/core.img
 219.1GB: boot/grub/grub.cfg
 225.6GB: boot/initrd.img-2.6.32-21-generic
 225.5GB: boot/vmlinuz-2.6.32-21-generic
 225.6GB: initrd.img
 225.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  59 82 93 d9 0d 2e 09 12  fb c7 88 27 8f 18 2d 69  |Y..........'..-i|
00000010  08 a1 2a 5e 08 32 e1 30  5a 1c 07 a1 51 76 fb 89  |..*^.2.0Z...Qv..|
00000020  9e d2 46 37 76 e0 15 2b  94 bf 32 b4 4d 77 9f 7d  |..F7v..+..2.Mw.}|
00000030  b2 64 bc 33 52 c0 bd 42  36 ac c8 20 6d bf 81 64  |.d.3R..B6.. m..d|
00000040  4e b2 d9 bc 00 63 d8 91  31 64 ea fc 52 b6 c7 92  |N....c..1d..R...|
00000050  13 dc ca 4e ce 8d 5d 2b  04 32 40 15 a0 40 6d ab  |...N..]+.2@..@m.|
00000060  95 c4 b4 d8 14 72 d5 a0  e9 8d 1d c0 10 50 e4 d0  |.....r.......P..|
00000070  92 16 98 06 43 bd 35 1d  e1 02 32 be 3d 93 c0 5f  |....C.5...2.=.._|
00000080  47 2f e5 52 08 a4 7d 86  cf 80 66 72 2d 94 00 25  |G/.R..}...fr-..%|
00000090  7e d4 04 c1 f4 32 ba d5  a4 4d b2 5f 09 a0 83 d5  |~....2...M._....|
000000a0  26 8a 24 7c d8 86 7b b9  18 00 52 2c 13 4c d9 f1  |&.$|..{...R,.L..|
000000b0  00 54 c8 2d f7 35 ef bb  70 38 14 ab 62 84 be c1  |.T.-.5..p8..b...|
000000c0  f1 9a 7d 26 8b 61 36 1a  5c 12 38 ec 7d bb 4f 2c  |..}&.a6.\.8.}.O,|
000000d0  3f 95 fd da 99 c2 7a 14  0a 6d 84 96 00 68 d9 b2  |?.....z..m...h..|
000000e0  b9 44 09 e5 c0 e8 a5 66  80 9a f6 87 4f ef 4f f8  |.D.....f....O.O.|
000000f0  e1 2f 2d 1a 68 1c 05 4b  5f f5 f9 94 bf c2 41 c2  |./-.h..K_.....A.|
00000100  aa df 54 5c e1 1a 49 0b  a2 0e 2f 2b 66 0c 6f 57  |..T\..I.../+f.oW|
00000110  de 8c fb 77 44 63 44 53  25 1b 4a f2 c2 6a 76 eb  |...wDcDS%.J..jv.|
00000120  36 35 c7 c5 2c 15 2c 09  ef ea 74 97 da 0a 69 f3  |65..,.,...t...i.|
00000130  89 07 4c 40 01 96 d1 08  e8 ad 03 a4 c7 c3 cc 57  |..L@...........W|
00000140  87 28 6b af 3d 82 07 b1  f7 4a 12 f1 b9 dd 72 80  |.(k.=....J....r.|
00000150  ae ab 2d ce da 68 e6 c8  d4 ba 37 60 18 eb 98 8d  |..-..h....7`....|
00000160  66 da 36 a2 28 5a 5e 32  86 a8 69 4a 22 f7 cd e3  |f.6.(Z^2..iJ"...|
00000170  9f 13 d4 58 2e c7 b9 b2  f0 f3 63 95 b5 f4 d4 d7  |...X......c.....|
00000180  7e 29 21 d2 8d d1 13 d8  9e de 38 45 47 ba d9 bd  |~)!.......8EG...|
00000190  ad 6d 40 3c d6 b3 62 52  73 b2 46 8e 05 c3 8b fa  |.m@<..bRs.F.....|
000001a0  89 9a 1c 70 9e ee 0c a6  eb 4a ab 21 ee fb 93 8f  |...p.....J.!....|
000001b0  85 f4 3b b4 84 b5 da 36  af e1 3b ab 75 2f 00 fe  |..;....6..;.u/..|
000001c0  ff ff 83 fe ff ff 02 28  4a 0e 00 00 9c 02 00 fe  |.......(J.......|
000001d0  ff ff 05 fe ff ff 02 28  e6 10 00 60 1e 00 00 00  |.......(...`....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

Edit: Does this say I have Ubuntu installed twice?

---

### Post by oldfred on 2010-05-28
Yes you have linux installed twice. Your second install in sda7 is the one you are using. 

Are you keeping win7?

The win7 boot partition has some extra stuff that may cause problems with windows. [COLOR=DarkRed]windows files[/COLOR]
/menu.lst <-grub legacy
 /boot.ini <- win XP
 [COLOR=DarkRed]/bootmgr
 /Boot/BCD 
/Windows/System32/winload.exe[/COLOR]
 /grldr  <-wingrub C:\grldr="Topologilinux 6.1.0" 

I think you should remove the non-windows files.

I so not see any reason why you cannot delete windows if you want. I would not delete partitions but convert them to /home and or /data where you put your data. I prefer not to have lots of data in the system partition whether it is windows or any version of linux. You can also delete or reuse the first Ubuntu install and its swap.

I used this to move /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by Astroe on 2010-05-28
Ok, I googled how to reinstall grub, then booted from the live CD and used Gparted to consolidate everything into only one partition, the working ubuntu partition, and reinstalled grub. Thanks to NinoScript from the Oregon LoCo team, and thanks oldfred for that boot info script. I can see that coming in handy once I figure out how to read it :)

---

