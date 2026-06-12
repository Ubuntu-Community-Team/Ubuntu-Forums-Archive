---
title: "Grub2 problems - Ubuntu won't start"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by olamina on 2010-07-27
Hello I started running Ubuntu after my Windows completely crashed. Since my initial hard drive was overly full, Ubuntu was installed on an external hard drive. This week, I was searching for a file and discovered it was probably still on my original hard drive. Problem is I have no idea how to access the original drive from Ubuntu. Anyway long story short, I was trying to create a Windows boot disk when I discovered Ubuntu had too little disk space. I figured I could repartition from the LiveCD and accidentally ended up reinstalling Ubuntu. Now nothing works. 

sudo fdisk -l yields this

Partition table entries are not in disk order

Disk /dev/sdc: 18.2 GB, 18210036736 bytes
255 heads, 63 sectors/track, 2213 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1025     8233281   83  Linux
/dev/sdc2            1026        2213     9542579+   f  W95 Ext'd (LBA)
/dev/sdc5            1026        2213     9542578+   7  HPFS/NTFS


and sudo blkid yields this

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="LaCie" UUID="D4F80E89F80E69D6" TYPE="ntfs" 
/dev/sdb1: LABEL="FREECOM HDD" UUID="11FA-084A" TYPE="vfat" 
/dev/sdb5: UUID="8c82ee74-dc7f-417f-98a1-b72466a5178b" TYPE="ext4" 
/dev/sdb6: UUID="512d66c6-bc66-430a-8413-5791c7289e59" TYPE="swap" 
/dev/sdb7: UUID="0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0" TYPE="ext4" 
/dev/sdc1: UUID="c02941b0-5a56-44e7-b0c2-793526ff7038" TYPE="ext2" 
/dev/sdc5: LABEL="Dexter" UUID="3C78C41478C3CABA" TYPE="ntfs" 

I foolishly followed someone's advice to do this sudo lilo command and it seemed to just make things worse.

So my questions are as follows (in order of importance):

-How do I get my original Ubuntu install to start up again?
- What is the right way to fix the partitions? I think I had some luck with GParted.
- Will booting from a Windows start disk help me to get back to my original hard drive and retrieve some data? 

Thanks in advance for your help.

---

### Post by stlsaint on 2010-07-27
> 
-How do I get my original Ubuntu install to start up again?
- What is the right way to fix the partitions? I think I had some luck with GParted.
- Will booting from a Windows start disk help me to get back to my original hard drive and retrieve some data? 
1. I see that you have two partitions titled ext4. These are both probably your two ubuntu installs. Try entering both to see if either both work or one. Either way your probably looking at deleting some partitions and removing lilo amongst other stuff.
2. Use gparted via the livecd. How you managed to get into the installer for partitioning is beyond me!! ;)
3. You can install ubuntu to an external hdd, boot to that drive and still reach your windows drive from within ubuntu. In your Places tab you should see the other harddrive. By clicking on it you will mount it and have full access to it. Matter fact you can use the livecd on the system without even booting into the external hdd to reach the data on the windows drive.

> I foolishly followed someone's advice to do this sudo lilo command and it seemed to just make things worse.

Yea you probably did as lilo is another bootloader but your not trying to remove grub so there was no need to even come to lilo.
 

So to start fixing your issue:
1. Plug in the external hdd that is housing ubuntu.
2. Boot to the livecd. (unless you can boot to ubuntu in which skip this step.)
3. Come back to the forums on this post and download the bootinfoscript in my signature. 
4. This script will produce a file title: RESULTS.txt. 
5. Paste that txt document to this topic so we can see all of what is going on with the harddrive partitions.

---

### Post by olamina on 2010-07-27
Ok, this is what is in RESULTS. Hope it makes sense to someone....Thanks!

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdb
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,951,736,849 1,951,736,787   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   278,193,591   278,193,529   6 FAT16
/dev/sdb2         287,045,630   312,580,095    25,534,466   5 Extended
/dev/sdb5         294,567,840   303,321,583     8,753,744  83 Linux
/dev/sdb6         312,125,440   312,580,095       454,656  82 Linux swap / Solaris
/dev/sdb7         287,045,632   294,391,124     7,345,493  83 Linux
/dev/sdb8         303,323,136   312,111,103     8,787,968  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 18.2 GB, 18210036736 bytes
255 heads, 63 sectors/track, 2213 cylinders, total 35566478 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    16,466,624    16,466,562  83 Linux
/dev/sdc2          16,466,686    35,551,844    19,085,159   f W95 Ext d (LBA)
/dev/sdc5          16,466,688    35,551,844    19,085,157   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D4F80E89F80E69D6                       ntfs       LaCie                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        11FA-084A                              vfat       FREECOM HDD                   
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        8c82ee74-dc7f-417f-98a1-b72466a5178b   ext4                                     
/dev/sdb6        512d66c6-bc66-430a-8413-5791c7289e59   swap                                     
/dev/sdb7        0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0   ext4                                     
/dev/sdb8        4ed45b4b-9ca4-4a51-900e-a48800466b76   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        c02941b0-5a56-44e7-b0c2-793526ff7038   ext2                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        3C78C41478C3CABA                       ntfs       Dexter                        
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/FREECOM HDD       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1        /media/LaCie             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
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
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 13896e8aa5b0cb51
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=512d66c6-bc66-430a-8413-5791c7289e59 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 152.7GB: boot/grub/core.img
 150.9GB: boot/grub/grub.cfg
 152.9GB: boot/initrd.img-2.6.32-21-generic
 152.7GB: boot/vmlinuz-2.6.32-21-generic
 152.9GB: initrd.img
 152.7GB: vmlinuz

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0
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
search --no-floppy --fs-uuid --set 0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0
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
    search --no-floppy --fs-uuid --set 0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=9a1c02c2-35b1-4186-a2c7-672c3f04c7b0 none            swap    sw              0       0

