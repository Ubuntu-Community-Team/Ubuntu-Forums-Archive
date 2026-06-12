---
title: "GRUB ERROR: no such disk???"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by robine on 2010-03-08
Hi. I'm super annoyed, and getting desperate for some help! I can no longer use my system!! Here's what was going on about 1 hr ago:
[http://ubuntuforums.org/showpost.php?p=8933068&postcount=19](http://ubuntuforums.org/showpost.php?p=8933068&postcount=19)

  I was running 9.10 with few problems until one of my hard disks suddenly "disappeared". After following a few suggestions, I needed further help but couldn't find any. I decided to do a complete reinstall. (Btw, I previously had WinXP on this desktop. Don't know if that makes a difference.)

Everything seemed to go well. I rebooted when this was indicated. I saw "GRUB loading". But then...

"error: no such disk. grub rescue>"

How can there be no such disk when I just completely reinstalled 9.10?
Where did grub go?
What can I do??
I am a complete beginner at this and have never installed an OS. I really need help.

---

### Post by Maxcore on 2010-03-08
Do you have an external hard drive or any other drive connected that isn't recognized by GRUB? I know when I have my external hard drive plugged in to my computer GRUB gives me an error and doesn't let me boot up.

---

### Post by robine on 2010-03-08
I just took a look in the file browser. (I'm using the live CD right now to get help.) My 80gb HD has reappeared somehow. Not only that, all my files are still on it. I thought they would have been deleted and overwritten when I reinstalled Karmic.

Here is the result of "sudo fdisk -l":
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe919e919

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161   83  Linux

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xadece77e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+  83  Linux
/dev/sdb2            2433        4500    16611210    5  Extended
/dev/sdb5            2433        4500    16611178+  82  Linux swap / Solaris

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003d9f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       22956   184394038+   b  W95 FAT32
/dev/sdc2           22957       30515    60717667+   5  Extended
/dev/sdc5           22957       30201    58195431   83  Linux
/dev/sdc6           30202       30515     2522173+  82  Linux swap / Solaris
```The 251GB HD is my external drive (currently switched on & plugged in to desktop).

Here is the result of boot info script text file:
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=e7d977fb-8723-4ca3-9c4c-6a91c806b0cb)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
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

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe919e919

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xadece77e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    39,070,079    39,070,017  83 Linux
/dev/sdb2          39,070,080    72,292,499    33,222,420   5 Extended
/dev/sdb5          39,070,143    72,292,499    33,222,357  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003d9f6

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   368,788,139   368,788,077   b W95 FAT32
/dev/sdd2         368,788,140   490,223,474   121,435,335   5 Extended
/dev/sdd5         368,788,203   485,179,064   116,390,862  83 Linux
/dev/sdd6         485,179,128   490,223,474     5,044,347  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a31097ec-c78d-47b0-9cf0-2cfcd5aff759   ext3                                     
/dev/sdb1        bea739ac-dc3a-4af4-ba1b-9430e11d5158   ext3                                     
/dev/sdb5        760878d8-6c0f-4841-9b96-3c80672605e1   swap                                     
/dev/sdd1        71AB-1F06                              vfat       EXTERNAL HD                   
/dev/sdd5        e7d977fb-8723-4ca3-9c4c-6a91c806b0cb   ext4                                     
/dev/sdd6        5e3d6dad-0462-4626-8ca2-cb3fb863381b   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/a31097ec-c78d-47b0-9cf0-2cfcd5aff759 ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdd5        /media/e7d977fb-8723-4ca3-9c4c-6a91c806b0cb ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdd1        /media/EXTERNAL HD       vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1        /media/bea739ac-dc3a-4af4-ba1b-9430e11d5158 ext3       (rw,nosuid,nodev,uhelper=devkit)


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
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
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
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=a31097ec-c78d-47b0-9cf0-2cfcd5aff759 /home           ext3    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=760878d8-6c0f-4841-9b96-3c80672605e1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .5GB: boot/grub/core.img
    .5GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-16-generic-pae
    .6GB: boot/vmlinuz-2.6.31-16-generic-pae
    .5GB: initrd.img
    .6GB: vmlinuz

=========================== sdd5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd2,5)
search --no-floppy --fs-uuid --set e7d977fb-8723-4ca3-9c4c-6a91c806b0cb
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
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set e7d977fb-8723-4ca3-9c4c-6a91c806b0cb
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=e7d977fb-8723-4ca3-9c4c-6a91c806b0cb ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set e7d977fb-8723-4ca3-9c4c-6a91c806b0cb
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=e7d977fb-8723-4ca3-9c4c-6a91c806b0cb ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
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
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
    linux /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 ro quiet splash
    initrd /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
    linux /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 ro single
    initrd /boot/initrd.img-2.6.31-16-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=e7d977fb-8723-4ca3-9c4c-6a91c806b0cb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=5e3d6dad-0462-4626-8ca2-cb3fb863381b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd5: Location of files loaded by Grub: ===================


 191.1GB: boot/grub/core.img
 191.1GB: boot/grub/grub.cfg
 189.3GB: boot/initrd.img-2.6.31-20-generic-pae
 189.3GB: boot/vmlinuz-2.6.31-20-generic-pae
 189.3GB: initrd.img
 189.3GB: vmlinuz
```It looks like (and someone please correct me if I'm wrong) 9.10 was installed and created NEW partitions, while leaving all the previous partitions (and the previous 9.10 installation) intact! Can someone confirm this? Why would this happen? And how can I just wipe everything and start completely new (which is what I THOUGHT I was doing) with Karmic, and nothing else on the desktop??

---

### Post by robine on 2010-03-08
> **Maxcore said:**
> Do you have an external hard drive or any other drive connected that isn't recognized by GRUB? I know when I have my external hard drive plugged in to my computer GRUB gives me an error and doesn't let me boot up.

Hey, just saw your response after I posted again. Yes, I do have an external hard disk. I just posted all the info - it's the 251GB one. It looks like Karmic installed itself there instead of on the 80GB drive like I (thought I) told it to.

I'm so confused.

---

### Post by robine on 2010-03-08
Hey all, I would really appreciate some input on this. I need to solve this issue and understand what I've done wrong.

The only information I've been able to find on Google has been regarding dual installs (of Ubuntu & Windows), which don't apply to my situation.

---

### Post by natravis on 2010-03-08
easy solution: unplug external HDD, boot up normally, plug in HDD and wipe it (presuming there are no files you want to save), run ```
sudo update-grub
```

---

### Post by robine on 2010-03-08
> **natravis said:**
> easy solution: unplug external HDD, boot up normally, plug in HDD and wipe it (presuming there are no files you want to save), run ```
sudo update-grub
```

Hi, thanks for your reply. Actually, I don't want to run Ubuntu from my external hard drive; I use that just for backing up files and storing music. What I want is to wipe the 2 hard drives on the desktop and only have Ubuntu - nothing else.

---

### Post by natravis on 2010-03-08
Right now it looks like you have it installed on your external. That should be wiped at some point or at least the partitions should be changed so that you have only data on there.

For the other stuff, I would go through the normal install process, just just manual partitioning and select the appropriate drive and setup your partitions that way. Alternatively, you can unplug the USB drive from the system then install it, to ensure that you dont put anything on the external.

Just make sure you are looking at the correct drives when installing (use the sizes to guide you) and its usually nice to setup a /home partition, / partition, and swap on your main drive, then you can use the other internal drive for storage or whatever, perhaps mount it as /data. Make sure you format the internal drives (making sure you backed anything up off of them first) especially if you had Ubuntu installed previously, to ensure nothing is retained.

---

