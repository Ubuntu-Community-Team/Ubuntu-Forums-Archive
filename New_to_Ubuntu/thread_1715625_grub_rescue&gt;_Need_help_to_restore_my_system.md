---
title: "grub rescue&gt; Need help to restore my system"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by Pablo33 on 2011-03-27
Hello. I had installed ubuntu 10.04 on my desktop pc, and I wanted to try xubuntu, so I installed it on another hard drive on the same computer. It was all fine and I was able to boot from both of them, until I detached Xubuntu hard-drive. Now I can't boot my first and beloved almost-year-old ubuntu 10.04 system.

I'm following instructions from "The Grub Rescue Mode Megathread", and ran the *boot info script* by forum member *meierfra*.

Now I've lost my xubuntu installation, and I can't boot anything, but my Ubuntu 10.04 is still there.

I am at this point now:
I boot from ubuntu 10.04 live-cd, I can access to my file-system partition by mounting it in** /media** , but I don't know what to do now. Need some help. Thanks.

Here is the *boot script info *output  ("results.txt").


```
                                   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8622 MB, 8622931968 bytes
255 heads, 63 sectors/track, 1048 cylinders, total 16841664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    16,017,407    16,015,360  83 Linux
/dev/sdb2          16,019,454    16,840,703       821,250   5 Extended
/dev/sdb5          16,019,456    16,840,703       821,248  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 529 MB, 529661440 bytes
32 heads, 32 sectors/track, 1010 cylinders, total 1034495 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             32     1,034,494     1,034,463   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda         57144d27-1e26-4df9-8fc4-b9b2e155552e   ext4       Heracles                      
/dev/sdb1        10422cfc-3913-489e-be55-e5e8559996ec   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        e44a4854-7811-4906-aca6-c56b4a31c34f   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc         64767934-da97-499b-a941-ae84020bb9ac   ext4       Twingo                        
/dev/sdd1        7408-A8BE                              vfat       MR BLACK                      
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/10422cfc-3913-489e-be55-e5e8559996ec ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /media/MR BLACK          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=10422cfc-3913-489e-be55-e5e8559996ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10422cfc-3913-489e-be55-e5e8559996ec
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=10422cfc-3913-489e-be55-e5e8559996ec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e44a4854-7811-4906-aca6-c56b4a31c34f none            swap    sw              0       0

#Floppy disk
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# These are my fixed media.
#UUID=f3993055-083d-40dd-bb7f-4be45032e4eb    /mnt/Pegaso    ext4    rw,user,exec,auto    0    0
UUID=64767934-da97-499b-a941-ae84020bb9ac    /mnt/Twingo    ext4    rw,user,noexec,auto    0    0
#UUID="57144d27-1e26-4df9-8fc4-b9b2e155552e    /mnt/Heracles    ext4    rw,user,noexec,auto    0    0

=================== sdb1: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/core.img
   5.2GB: boot/grub/grub.cfg
   5.1GB: boot/initrd.img-2.6.32-21-generic
   6.0GB: boot/initrd.img-2.6.32-23-generic
   1.6GB: boot/initrd.img-2.6.32-24-generic
   4.0GB: boot/initrd.img-2.6.32-25-generic
   8.1GB: boot/initrd.img-2.6.32-26-generic
   3.2GB: boot/initrd.img-2.6.32-27-generic
   4.4GB: boot/initrd.img-2.6.32-28-generic
    .2GB: boot/initrd.img-2.6.32-29-generic
   4.3GB: boot/initrd.img-2.6.32-30-generic
   5.6GB: boot/vmlinuz-2.6.32-21-generic
   5.9GB: boot/vmlinuz-2.6.32-23-generic
   4.1GB: boot/vmlinuz-2.6.32-24-generic
   7.4GB: boot/vmlinuz-2.6.32-25-generic
   8.1GB: boot/vmlinuz-2.6.32-26-generic
   5.8GB: boot/vmlinuz-2.6.32-27-generic
   6.3GB: boot/vmlinuz-2.6.32-28-generic
   7.5GB: boot/vmlinuz-2.6.32-29-generic
   4.1GB: boot/vmlinuz-2.6.32-30-generic
   4.3GB: initrd.img
    .2GB: initrd.img.old
   4.1GB: vmlinuz
   7.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  c5 64 6e 4e ac 74 05 c5  f6 58 cf 6b 0f 55 ee a6  |.dnN.t...X.k.U..|
00000010  db 39 0c 4c 89 8f 82 92  9b ef c6 65 b1 45 e3 53  |.9.L.......e.E.S|
00000020  4e 15 0a 0e 02 1d f2 af  70 72 27 44 7e 1f 4c bb  |N.......pr'D~.L.|
00000030  de 9f db 5e d9 9e ba f0  f2 4a 6c 6a 98 e3 93 6a  |...^.....Jlj...j|
00000040  4b 97 d6 8d 07 e2 58 ed  96 0f 45 6a 98 47 29 28  |K.....X...Ej.G)(|
00000050  e8 bf 14 86 61 4c a3 ef  4b 2e 9c 9d bd 3f 09 09  |....aL..K....?..|
00000060  9e e1 98 72 f4 f3 e7 fd  d2 08 7d 52 9b 4d 53 09  |...r......}R.MS.|
00000070  0c 3a a8 70 f3 d3 da 3f  39 a7 ff 92 f4 9a 76 f1  |.:.p...?9.....v.|
00000080  a6 36 f1 11 e2 2d ad 6d  7d a1 00 5c c9 d0 f3 0f  |.6...-.m}..\....|
00000090  0d 28 98 32 a7 93 76 5a  18 54 a7 21 9d 5c 6a 23  |.(.2..vZ.T.!.\j#|
000000a0  56 7b da c4 24 9d 15 ba  1d 72 27 62 b8 c4 34 9f  |V{..$....r'b..4.|
000000b0  76 53 e9 0c bd e3 3e 44  ee 6a 4e 77 77 09 ea ec  |vS....>D.jNww...|
000000c0  26 25 c1 69 84 fa b2 21  5a 76 cd fe e7 52 00 b0  |&%.i...!Zv...R..|
000000d0  b8 85 cb c8 3b 30 5d d2  60 a6 ce fc 63 ef c9 fe  |....;0].`...c...|
000000e0  12 2c 01 1c 38 75 c0 52  9b 33 4d bb f6 f9 47 59  |.,..8u.R.3M...GY|
000000f0  2d e6 ea f0 f7 f5 37 30  ef 95 45 00 14 b9 f2 20  |-.....70..E.... |
00000100  53 33 b7 fe a7 9c 6d ac  90 b4 e8 1d de 77 67 71  |S3....m......wgq|
00000110  ee dd 42 83 49 2e b6 64  0a 73 99 b6 d4 d2 ed 98  |..B.I..d.s......|
00000120  a9 81 12 75 19 1d b1 8b  d5 3e 84 0a f9 7d db bc  |...u.....>...}..|
00000130  ed f7 ae 22 d7 ab d5 4d  e7 7b 97 2e 24 4c 42 f2  |..."...M.{..$LB.|
00000140  30 53 93 29 ee f2 c6 1a  a2 27 cf 86 50 f0 29 61  |0S.).....'..P.)a|
00000150  a9 9e 01 d4 bb fb 7f 3e  d5 5f b5 78 90 e2 f8 c3  |.......>._.x....|
00000160  0f 57 ef 08 f7 49 8f 01  63 57 f8 29 79 e1 9d 28  |.W...I..cW.)y..(|
00000170  c4 8c 8c 9b 17 ac 14 0a  a9 b1 96 9f 45 87 c9 c4  |............E...|
00000180  3e b1 1c 99 c7 c0 2c 28  9f a2 b7 44 7a e3 ef 02  |>.....,(...Dz...|
00000190  9f b3 bd de 7c d2 f5 01  00 5d 1b 00 80 c1 98 2e  |....|....]......|
000001a0  19 f7 50 52 59 94 dc 5c  8c f9 20 cf f7 a1 4e 5c  |..PRY..\.. ...N\|
000001b0  39 16 9b a9 df d6 22 06  08 66 6a e8 4e 38 00 2a  |9....."..fj.N8.*|
000001c0  c6 e5 82 fe ff ff 02 00  00 00 00 88 0c 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```Thanks for your help.

---

### Post by bkratz on 2011-03-27
since you are running 10.04 you really are using grub2 not grub. This thread has more up-to-date info.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Pablo33 on 2011-03-27
Thanks a lot ! , it worked perfectly.   :D   I've successfully restored my system.

---

### Post by bkratz on 2011-03-27
> **Pablo33 said:**
> Thanks a lot ! , it worked perfectly.   :D   I've successfully restored my system.



Glad you got it fixed!

---