=================== sdb7: Location of files loaded by Grub: ===================


 150.5GB: boot/grub/core.img
 150.5GB: boot/grub/grub.cfg
 150.6GB: boot/initrd.img-2.6.32-21-generic
 150.5GB: boot/vmlinuz-2.6.32-21-generic
 150.6GB: initrd.img
 150.5GB: vmlinuz

=========================== sdb8/boot/grub/grub.cfg: ===========================

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
set root='(hd1,8)'
search --no-floppy --fs-uuid --set 4ed45b4b-9ca4-4a51-900e-a48800466b76
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
set root='(hd1,8)'
search --no-floppy --fs-uuid --set 4ed45b4b-9ca4-4a51-900e-a48800466b76
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
    set root='(hd1,8)'
    search --no-floppy --fs-uuid --set 4ed45b4b-9ca4-4a51-900e-a48800466b76
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=4ed45b4b-9ca4-4a51-900e-a48800466b76 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,8)'
    search --no-floppy --fs-uuid --set 4ed45b4b-9ca4-4a51-900e-a48800466b76
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=4ed45b4b-9ca4-4a51-900e-a48800466b76 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,8)'
    search --no-floppy --fs-uuid --set 4ed45b4b-9ca4-4a51-900e-a48800466b76
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,8)'
    search --no-floppy --fs-uuid --set 4ed45b4b-9ca4-4a51-900e-a48800466b76
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb7)" {
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set 0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb7)" {
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set 0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=0e0edcf8-c150-44b5-8f0f-42b7f4bcb8a0 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=4ed45b4b-9ca4-4a51-900e-a48800466b76 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=512d66c6-bc66-430a-8413-5791c7289e59 none            swap    sw              0       0

