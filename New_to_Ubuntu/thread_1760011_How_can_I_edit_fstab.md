---
title: "How can I edit fstab"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by bertoCS on 2011-05-16
I use 2 different HDD which are partitioned. One has Ubuntu 9.04 & the other Ubuntu 10.04. I edited fstab (10.04) & now can't boot.:( Whether I use a LiveCD or Ubuntu 9.04, I can't edit & save the fstab on my 10.04 HDD. Can anyone help me with this? Thanks.

---

### Post by Rubi1200 on 2011-05-16
Hi and welcome to the forums :-)

Are you running as root when you try to modify fstab?

Please post the results of the boot script so we can see what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by bertoCS on 2011-05-16
Thanks for quick response!

Yes, I've tried as root & also hope I've inserted 'quotes' as you wanted?

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

```
 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005ce73

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   976,768,064   976,768,002   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x983dcc43

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    28,563,569    28,563,507  83 Linux
/dev/sdb2          28,563,631    60,050,969    31,487,339   5 Extended
/dev/sdb5          28,563,633    32,467,364     3,903,732  82 Linux swap / Solaris
/dev/sdb6          32,467,428    60,050,969    27,583,542  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00054a23

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    39,439,574    39,439,512  83 Linux
/dev/sdc2          39,439,575    43,552,214     4,112,640   5 Extended
/dev/sdc5          39,455,640    43,552,214     4,096,575  82 Linux swap / Solaris
/dev/sdc3          43,552,215   156,296,384   112,744,170  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F09E-DF43                              vfat       500STUFF                      
/dev/sdb1        d8809860-72c8-46e7-b0d1-1c0ca4bb90cf   ext3                                     
/dev/sdb5        58884df9-ffd3-4493-afac-e00ecf28d363   swap                                     
/dev/sdb6        bbf0f693-5a4f-4848-b9f1-f08288eb854c   ext3                                     
/dev/sdc1        10f5d024-9e20-46c1-a42e-9f7a3c0c1d69   ext4       Lucid                         
/dev/sdc3        e0edf4b4-4fcc-4f4a-a1df-573433944c92   ext4       StoreSpace                    
/dev/sdc5        23c05652-bd9c-4d91-8ce3-5125dcce0155   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-22-generic root=/dev/sdb1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-22-generic root=/dev/sdb1 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-21-generic root=/dev/sdb1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-21-generic root=/dev/sdb1 ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb1 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-19-generic root=/dev/sdb1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-19-generic root=/dev/sdb1 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=d8809860-72c8-46e7-b0d1-1c0ca4bb90cf / ext3 errors=remount-ro 0 1
# Entry for /dev/sdb6 :
UUID=bbf0f693-5a4f-4848-b9f1-f08288eb854c /home ext3 defaults 0 2
# Entry for /dev/sdb5 :
UUID=58884df9-ffd3-4493-afac-e00ecf28d363 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

=================== sdb1: Location of files loaded by Grub: ===================


   8.8GB: boot/grub/core.img
   9.4GB: boot/grub/grub.cfg
   8.7GB: boot/initrd.img-2.6.31-14-generic
   9.2GB: boot/initrd.img-2.6.31-19-generic
  11.4GB: boot/initrd.img-2.6.31-20-generic
   9.0GB: boot/initrd.img-2.6.31-21-generic
  11.1GB: boot/initrd.img-2.6.31-22-generic
   8.8GB: boot/vmlinuz-2.6.31-14-generic
   8.8GB: boot/vmlinuz-2.6.31-19-generic
   8.9GB: boot/vmlinuz-2.6.31-20-generic
   8.8GB: boot/vmlinuz-2.6.31-21-generic
   9.9GB: boot/vmlinuz-2.6.31-22-generic
  11.1GB: initrd.img
   9.0GB: initrd.img.old
   9.9GB: vmlinuz
   8.8GB: vmlinuz.old

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
search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
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
search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
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
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single  quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single  quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single  quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single  quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single  quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single  quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single  quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single  quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro  quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 ro single  quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 10f5d024-9e20-46c1-a42e-9f7a3c0c1d69
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d8809860-72c8-46e7-b0d1-1c0ca4bb90cf
    linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sdb1 ro quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d8809860-72c8-46e7-b0d1-1c0ca4bb90cf
    linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sdb1 ro single
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d8809860-72c8-46e7-b0d1-1c0ca4bb90cf
    linux /boot/vmlinuz-2.6.31-21-generic root=/dev/sdb1 ro quiet splash
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d8809860-72c8-46e7-b0d1-1c0ca4bb90cf
    linux /boot/vmlinuz-2.6.31-21-generic root=/dev/sdb1 ro single
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d8809860-72c8-46e7-b0d1-1c0ca4bb90cf
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb1 ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d8809860-72c8-46e7-b0d1-1c0ca4bb90cf
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb1 ro single
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d8809860-72c8-46e7-b0d1-1c0ca4bb90cf
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sdb1 ro quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d8809860-72c8-46e7-b0d1-1c0ca4bb90cf
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sdb1 ro single
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d8809860-72c8-46e7-b0d1-1c0ca4bb90cf
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d8809860-72c8-46e7-b0d1-1c0ca4bb90cf
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
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
# / was on /dev/sdb1 during installation
UUID=10f5d024-9e20-46c1-a42e-9f7a3c0c1d69 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=58884df9-ffd3-4493-afac-e00ecf28d363 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=23c05652-bd9c-4d91-8ce3-5125dcce0155 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=274FD8681D0C2119 /media/sdc3 /home ext4 defaults 0 2
0
/dev/sda1: LABEL="500STUFF" UUID="F09E-DF43" TYPE="vfat" defaults 0 2

=================== sdc1: Location of files loaded by Grub: ===================


  13.1GB: boot/grub/core.img
  12.5GB: boot/grub/grub.cfg
  13.0GB: boot/initrd.img-2.6.32-21-generic
  13.8GB: boot/initrd.img-2.6.32-24-generic
  15.1GB: boot/initrd.img-2.6.32-25-generic
  14.2GB: boot/initrd.img-2.6.32-26-generic
  14.9GB: boot/initrd.img-2.6.32-27-generic
  12.5GB: boot/initrd.img-2.6.32-28-generic
  13.8GB: boot/initrd.img-2.6.32-29-generic
  15.5GB: boot/initrd.img-2.6.32-30-generic
  12.4GB: boot/initrd.img-2.6.32-31-generic
  13.0GB: boot/vmlinuz-2.6.32-21-generic
  13.1GB: boot/vmlinuz-2.6.32-24-generic
  13.8GB: boot/vmlinuz-2.6.32-25-generic
  14.1GB: boot/vmlinuz-2.6.32-26-generic
  14.5GB: boot/vmlinuz-2.6.32-27-generic
  14.5GB: boot/vmlinuz-2.6.32-28-generic
  13.8GB: boot/vmlinuz-2.6.32-29-generic
   1.8GB: boot/vmlinuz-2.6.32-30-generic
  13.1GB: boot/vmlinuz-2.6.32-31-generic
  12.4GB: initrd.img
  15.5GB: initrd.img.old
  13.1GB: vmlinuz
   1.8GB: vmlinuz.old
```

