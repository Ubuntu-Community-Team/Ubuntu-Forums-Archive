---
title: "how to mannually install bootloader"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by zhoulab on 2011-02-25
I tried install Ubuntu 10.10 alongside 2003 Server (on a different disk) and it worked just fine.  Now when I erased 2003 and try to install the UBUNTU to the mirrored disk (used for 2003os before), the installation stalled because there was a problem install the BOOTLOADER.  I chose the option to skip the bootloader and finish the installation.  Now its down and can not boot to ubuntu,  how do I manually install the bootloader?

---

### Post by wilee-nilee on 2011-02-25
> **zhoulab said:**
> I tried install Ubuntu 10.10 alongside 2003 Server (on a different disk) and it worked just fine.  Now when I erased 2003 and try to install the UBUNTU to the mirrored disk (used for 2003os before), the installation stalled because there was a problem install the BOOTLOADER.  I chose the option to skip the bootloader and finish the installation.  Now its down and can not boot to ubuntu,  how do I manually install the bootloader?

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by zhoulab on 2011-02-25
Thanks a lot.  While i was waiting, i have tried disable the RAID1 thinking that might be the problem.  I probably have made it worse.  

               ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Lilo is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   468,520,959   468,518,912  83 Linux
/dev/sda2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   468,520,959   468,518,912  83 Linux
/dev/sdb2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sdb5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048   468,520,959   468,518,912  83 Linux
/dev/sdd2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sdd5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1               2,048   468,520,959   468,518,912  83 Linux
/dev/sde2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sde5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a44f5973-142f-429d-b9f5-afaf9fcc02c3   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ff60a3ae-1364-498e-b42e-7f2763495fa0   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        10ca5263-f5d0-4fdb-b806-abaaac70d5b7   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        c85cc6f4-15a1-40d8-a1d5-e4d4dee7596f   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdd1        2c15d67b-561b-43dd-9a53-0c72c65de970   ext4                                     
/dev/sdd2: PTTYPE="dos" 
/dev/sdd5        4932b72e-05d9-4666-b179-fb7d5642c5f9   swap                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        2c15d67b-561b-43dd-9a53-0c72c65de970   ext4                                     
/dev/sde2: PTTYPE="dos" 
/dev/sde5        4932b72e-05d9-4666-b179-fb7d5642c5f9   swap                                     
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set a44f5973-142f-429d-b9f5-afaf9fcc02c3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set a44f5973-142f-429d-b9f5-afaf9fcc02c3
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a44f5973-142f-429d-b9f5-afaf9fcc02c3
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=a44f5973-142f-429d-b9f5-afaf9fcc02c3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a44f5973-142f-429d-b9f5-afaf9fcc02c3
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=a44f5973-142f-429d-b9f5-afaf9fcc02c3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a44f5973-142f-429d-b9f5-afaf9fcc02c3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set a44f5973-142f-429d-b9f5-afaf9fcc02c3
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
/dev/sdc1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=ff60a3ae-1364-498e-b42e-7f2763495fa0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 202.0GB: boot/grub/core.img
 124.7GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-25-generic-pae
 202.0GB: boot/vmlinuz-2.6.35-25-generic-pae
    .5GB: initrd.img
 202.0GB: vmlinuz

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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 10ca5263-f5d0-4fdb-b806-abaaac70d5b7
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=10ca5263-f5d0-4fdb-b806-abaaac70d5b7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 10ca5263-f5d0-4fdb-b806-abaaac70d5b7
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=10ca5263-f5d0-4fdb-b806-abaaac70d5b7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 10ca5263-f5d0-4fdb-b806-abaaac70d5b7
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 10ca5263-f5d0-4fdb-b806-abaaac70d5b7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 ro single 
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 10ca5263-f5d0-4fdb-b806-abaaac70d5b7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 10ca5263-f5d0-4fdb-b806-abaaac70d5b7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=2c15d67b-561b-43dd-9a53-0c72c65de970 ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=2c15d67b-561b-43dd-9a53-0c72c65de970 ro single
    initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/mapper/nvidia_aegcccef1 ro quiet splash
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/mapper/nvidia_aegcccef1 ro single
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (on /dev/sdd1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=2c15d67b-561b-43dd-9a53-0c72c65de970 ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode) (on /dev/sdd1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=2c15d67b-561b-43dd-9a53-0c72c65de970 ro single
    initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdd1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/mapper/nvidia_aegcccef1 ro quiet splash
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdd1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/mapper/nvidia_aegcccef1 ro single
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (on /dev/sde1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set a44f5973-142f-429d-b9f5-afaf9fcc02c3
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=a44f5973-142f-429d-b9f5-afaf9fcc02c3 ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode) (on /dev/sde1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set a44f5973-142f-429d-b9f5-afaf9fcc02c3
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=a44f5973-142f-429d-b9f5-afaf9fcc02c3 ro single
    initrd /boot/initrd.img-2.6.35-25-generic-pae
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
UUID=10ca5263-f5d0-4fdb-b806-abaaac70d5b7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c85cc6f4-15a1-40d8-a1d5-e4d4dee7596f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 176.2GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-25-generic-pae
 219.1GB: boot/vmlinuz-2.6.35-25-generic-pae
    .5GB: initrd.img
 219.1GB: vmlinuz

=========================== sdd1/boot/grub/grub.cfg: ===========================

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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/nvidia_aegcccef,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=2c15d67b-561b-43dd-9a53-0c72c65de970 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/nvidia_aegcccef,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=2c15d67b-561b-43dd-9a53-0c72c65de970 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/nvidia_aegcccef,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/mapper/nvidia_aegcccef1 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/nvidia_aegcccef,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/mapper/nvidia_aegcccef1 ro single 
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/nvidia_aegcccef,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/nvidia_aegcccef,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a44f5973-142f-429d-b9f5-afaf9fcc02c3
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=a44f5973-142f-429d-b9f5-afaf9fcc02c3 ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a44f5973-142f-429d-b9f5-afaf9fcc02c3
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=a44f5973-142f-429d-b9f5-afaf9fcc02c3 ro single
    initrd /boot/initrd.img-2.6.35-25-generic-pae
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

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/nvidia_aegcccef1 /               ext4    errors=remount-ro 0       1
/dev/mapper/nvidia_aegcccef5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


 141.8GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-25-generic-pae
 107.5GB: boot/vmlinuz-2.6.35-22-generic
 107.5GB: boot/vmlinuz-2.6.35-25-generic-pae
    .7GB: initrd.img
 107.5GB: vmlinuz

=========================== sde1/boot/grub/grub.cfg: ===========================

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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/nvidia_aegcccef,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=2c15d67b-561b-43dd-9a53-0c72c65de970 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/nvidia_aegcccef,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=2c15d67b-561b-43dd-9a53-0c72c65de970 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/nvidia_aegcccef,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/mapper/nvidia_aegcccef1 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/nvidia_aegcccef,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=/dev/mapper/nvidia_aegcccef1 ro single 
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/nvidia_aegcccef,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/mapper/nvidia_aegcccef,msdos1)'
    search --no-floppy --fs-uuid --set 2c15d67b-561b-43dd-9a53-0c72c65de970
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a44f5973-142f-429d-b9f5-afaf9fcc02c3
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=a44f5973-142f-429d-b9f5-afaf9fcc02c3 ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a44f5973-142f-429d-b9f5-afaf9fcc02c3
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=a44f5973-142f-429d-b9f5-afaf9fcc02c3 ro single
    initrd /boot/initrd.img-2.6.35-25-generic-pae
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

=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/nvidia_aegcccef1 /               ext4    errors=remount-ro 0       1
/dev/mapper/nvidia_aegcccef5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sde1: Location of files loaded by Grub: ===================


 141.8GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-25-generic-pae
 107.5GB: boot/vmlinuz-2.6.35-22-generic
 107.5GB: boot/vmlinuz-2.6.35-25-generic-pae
    .7GB: initrd.img
 107.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  2d ef 51 24 15 9d df 51  da 73 41 27 d7 2b ba 5e  |-.Q$...Q.sA'.+.^|
00000010  aa d1 be 69 6e 14 39 ec  1c 9f ad 9a 83 cd a9 17  |...in.9.........|
00000020  58 6a c7 b2 0e 0e 68 c6  11 f2 e5 80 d9 e0 3c 9f  |Xj....h.......<.|
00000030  cc 4c 4f e0 e9 3d e3 8a  25 70 19 a9 cf a1 e2 29  |.LO..=..%p.....)|
00000040  ac e9 d4 e3 1a 41 c5 b2  8c 0b 06 d9 7a 0a 42 3d  |.....A......z.B=|
00000050  2f 96 eb e4 fb ec 82 f6  6b d3 11 5d c3 86 28 e7  |/.......k..]..(.|
00000060  a1 72 e2 e9 9a 59 b7 13  df c1 b7 00 d6 9d 1b 55  |.r...Y.........U|
00000070  c7 4e 0a 33 63 af f8 be  d9 bb 24 86 a2 ed 0f ec  |.N.3c.....$.....|
00000080  15 09 54 2f e8 96 6c 21  1b b4 ec 42 a5 d8 17 78  |..T/..l!...B...x|
00000090  fe 36 7a d4 de d3 11 26  6c 17 db d6 15 e6 d4 e8  |.6z....&l.......|
000000a0  be 66 a0 c4 d8 fa b1 be  e3 6d 7b 57 5f fb ea 69  |.f.......m{W_..i|
000000b0  c1 53 69 69 ed f1 6a 52  e4 b1 4e 3f c9 a5 bb e8  |.Sii..jR..N?....|
000000c0  f4 2d 00 cc f0 26 cf 9c  af b4 93 ae 0b 96 2a df  |.-...&........*.|
000000d0  c7 39 2b 43 ff bc 49 ec  1c cc 6d bc 01 1e 2a 94  |.9+C..I...m...*.|
000000e0  34 a9 e2 9c 1a ba 0d 16  eb 8f dc 45 b8 07 19 89  |4..........E....|
000000f0  ba c4 1f 59 b5 87 7d 50  37 8b 5e e9 ab 38 6d 6b  |...Y..}P7.^..8mk|
00000100  0a 69 d9 66 01 48 53 73  58 48 29 33 f7 e2 45 c5  |.i.f.HSsXH)3..E.|
00000110  e3 cf aa 81 55 0d 9c 5a  1e 81 89 b8 92 f1 82 c9  |....U..Z........|
00000120  70 9b 57 ed b2 2d dc 9c  17 eb 08 f2 38 01 89 75  |p.W..-......8..u|
00000130  de 74 0d 8a a2 ca 31 51  41 54 d9 17 bd a9 a3 d5  |.t....1QAT......|
00000140  9a 7e 67 0a 10 01 0f a7  53 11 bc e7 a2 fc 9c f6  |.~g.....S.......|
00000150  52 eb 79 04 3e 69 09 21  01 5f 55 3a 42 0e 4b e5  |R.y.>i.!._U:B.K.|
00000160  92 51 59 e2 45 56 f5 5b  9a 50 49 68 5a ed a9 41  |.QY.EV.[.PIhZ..A|
00000170  cd 93 25 0a 7f 58 8b 70  91 6f 07 cf a5 ca bc b0  |..%..X.p.o......|
00000180  59 db 0c 12 db 69 2b d6  73 8d ed b7 3e e4 ec ad  |Y....i+.s...>...|
00000190  39 ce c6 f9 f0 a9 ca 56  6b ad 3c b9 40 5b 6d 7d  |9......Vk.<.@[m}|
000001a0  8b 53 57 7d ab 20 4e 27  6a 8d 82 48 3e f4 ac ef  |.SW}. N'j..H>...|
000001b0  39 1a 2c ab 18 e0 d6 03  22 84 5d f9 53 ec 00 fe  |9.,.....".].S...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 40 2f 01 00 00  |...........@/...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by wilee-nilee on 2011-02-25
So help should come soon, as far as raid goes I'm not familiar. In the mean time if you could look in my signature at the code tags description and edit the text you posted with the (bracketed code tags) at the beginning and at the end as described. This will put all the text in a scrolling box that lines it up better for easier reading.:)

---

### Post by zhoulab on 2011-02-25
I have two on obard CK804 SATA controller, each links to 2 disks.  a 5th one is on a sil3112 controller.  The first 4 used to be in a RAID1 cfg (hardware).  Can I install Ubuntu to the RAID1 directly, or rebuild the RAID after installing to one of the disks?

Many thanks!

---

### Post by zhoulab on 2011-02-25
It's changed now.

---