=================== sdb8: Location of files loaded by Grub: ===================


 158.1GB: boot/grub/core.img
 159.3GB: boot/grub/grub.cfg
 159.4GB: boot/initrd.img-2.6.32-21-generic
 159.3GB: boot/vmlinuz-2.6.32-21-generic
 159.4GB: initrd.img
 159.3GB: vmlinuz

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro single
    initrd /boot/initrd.img-2.6.32-21-generic
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
/dev/sdc1       /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=512d66c6-bc66-430a-8413-5791c7289e59 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


   7.8GB: boot/grub/core.img
   7.8GB: boot/grub/grub.cfg
   7.6GB: boot/initrd.img-2.6.32-21-generic
   7.8GB: boot/initrd.img-2.6.32-23-generic
   7.8GB: boot/vmlinuz-2.6.32-21-generic
   7.7GB: boot/vmlinuz-2.6.32-23-generic
   7.8GB: initrd.img
   7.6GB: initrd.img.old
   7.7GB: vmlinuz
   7.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  ce c8 c0 9c 9c 5b 46 dd  31 4b 4f 0c de 93 71 e0  |.....[F.1KO...q.|
00000010  09 7d 46 8d 3d f3 79 c9  9e c3 bc 1c a2 19 13 e1  |.}F.=.y.........|
00000020  f7 89 33 e7 de fb 18 05  a1 7a 62 b8 7e f0 29 7a  |..3......zb.~.)z|
00000030  ac 02 e8 8a 2d 79 33 d3  aa 0c 74 8b 43 35 71 c6  |....-y3...t.C5q.|
00000040  39 e1 93 ef 4d 7e 26 3e  f1 7a 73 d3 04 d5 e7 4c  |9...M~&>.zs....L|
00000050  61 02 e7 8f 00 5b 12 0c  dd c2 92 80 59 e3 cf 78  |a....[......Y..x|
00000060  29 da 7e 3f f6 0f 70 46  82 48 19 e4 03 e3 a8 ae  |).~?..pF.H......|
00000070  6f 5a 07 8b 80 27 1b 00  85 79 47 df be 6c 0d 5f  |oZ...'...yG..l._|
00000080  01 71 1d 52 c0 cb 78 ba  22 84 e5 f7 d1 59 70 19  |.q.R..x."....Yp.|
00000090  ca 3d 46 37 ea 94 8e 12  ea 51 1b c3 a5 ef bb 9d  |.=F7.....Q......|
000000a0  4e de b2 4d 45 e0 a7 76  6f ba 37 1a 2a 2f 54 a6  |N..ME..vo.7.*/T.|
000000b0  75 11 78 18 fc 2d 11 db  4c d9 ca a3 db 8a 31 74  |u.x..-..L.....1t|
000000c0  b3 1a 44 3c ce 77 a4 02  23 3c 67 50 a4 18 d7 11  |..D<.w..#<gP....|
000000d0  d1 63 7a a8 18 0e 8f 87  a0 a6 51 79 a2 29 7f 8b  |.cz.......Qy.)..|
000000e0  be 9c 19 99 f7 0e 80 ff  87 95 4c 2e 57 55 76 37  |..........L.WUv7|
000000f0  e1 ff 95 7f 0b fc 0a 95  55 5f be 0c 95 57 88 3c  |........U_...W.<|
00000100  3d 04 20 51 b6 d6 81 7f  01 bb ed 9a 06 38 04 89  |=. Q.........8..|
00000110  3e c5 02 be 07 02 95 70  54 cf ae 23 59 db 9f 70  |>......pT..#Y..p|
00000120  14 e7 35 c1 bf 41 81 4f  ee 72 09 70 19 27 e8 28  |..5..A.O.r.p.'.(|
00000130  c4 a1 db 60 ca 02 0c 04  25 58 0a 42 f9 f6 4f 97  |...`....%X.B..O.|
00000140  8f d5 81 d0 3f 38 a4 18  ae 77 10 66 30 4e 0c 5e  |....?8...w.f0N.^|
00000150  10 2a 9f d2 e6 c7 be fc  8a 99 bb eb 0b fc 9f 4b  |.*.............K|
00000160  94 17 e6 83 c2 40 2b c1  de 1e 2f b2 6f c7 c9 2c  |.....@+.../.o..,|
00000170  ea 19 00 96 e1 23 f8 5a  e0 14 e2 0d 16 ad 7b 54  |.....#.Z......{T|
00000180  1d db fc 96 37 1a 8b ec  cb ea 8b 08 76 73 f1 72  |....7.......vs.r|
00000190  c6 47 2e 55 1e 7d e1 4d  aa 10 65 1f 7b 44 ab cc  |.G.U.}.M..e.{D..|
000001a0  53 12 7f 6d f1 5c e3 5c  3c 3c 57 85 c0 7d ad 03  |S..m.\.\<<W..}..|
000001b0  64 83 e0 65 74 14 0a 55  59 64 b0 10 8b fc 00 fe  |d..et..UYd......|
000001c0  ff ff 83 fe ff ff a2 c7  72 00 50 92 85 00 00 fe  |........r.P.....|
000001d0  ff ff 05 fe ff ff 02 78  7e 01 00 28 07 00 00 00  |.......x~..(....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by stlsaint on 2010-07-27
Are you on a desktop or laptop? I see many issues that i will address after i see what system you are on!:popcorn:

---

### Post by olamina on 2010-07-27
I'm on a desktop.

---

### Post by jimstar79 on 2010-07-27
i've got a similar problem. 

tried installing ideneb 10.5.5 onto a partition on my hd.

just deleted the partition with Grub. 

BUT the system keeps launching Chameleon...and then just goes onto ideneb (some restart system window which i can not progress past). 

Gparted showed that my original Ubuntu is still there. I just don't know how to launch it - god, i miss my Ubuntu. 

I swear, if i can get back into my Ubuntu i won't be bothering with any other operating system!!

---

### Post by anewguy on 2010-07-27
I haven't had the need for it, but I thought you could boot the livecd and run update-grub and reboot.

---

### Post by stlsaint on 2010-07-27
Issue#1:
```
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #8 for /boot/grub.
=> Lilo is installed in the MBR of /dev/sdb
=> Lilo is installed in the MBR of /dev/sdc

```
You have two bootloaders installed. Grub2 and Lilo. Grub2 is what you should be using which is on /dev/sda which is your primary/master hdd in system. the other two drives (unless you specifically want this) do not need to have a bootloader on them. Grub2 can handle chainloading over to windows if needed.Remove lilo!!

Issue#2: on /sda1 you have your windows xp but without nowhere to boot to! Check out the last line starrting with Boot files... 
```
File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 