---

### Post by bertoCS on 2011-05-16
Sorry, forgot to mention - sdc1 is where the fstab file with errors is. I edited the UUID=274FD8681D0C2119 /media/sdc3 /home ext4 defaults 0 2
0 (after I'd tried it as ntfs but then reformatted to ext4, it started giving me an ntfs-3g error message & wouldn't mount at all. It used to be: UUID=274FD8681D0C2119 /media/sdc3 ntfs-3g users 0 0. I renamed it & it mounted immediately).
Then I went and added:
/dev/sda1: LABEL="500STUFF" UUID="F09E-DF43" TYPE="vfat" defaults 0 2

After this I switched off & when I rebooted the next day...I couldn't.

Hope this info helps.

---

### Post by Rubi1200 on 2011-05-16
You could try booting into recovery mode and editing the file, but I think you may need to do this from a LiveCD using the chroot method:

```
sudo mkdir /mnt/temp 
sudo mount /dev/sdc1 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```
The last command should bring you to a root prompt. Then you can open and edit the file without need for additional root privileges.

Edit and save the file then exit and unmount:

```
exit
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
```
Reboot taking out the CD and assuming no errors were reported along the way, keep your fingers crossed.

Please let me know if this works or if you need additional help with anything.

---

### Post by bertoCS on 2011-05-17
Hi Rubi1200

