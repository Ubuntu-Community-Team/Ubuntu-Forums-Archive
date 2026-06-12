---
title: "modprobe fatal error ?????"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by wiggy25 on 2011-01-03
Hope some one can help with this!

I have re-installed Ubuntu 10.10 and re-partioned the drive to give me a separate / partion and /home partion.

All of this is working well and everything boots up as required, but I now have this error mesaage appearing.

I switch on PC, boot loader comes on it defaults to Linux carries on with the load but displays two lines showing this message, both are the same:-

> modprobe: FATAL : could not load/lib/modules/2.6.35-24 generic-modules.dep : no such file or directorySo there are two lines both showing the above, but the load continues and Ubuntu 10.10 loads as normal everything fine.

It's just annoying that this flashes up for what seems like no reason, is there anything I can do to get rid of it?

I have put these screen shots in as well for further information, if you need anything else please be VERY basic with me still very new to this!

[[IMG]http://i106.photobucket.com/albums/m280/wiggy25/th_Screenshot-1-1.png[/IMG]]("http://s106.photobucket.com/albums/m280/wiggy25/?action=view&current=Screenshot-1-1.png")
[[IMG]http://i106.photobucket.com/albums/m280/wiggy25/th_Screenshot-2.png[/IMG]]("http://s106.photobucket.com/albums/m280/wiggy25/?action=view&current=Screenshot-2.png")

Ouptut of Boot Info Script:-
 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    10,487,807    10,485,760  27 Hidden HPFS/NTFS
/dev/sda2    *     10,487,808   344,887,284   334,399,477   7 HPFS/NTFS
/dev/sda3         344,887,294   488,396,799   143,509,506   5 Extended
/dev/sda5         344,887,296   365,432,831    20,545,536  83 Linux
/dev/sda6         482,459,648   488,396,799     5,937,152  82 Linux swap / Solaris
/dev/sda7         365,434,880   482,457,599   117,022,720  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        32C49991C49957C5                       ntfs       WINRE                         
/dev/sda2        043E98713E985E0C                       ntfs       SYSTEM                        
/dev/sda3: PTTYPE="dos" 
/dev/sda5        756a03ed-a408-4145-93c4-d9e4a2b7be9d   ext4                                     
/dev/sda6        54c1f5e1-3ff6-4d35-b8ac-a11e9dd51a4c   swap                                     
/dev/sda7        96335ae5-6de8-4c92-a02a-84279385b8c3   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 756a03ed-a408-4145-93c4-d9e4a2b7be9d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 756a03ed-a408-4145-93c4-d9e4a2b7be9d
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 756a03ed-a408-4145-93c4-d9e4a2b7be9d
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=756a03ed-a408-4145-93c4-d9e4a2b7be9d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 756a03ed-a408-4145-93c4-d9e4a2b7be9d
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=756a03ed-a408-4145-93c4-d9e4a2b7be9d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 756a03ed-a408-4145-93c4-d9e4a2b7be9d
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=756a03ed-a408-4145-93c4-d9e4a2b7be9d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 756a03ed-a408-4145-93c4-d9e4a2b7be9d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=756a03ed-a408-4145-93c4-d9e4a2b7be9d ro single 
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
    search --no-floppy --fs-uuid --set 756a03ed-a408-4145-93c4-d9e4a2b7be9d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 756a03ed-a408-4145-93c4-d9e4a2b7be9d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 043e98713e985e0c
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
# / was on /dev/sda5 during installation
UUID=756a03ed-a408-4145-93c4-d9e4a2b7be9d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=96335ae5-6de8-4c92-a02a-84279385b8c3 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=54c1f5e1-3ff6-4d35-b8ac-a11e9dd51a4c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 185.9GB: boot/grub/core.img
 178.9GB: boot/grub/grub.cfg
 177.4GB: boot/initrd.img-2.6.35-22-generic
 177.4GB: boot/initrd.img-2.6.35-24-generic
 186.0GB: boot/vmlinuz-2.6.35-22-generic
 186.0GB: boot/vmlinuz-2.6.35-24-generic
 177.4GB: initrd.img
 177.4GB: initrd.img.old
 186.0GB: vmlinuz
 186.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```Cheers

Ian

---

### Post by cariboo on 2011-01-04
Does the file exist? Have a look in /lib/modules/2.6.35-24-generic/

---

### Post by wiggy25 on 2011-01-04
No it doesn't exist.

When I try to look in there it responds with can't access file doesn't exist.

Cheers

Ian

---

### Post by blackdalek on 2011-01-16
I get the same error when my machine boots up. ("modprobe: FATAL : could not load/lib/modules/2.6.35-24 generic-modules.dep : no such file or directory" ...twice)

However the file DOES exist in /lib/modules/2.6.35-24-generic/modules.dep on my machine.

---

### Post by netizen99 on 2011-01-31
I have the same issue, I install Ubuntu in separate partition and delete the partition and install Ubuntu 10.10. After installation, I have 2 lines of below error and the system can be startup after sometimes later. Any hints how to fix it?

modprobe : Fatal: Could not load /lib/modules/2.6.35-24-generic/modules.dep no such file or directory

This issue have gone after I upgrade to 11.10.

---

### Post by GingaSnaps on 2011-01-31
I get the same error then my screen goes blue and says "no signal"....

I get a third line after that then the screen goes black, then blue where is says no signal

---

