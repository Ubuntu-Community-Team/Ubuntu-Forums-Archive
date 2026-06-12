---
title: "Windows partition problems"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by robotz421 on 2011-05-11
Ubuntu 10.04

When I try to list or copy files from my Windows partition on a dual boot setup, I often get input/output errors.  How can I fix/get around this?

---

### Post by Hedgehog1 on 2011-05-11
We need to get a look at what format your partitions have.

From Ubuntu, please do this::

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by robotz421 on 2011-05-13
Please note: my initial post of my Ubuntu version was incorrect.  I edited it and it is now correct and should read 10.04 (Lucid).

Here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sda2    *     31,459,328    31,664,127       204,800   7 HPFS/NTFS
/dev/sda3          31,664,128 1,184,713,999 1,153,049,872   7 HPFS/NTFS
/dev/sda4       1,184,714,750 1,953,523,711   768,808,962   5 Extended
/dev/sda5       1,184,714,752 1,922,320,383   737,605,632  83 Linux
/dev/sda6       1,922,322,432 1,953,523,711    31,201,280  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0404B55D04B55282                       ntfs       PQSERVICE                     
/dev/sda2        6040B5FB40B5D7CC                       ntfs       SYSTEM RESERVED               
/dev/sda3        FC0EB7C60EB7786A                       ntfs       Gateway                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        70ba9340-b5ac-432c-ab0a-d419970b638f   ext4                                     
/dev/sda6        653c8ecc-135c-4717-bf66-e7e8507d5905   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/Gateway           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/SYSTEM RESERVED   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 70ba9340-b5ac-432c-ab0a-d419970b638f
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
search --no-floppy --fs-uuid --set 70ba9340-b5ac-432c-ab0a-d419970b638f
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 70ba9340-b5ac-432c-ab0a-d419970b638f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=70ba9340-b5ac-432c-ab0a-d419970b638f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 70ba9340-b5ac-432c-ab0a-d419970b638f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=70ba9340-b5ac-432c-ab0a-d419970b638f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 70ba9340-b5ac-432c-ab0a-d419970b638f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 70ba9340-b5ac-432c-ab0a-d419970b638f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0404b55d04b55282
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6040b5fb40b5d7cc
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
UUID=70ba9340-b5ac-432c-ab0a-d419970b638f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=653c8ecc-135c-4717-bf66-e7e8507d5905 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 611.0GB: boot/grub/core.img
 812.8GB: boot/grub/grub.cfg
 606.9GB: boot/initrd.img-2.6.32-24-generic
 611.0GB: boot/vmlinuz-2.6.32-24-generic
 606.9GB: initrd.img
 611.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 

```

---

### Post by sandyd on 2011-05-13
> **robotz421 said:**
> Please note: my initial post of my Ubuntu version was incorrect.  I edited it and it is now correct and should read 10.04 (Lucid).

Here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sda2    *     31,459,328    31,664,127       204,800   7 HPFS/NTFS
/dev/sda3          31,664,128 1,184,713,999 1,153,049,872   7 HPFS/NTFS
/dev/sda4       1,184,714,750 1,953,523,711   768,808,962   5 Extended
/dev/sda5       1,184,714,752 1,922,320,383   737,605,632  83 Linux
/dev/sda6       1,922,322,432 1,953,523,711    31,201,280  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0404B55D04B55282                       ntfs       PQSERVICE                     
/dev/sda2        6040B5FB40B5D7CC                       ntfs       SYSTEM RESERVED               
/dev/sda3        FC0EB7C60EB7786A                       ntfs       Gateway                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        70ba9340-b5ac-432c-ab0a-d419970b638f   ext4                                     
/dev/sda6        653c8ecc-135c-4717-bf66-e7e8507d5905   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/Gateway           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/SYSTEM RESERVED   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 70ba9340-b5ac-432c-ab0a-d419970b638f
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
search --no-floppy --fs-uuid --set 70ba9340-b5ac-432c-ab0a-d419970b638f
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 70ba9340-b5ac-432c-ab0a-d419970b638f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=70ba9340-b5ac-432c-ab0a-d419970b638f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 70ba9340-b5ac-432c-ab0a-d419970b638f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=70ba9340-b5ac-432c-ab0a-d419970b638f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 70ba9340-b5ac-432c-ab0a-d419970b638f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 70ba9340-b5ac-432c-ab0a-d419970b638f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0404b55d04b55282
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6040b5fb40b5d7cc
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
UUID=70ba9340-b5ac-432c-ab0a-d419970b638f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=653c8ecc-135c-4717-bf66-e7e8507d5905 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 611.0GB: boot/grub/core.img
 812.8GB: boot/grub/grub.cfg
 606.9GB: boot/initrd.img-2.6.32-24-generic
 611.0GB: boot/vmlinuz-2.6.32-24-generic
 606.9GB: initrd.img
 611.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 

```
Check your disk with disk checking software of windows checkdisk (right click on drive in windows, properties, tools?, Disk check). I/O errors are an indication of problems with the hard drive.

---

### Post by BertN45 on 2011-05-13
You could start Disk Utility in Ubuntu and click on the SMART Data. Check the smart data for red entries.
You could also run the self test, that will check the disk surface for errors.

In windows you have to right click the disk, choose properties and select the second tab: Extra. Check the volume for errors and tick both choices (the surface check and the repair options). Probably it will propose to do the test on the next reboot.

---