I've just tried your suggestion, applying 1 line at a time in terminal, but when I run the 3rd line, I receive a long error message beginning with "mount: invalid option -- 'B'".

Thanks

---

### Post by Rubi1200 on 2011-05-17
Okay, let me call in some reinforcements to try and help you get this sorted out.

Please hang in there and we will get back to you as soon as possible.

---

### Post by Elfy on 2011-05-17
> **bertoCS said:**
> Thanks for quick response!

Yes, I've tried as root & also hope I've inserted 'quotes' as you wanted?


It's code tags not quote - big difference if you have a look at your post now :)

If you're in a quick reply box add them by typing - [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse]at the end.

---

### Post by drs305 on 2011-05-17
I'm going to assume you are booting from sdc with sdc1's Grub files, and that your boot fails because it can't mount home because of this line. If any of that is wrong please correct me:
> 
UUID=274FD8681D0C2119 /media/sdc3 /home ext4 defaults 0 2

Anyway, for an fstab error you don't need to use chroot. The reason is that fstab is a static file which doesn't get modified during normal operations. And Grub2 looks elsewhere for information, which may be a bit odd but makes sense.

Thus you can simply open the file by any means, make the change, and save it. From the LiveCD, mount sdc1 and edit the file. It looks like you have an erroneous /home entry and below it there is an extra 0 hanging about. Also fstab has two swap entries. I didn't look at swap but you can share one swap between both Ubuntu installations if you'd like.
```
sudo mount /dev/sdc1 /mnt
gksu gedit /mnt/etc/fstab

```

Save the file and reboot.

---

### Post by oldfred on 2011-05-17
It looks like two lines do not follow fstab standards:

```
UUID=274FD8681D0C2119 /media/sdc3 /home ext4 defaults 0 2
0
/dev/sda1: LABEL="500STUFF" UUID="F09E-DF43" TYPE="vfat" defaults 0 2

```

Besides the hanging 0, there are two mounts  in the first line and the second line has what looks like notes or something about the three ways to define a partition, label, UUID & device.

---

### Post by Rubi1200 on 2011-05-17
I think this link will help you understand fstab syntax when it comes time to editing the file:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by bertoCS on 2011-05-18
Thanks to all of you for your input. I'm really impressed.

I tried drs305's suggestion last night & it worked perfectly. It's amazing that with all my research, I don't remember seeing anything like this: gksu gedit /mnt/etc/fstab to edit fstab. I was always finding other options (root, sudo, LiveCD, etc), but none gave rights to edit fstab.

Do any of you have suggestions on where/how I should start to improve my skills using a terminal? Is there a logical, orderly way, or do I just pick up the bits-&-pieces as I fumble along?

Right, now to learn how to mount these partions correctly...

---

### Post by Rubi1200 on 2011-05-18
This is great news :-) I am really pleased you got things worked out and, of course, a huge thanks to drs305 and oldfred for stopping by to help out with this.

Please mark this thread Solved using the Thread Tools near the top of the page. This way, other users who find themselves in a similar situation can find a working solution to help them.

Enjoy!

---