```
There should be some windows directory locations there. Not that big an issue as like i said grub2 can hand over the bootloading process to windows and let windows do its thing if need be but since you dont have anything in grub2 neither showing chainloading to windows im lead to believe that windows is faulty and needs to be repaired! ;)

Issue#3:
You have two installs on /sdb and /sdc. One was the original and im assuming the other is the one you tried to fix but ended up installing. It is fine to dual boot two ubuntu' releases, (i do;)) but there are some things you need to do first. 


Fix:
1. Remove lilo from your other two drives.
       a. After you remove lilo than in a terminal run:
```
sudo update-grub
```
2. If you dont want to have two ubuntu installs than format the partition on that drive that is housing ubuntu...here ill help ya... 
Ubuntu is installed on: 
/dev/sdb5 and /dev/sdb7 and /dev/sdb8 also something of ubuntu on /dev/sdc1.

My Recommendation: Since you are farily new i would suggest you backup all files of those drives and format the ubuntu drives and reinstall ubuntu. Than get a windows xp recovery disc and repair windows if you want a dual boot. But if you do opt for the dual boot and you repair windows than you may need to reinstall grub2 to MBR! Please see the GRUB2 link in my signature for that!

---

### Post by olamina on 2010-07-27
> **stlsaint said:**
> Issue#1: Remove lilo!!
Ok, done.

> Issue#2: im lead to believe that windows is faulty and needs to be repaired! ;)I am trying to get my hands on a Windows XP disk, that should solve it, right?

> 
Fix:
1. Remove lilo from your other two drives.
       a. After you remove lilo than in a terminal run:
```
sudo update-grub
```I get this when I type that in. 

[I]ubuntu@ubuntu:~$ sudo update-grub
 /usr/sbin/grub-probe: error: cannot find a device for / (is /dev  mounted[/I]?).
I think I may be missing something there... :(

> My Recommendation: Since you are farily new i would suggest you backup  all files of those drives and format the ubuntu drives and reinstall  ubuntu. Than get a windows xp recovery disc and repair windows if you  want a dual boot.Yeah, I am gonna just backup all the data on that drive, format the sucker and reinstall. I was hoping there'd be an easier way. Ah well, chalk it up experience I guess...

Thanks a bunch!

---

### Post by olamina on 2010-07-28
OK , I'm hoping you're still around stlsaint because things have gone from bad to worse. 

I put in the LiveCD and told it to go ahead and install on the entire drive.  I get the cheery message that everything is installed. The system resets and brings me to a blank screen with just one tiny cursor blinking at me. On reboot I get a "no boot signature in partition". Here's what I got from Bootinfo 

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,951,736,849 1,951,736,787   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   306,620,415   306,618,368  83 Linux
/dev/sdb2         306,622,462   312,580,095     5,957,634   5 Extended
/dev/sdb5         306,622,464   312,580,095     5,957,632  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 18.2 GB, 18210036736 bytes
255 heads, 63 sectors/track, 2213 cylinders, total 35566478 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    16,466,624    16,466,562  83 Linux
/dev/sdc2          16,466,686    35,551,844    19,085,159   f W95 Ext d (LBA)
/dev/sdc5          16,466,688    35,551,844    19,085,157   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D4F80E89F80E69D6                       ntfs       LaCie                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9b953829-c630-49a8-a136-a7089d1d8911   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        05e6e6ab-5bc1-448e-8d2c-09c93493b56d   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        c02941b0-5a56-44e7-b0c2-793526ff7038   ext2                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        3C78C41478C3CABA                       ntfs       Dexter                        
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/9b953829-c630-49a8-a136-a7089d1d8911 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 9b953829-c630-49a8-a136-a7089d1d8911
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 9b953829-c630-49a8-a136-a7089d1d8911
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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9b953829-c630-49a8-a136-a7089d1d8911
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9b953829-c630-49a8-a136-a7089d1d8911 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9b953829-c630-49a8-a136-a7089d1d8911
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9b953829-c630-49a8-a136-a7089d1d8911 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9b953829-c630-49a8-a136-a7089d1d8911
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 9b953829-c630-49a8-a136-a7089d1d8911
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
  97.0GB: boot/grub/grub.cfg
   4.4GB: boot/initrd.img-2.6.32-21-generic
   4.4GB: boot/vmlinuz-2.6.32-21-generic
   4.4GB: initrd.img
   4.4GB: vmlinuz

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro single
    initrd /boot/initrd.img-2.6.32-21-generic
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
/dev/sdc1       /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=512d66c6-bc66-430a-8413-5791c7289e59 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


   7.8GB: boot/grub/core.img
   7.8GB: boot/grub/grub.cfg
   7.6GB: boot/initrd.img-2.6.32-21-generic
   7.8GB: boot/initrd.img-2.6.32-23-generic
   7.8GB: boot/vmlinuz-2.6.32-21-generic
   7.7GB: boot/vmlinuz-2.6.32-23-generic
   7.8GB: initrd.img
   7.6GB: initrd.img.old
   7.7GB: vmlinuz
   7.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  ed 81 00 00 1c 45 00 00  29 44 bf 4b 8e 3f 3e 4c  |.....E..)D.K.?>L|
00000010  29 44 bf 4b 00 00 00 00  00 00 01 00 28 00 00 00  |)D.K........(...|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  05 00 00 00 4b 2a 02 00  |............K*..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 d8 cf 24 79  00 00 00 00 00 00 00 00  |......$y........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 50 c0 ac 45  00 00 00 00 00 00 00 00  |....P..E........|
00000090  8e 3f 3e 4c 08 5b e1 3e  00 00 00 00 00 00 00 00  |.?>L.[.>........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  ed 81 00 00 e4 34 00 00  29 44 bf 4b 8e 3f 3e 4c  |.....4..)D.K.?>L|
00000110  29 44 bf 4b 00 00 00 00  00 00 01 00 20 00 00 00  |)D.K........ ...|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  04 00 00 00 50 2a 02 00  |............P*..|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 d9 cf 24 79  00 00 00 00 00 00 00 00  |......$y........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 50 c0 ac 45  00 00 00 00 00 00 00 00  |....P..E........|
00000190  8e 3f 3e 4c 50 c0 ac 45  00 00 00 00 00 00 00 00  |.?>LP..E........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 5a 00 00 00  |............Z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

This leads me to believe that there are no boot files on sdb or sdc. Why is this the case? Shouldn't the Ubuntu install have sorted this all out?

Im also not sure why Lilo is still on sdc...hmmm. HELP!

---

### Post by varunendra on 2010-07-29
> **olamina said:**
> This leads me to believe that there are no boot files on sdb or sdc. Why is this the case? Shouldn't the Ubuntu install have sorted this all out
Hmmmm.... the long array of drives/partitions is making it a bit confusing for me, but here's what I guess to be your problem....

Currently you have two internal HDDs (1TB & 160GB) and an external one (20GB??). Now Grub2 is installed (only) on 1TB drive (sda) and (if consulted) will look for boot files on the same drive. But there aren't any boot files on it!! :lol:

Next, **your 160GB drive (sdb) is the only one which has 'No boot loader'** on its MBR. However it does have the boot files. I guess this is the drive where Lucid got installed somehow, whereas Grub got installed on sda due to some mistake or misconfiguration.

Let's forget about the external drive (sdc) for sometime.

Now combining this situation with the error message you are  getting-> On reboot I get a "no boot signature in  partition".- it seems like your computer is trying to boot from the 160GB drive (sdb) where there is no boot loader.

Now if this is right, here's a quick fix-

[LIST=1]
[*]disconnect the external drive and boot off a live cd
[*]install GRUB on sdb (using[FONT=Trebuchet MS]** sudo fdisk -l**[/FONT] command, make sure sdb is the 160GB drive)
[*]run sudo update-grub.
[*]reboot and see if it boots into Lucid. You may connect your external HDD then.
[/LIST]

---

### Post by olamina on 2010-07-29
> Currently you have two internal HDDs (1TB & 160GB) and an external  one (20GB??). Now Grub2 is installed (only) on 1TB drive (sda) and (if  consulted) will look for boot files on the same drive. But there aren't  any boot files on it!! :lol:

Well I have one internal HD (20GB( and two external  (160 GB and 1 TB). Ubuntu was previously running on the 160GB drive when it was partitioned. I thought the new Ubuntu install erased everything on that drive and gave me everything I needed, but it didn't. I have no idea what Grub2 is doing on the 1TB drive:confused:

> Now if this is right, here's a quick fix-

[LIST=1]
[*]disconnect the external drive  and boot off a live cd
[*]install GRUB on sdb (using[FONT=Trebuchet MS]** sudo fdisk  -l**[/FONT] command, make sure sdb is the 160GB drive)
[*]run sudo update-grub.
[*]reboot and see if it boots into Lucid. You may connect your external  HDD then.
[/LIST]


As I mentioned sdc is the only INTERNAL drive in the lineup. Should I still go in and disconnect it. I am running off the Live Disk at the moment, isn't there anyway I can go do something like a good old fashioned dos "CD" command and install that way?  Thanks for all your help. I'm doing nothing til I hear back from you. :oops:

---

### Post by varunendra on 2010-07-29
So which drive do you wish to install Lucid in? I'd suggest the one with maximum free space.
You can check it with gparted.

---

### Post by olamina on 2010-07-29
Ubuntu should "already" be installed on the 160GB external drive. I went through the installation process on it. Not sure what happened. If it's not installed, then that is where i *want* it to be.

---

### Post by varunendra on 2010-07-29
> **olamina said:**
> Ubuntu should "already" be installed on the 160GB external drive. I went through the installation process on it. Not sure what happened. If it's not installed, then that is where i *want* it to be.

I can see two possibilities. Try any one of them:

[LIST=1]
[*]To install Grub on sdb itself, disconnect all except sdb (160GB) and reinstall grub on it booting off LiveCD. Then reboot without connecting others and post the result.
[*]To install Grub on the fixed drive (sdc-20GB) disconnect only sda (1TB) and do the following:
[/LIST]

[LIST]
[*]Booting off live CD, remove LILO first ```
lilo -u /dev/sdx
``` where x has to be replaced by the letter your fixed HDD has been assigned. (check it with [FONT=Trebuchet MS]**sudo fdisk -l**[/FONT] command)
[*]Install Grub2 on it```
sudo grub-install /dev/sd**x**
``` (in case you are having problem uninstalling lilo, just skip previous step and come directly to this one. Grub may simply overwrite lilo)
[*]Run ```
sudo update-grub
```
[*]Reboot and post here what happens.
[/LIST]
I'd recommend to go with option 1 because in option 2, booting will fail everytime the external drive is removed.

---

### Post by olamina on 2010-07-29
i tried option 2. alas i don't think it worked. here is what i got.

> ubuntu@ubuntu:~$ lilo -u /dev/sda
The program 'lilo' is currently not installed.  You can install it by typing:
sudo apt-get install lilo
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Finished. The results are in the file RESULTS1.txt located in /home/ubuntu/Desktop
ubuntu@ubuntu:~$ lilo -u /dev/sda1
The program 'lilo' is currently not installed.  You can install it by typing:
sudo apt-get install lilo
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).looking forward to hearing from you when you have more time. thanks so much for your effort. this makes the switch to linux a bit less frightening.

---

### Post by varunendra on 2010-07-29
To uninstall lilo, try the method you used to uninstall it from sdb.

Before installing Grub, the destination drive needs to be mounted.
First, make sure the drive is detected as sda (and installation partition is detected as sda1) Use:
```
sudo fdisk -l
```

To install grub, you may need to chroot. Follow instructions as given [here]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html").

---

### Post by chong601 on 2010-07-29
[http://support.microsoft.com/kb/330184](http://support.microsoft.com/kb/330184)

I think this might help you to rebuild your Boot.ini because it looks like your Boot.ini is missing (might be missing; not so sure)but make sure you have existing installation of Windows XP your computer

---

### Post by olamina on 2010-07-29
> To uninstall lilo, try the method you used to uninstall it from sdb.I didn't uninstall lilo from sdb. When I installed Ubuntu to sdb, I think it removed Lilo by default. How do I remove Lilo? I've tried just about everything. 

> Before installing Grub, the destination drive needs to be mounted.
To install grub, you may need to chroot. Follow instructions as given [here]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html").well this is what i got when i tried that...

ubuntu@ubuntu:~$ sudo mount /dev/sda1/mnt
mount: can't find /dev/sda1/mnt in /etc/fstab or /etc/mtab

what now? i don't even know what linux is doing on sda. should i remove it? how?

> I think this might help you to rebuild your Boot.ini because it looks  like your Boot.ini is missing (might be missing; not so sure)but make  sure you have existing installation of Windows XP your computerI don't have a windows boot disk at the moment. i downloaded one but i cannot burn it to dvd until i get my ubuntu back up and running since the only dvd drive i have is on this machine. 

thanks so much!:shock:

---

### Post by varunendra on 2010-07-29
> what now? i don't even know what linux is doing on sda. should i remove it? how?
Ohh.... Big mistake on my part!!
While suggesting option 2, I forgot that you want to install Lucid in your 160GB drive (sdb). So you MUST leave that one connected!!

In this situation, option 1 is the best way to go (leave **ONLY** sdb connected) if you are sure that Lucid was installed there. Since it is an external drive, it is best that you have Grub installed on it rather than the fixed drive. You can always change the booting device from boot device menu or in the BIOS itself.
So do it now and follow the GRUB installation method from the link I provided.

And oh, there is a space between /dev/sda1 and /mnt. Try copy-pasting commands to avoid typo/syntax errors. :)

Sorry for the confusing suggestion earlier. I'll be here till it is done (if YOU don't give up first of-course). And no need to thank me.... its kinda fun-activity for me ;)

I'm going to edit my earlier post to make it correct.

---

### Post by olamina on 2010-07-29
OK, so I removed that internal drive and just had the 160GB drive attached. I installed Grub (followed the chroot directions which were surprisingly thrilling)  and even got this cheery report in bootinfo

        >         Boot Info Script 0.55    dated February 15th,  2010                    

============================= Boot Info  Summary: ==============================
  
 => Grub 2 is installed in the MBR of /dev/sda and looks on the  same drive in 
    partition #1 for /boot/grub.

sda1:  _________________________________________________________________________

     File system:       ext4
      Boot sector type:  -
    Boot sector info:  
    Operating  System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg  /etc/fstab /boot/grub/core.img

sda2:  _________________________________________________________________________
  
    File system:       Extended Partition
    Boot sector type:   Unknown
    Boot sector info:  

sda5:  _________________________________________________________________________

     File system:       swap
      Boot sector type:  -
    Boot sector info:  

But then I restarted and got this "Minimal bash like line editing is supported" message. Which made me think that maybe Ubuntu wasn't installed after all. So what did I do? Of, course. REINSTALL. 

I restarted again and got this message - **error: out of disk grub rescue>**

Here is what bootinfo is showing now...
> 
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   306,620,415   306,618,368  83 Linux
/dev/sda2         306,622,462   312,580,095     5,957,634   5 Extended
/dev/sda5         306,622,464   312,580,095     5,957,632  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 18.2 GB, 18210036736 bytes
255 heads, 63 sectors/track, 2213 cylinders, total 35566478 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    16,466,624    16,466,562  83 Linux
/dev/sdb2          16,466,686    35,551,844    19,085,159   f W95 Ext d (LBA)
/dev/sdb5          16,466,688    35,551,844    19,085,157   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        c5d9312f-0149-48de-ad1b-f04cb93d1e4e   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        05e6e6ab-5bc1-448e-8d2c-09c93493b56d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c02941b0-5a56-44e7-b0c2-793526ff7038   ext2                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        3C78C41478C3CABA                       ntfs       Dexter                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c5d9312f-0149-48de-ad1b-f04cb93d1e4e
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c5d9312f-0149-48de-ad1b-f04cb93d1e4e
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c5d9312f-0149-48de-ad1b-f04cb93d1e4e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c5d9312f-0149-48de-ad1b-f04cb93d1e4e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c5d9312f-0149-48de-ad1b-f04cb93d1e4e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c5d9312f-0149-48de-ad1b-f04cb93d1e4e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c5d9312f-0149-48de-ad1b-f04cb93d1e4e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c5d9312f-0149-48de-ad1b-f04cb93d1e4e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c5d9312f-0149-48de-ad1b-f04cb93d1e4e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=05e6e6ab-5bc1-448e-8d2c-09c93493b56d none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 129.0GB: boot/grub/core.img
  45.4GB: boot/grub/grub.cfg
 129.0GB: boot/initrd.img-2.6.32-21-generic
 128.9GB: boot/vmlinuz-2.6.32-21-generic
 129.0GB: initrd.img
 128.9GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro single
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=512d66c6-bc66-430a-8413-5791c7289e59 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   7.9GB: boot/grub/core.img
   7.8GB: boot/grub/grub.cfg
   7.6GB: boot/initrd.img-2.6.32-21-generic
   7.8GB: boot/initrd.img-2.6.32-23-generic
   7.8GB: boot/vmlinuz-2.6.32-21-generic
   7.7GB: boot/vmlinuz-2.6.32-23-generic
   7.8GB: initrd.img
   7.6GB: initrd.img.old
   7.7GB: vmlinuz
   7.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ed 81 00 00 1c 45 00 00  29 44 bf 4b 8e 3f 3e 4c  |.....E..)D.K.?>L|
00000010  29 44 bf 4b 00 00 00 00  00 00 01 00 28 00 00 00  |)D.K........(...|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  05 00 00 00 4b 2a 02 00  |............K*..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 d8 cf 24 79  00 00 00 00 00 00 00 00  |......$y........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 50 c0 ac 45  00 00 00 00 00 00 00 00  |....P..E........|
00000090  8e 3f 3e 4c 08 5b e1 3e  00 00 00 00 00 00 00 00  |.?>L.[.>........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  ed 81 00 00 e4 34 00 00  29 44 bf 4b 8e 3f 3e 4c  |.....4..)D.K.?>L|
00000110  29 44 bf 4b 00 00 00 00  00 00 01 00 20 00 00 00  |)D.K........ ...|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  04 00 00 00 50 2a 02 00  |............P*..|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 d9 cf 24 79  00 00 00 00 00 00 00 00  |......$y........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 50 c0 ac 45  00 00 00 00 00 00 00 00  |....P..E........|
00000190  8e 3f 3e 4c 50 c0 ac 45  00 00 00 00 00 00 00 00  |.?>LP..E........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 5a 00 00 00  |............Z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by varunendra on 2010-07-29
Didn't go thoroughly through the boot-info result, but a quick guess-
Did you reconnect the 20GB drive back while reinstalling? You shouldn't have...... (no it's not wrong, but since your setup is so messed up..... u know what I mean..:))

Anyway, try changing boot-device in BIOS 'boot device selection' menu or boot order in BIOS. If it doesn't help, then I'm afraid reinstalling (with only 160GB drive connected) would be the only stupid looking wise idea :(.

You'll have to figure out the 'F' key to bring up the boot device selection menu. Or just go into BIOS and change the boot order there.


PS: use # icon to enclose the boot-info result within [ code] instead of [ quote].

---

### Post by olamina on 2010-07-29
> Did you reconnect the 20GB drive back while reinstalling?

No, I didn't.

> Anyway, try changing boot-device in BIOS 'boot device selection' menu or  boot order in BIOS. If it doesn't help, then I'm afraid reinstalling  (with only 160GB drive connected) would be the only stupid looking wise  idea :sad:.

I'm going to try and change the BIOS and will be right back. I'm willing to try almost anything else, but I don't understand how reinstalling for a third time would solve anything...

Be right back...

---

### Post by varunendra on 2010-07-29
> **olamina said:**
> but I don't understand how reinstalling for a third time would solve anything...

If installing with **ONLY **one drive, then booting also with **ONLY **the same and **ONLY **drive works (which it MUST:evil:) then figuring out any further issues should be quite easy.

This will make sure that at least your installation source and the rest of the hardware has no issues, and is only some problem with drive-configuration which should be easy to overcome once you have a working installation.



PS: Dinner time! Shall be back in half an hour..... :)

---

### Post by olamina on 2010-07-29
> Anyway, try changing boot-device in BIOS 'boot device selection' menu or   boot order in BIOS. If it doesn't help, then I'm afraid reinstalling   (with only 160GB drive connected) would be the only stupid looking wise   idea :sad:. 			 		

So, not sure why or what in the world but I changed the boot device selection and all of a sudden I am where I wanna be with my good old desktop (yes the desktop I had before all this mess started) and bookmarks and stuff. Golly. Things are still buggy but I am in, and that's what matters. 


Here's my final bootinfo. I'll mark this as solved and If I have any new problems, I'll just open a new thread. Thanks SO much. Bon appetit!
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   306,620,415   306,618,368  83 Linux
/dev/sda2         306,622,462   312,580,095     5,957,634   5 Extended
/dev/sda5         306,622,464   312,580,095     5,957,632  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 18.2 GB, 18210036736 bytes
255 heads, 63 sectors/track, 2213 cylinders, total 35566478 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    16,466,624    16,466,562  83 Linux
/dev/sdb2          16,466,686    35,551,844    19,085,159   f W95 Ext d (LBA)
/dev/sdb5          16,466,688    35,551,844    19,085,157   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c5d9312f-0149-48de-ad1b-f04cb93d1e4e   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        05e6e6ab-5bc1-448e-8d2c-09c93493b56d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c02941b0-5a56-44e7-b0c2-793526ff7038   ext2                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        3C78C41478C3CABA                       ntfs       Dexter                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext2       (rw,errors=remount-ro)
/dev/sda1        /media/c5d9312f-0149-48de-ad1b-f04cb93d1e4e ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c5d9312f-0149-48de-ad1b-f04cb93d1e4e
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c5d9312f-0149-48de-ad1b-f04cb93d1e4e
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
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c5d9312f-0149-48de-ad1b-f04cb93d1e4e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c5d9312f-0149-48de-ad1b-f04cb93d1e4e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c5d9312f-0149-48de-ad1b-f04cb93d1e4e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c5d9312f-0149-48de-ad1b-f04cb93d1e4e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c5d9312f-0149-48de-ad1b-f04cb93d1e4e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c5d9312f-0149-48de-ad1b-f04cb93d1e4e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c5d9312f-0149-48de-ad1b-f04cb93d1e4e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=05e6e6ab-5bc1-448e-8d2c-09c93493b56d none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 129.0GB: boot/grub/core.img
  45.4GB: boot/grub/grub.cfg
 129.0GB: boot/initrd.img-2.6.32-21-generic
 128.9GB: boot/vmlinuz-2.6.32-21-generic
 129.0GB: initrd.img
 128.9GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c02941b0-5a56-44e7-b0c2-793526ff7038 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c02941b0-5a56-44e7-b0c2-793526ff7038
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8c82ee74-dc7f-417f-98a1-b72466a5178b
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=8c82ee74-dc7f-417f-98a1-b72466a5178b ro single
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=512d66c6-bc66-430a-8413-5791c7289e59 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   7.9GB: boot/grub/core.img
   7.8GB: boot/grub/grub.cfg
   7.6GB: boot/initrd.img-2.6.32-21-generic
   7.8GB: boot/initrd.img-2.6.32-23-generic
   7.8GB: boot/vmlinuz-2.6.32-21-generic
   7.7GB: boot/vmlinuz-2.6.32-23-generic
   7.8GB: initrd.img
   7.6GB: initrd.img.old
   7.7GB: vmlinuz
   7.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ed 81 00 00 1c 45 00 00  29 44 bf 4b 8e 3f 3e 4c  |.....E..)D.K.?>L|
00000010  29 44 bf 4b 00 00 00 00  00 00 01 00 28 00 00 00  |)D.K........(...|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  05 00 00 00 4b 2a 02 00  |............K*..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 d8 cf 24 79  00 00 00 00 00 00 00 00  |......$y........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 50 c0 ac 45  00 00 00 00 00 00 00 00  |....P..E........|
00000090  8e 3f 3e 4c 08 5b e1 3e  00 00 00 00 00 00 00 00  |.?>L.[.>........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  ed 81 00 00 e4 34 00 00  29 44 bf 4b 8e 3f 3e 4c  |.....4..)D.K.?>L|
00000110  29 44 bf 4b 00 00 00 00  00 00 01 00 20 00 00 00  |)D.K........ ...|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  04 00 00 00 50 2a 02 00  |............P*..|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 d9 cf 24 79  00 00 00 00 00 00 00 00  |......$y........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 50 c0 ac 45  00 00 00 00 00 00 00 00  |....P..E........|
00000190  8e 3f 3e 4c 50 c0 ac 45  00 00 00 00 00 00 00 00  |.?>LP..E........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 5a 00 00 00  |............Z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by varunendra on 2010-07-29
I'm Sooooooo... happy for you :guitar:\\:D/:lolflag:=D>=D>=D>
Sometimes the most obvious is found in the last :lol:

Now you can reconnect all the drives and just change (or keep) the boot order in the BIOS such that your 160GB drive stays at the top of the order.

It was just that Lucid was installed in sdb (160GB) but the BIOS was set to boot off sda (20GB) which had a corrupt installation.


Dinner was really good!!!! :D

---

### Post by olamina on 2010-07-29
> It was just that Lucid was installed in sdb (160GB) but the BIOS was set  to boot off sda (20GB) which had a corrupt installation.

actually it was by setting the boot to the 20GB drive that i am back in business. don't ask me to explain because i can't. but it's working.\\:D/

---

### Post by varunendra on 2010-07-29
> **olamina said:**
> actually it was by setting the boot to the 20GB drive that i am back in business. don't ask me to explain because i can't. but it's working.\\:D/

Okay, so make it sdb which BIOS might be looking at earlier (I remember now that it was the only one without a boot-loader when you got "no boot sig" error) and had a corrupt installation!!

But in that case, you should have been able to boot successfully with both externals removed:confused: (maybe with a little interference with boot order). Besides, your goal to install in 160GB drive seems to have been unaccomplished then!!!!

If this is true these should happen:

[LIST=1]
[*]While only and only 20GB drive is connected, booting should be OK.
[*]While only and only 160GB drive is connected, booting should FAIL!!
[/LIST]
Nice that you are happy, I just wanted to tell what I feel. :)

---

