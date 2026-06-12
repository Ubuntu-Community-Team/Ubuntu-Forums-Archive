---
title: "Deleting partitions"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by weichimaster on 2010-01-20
Hi

I was drunk when I installed Ubuntu. As a result, my hard disk partitions are messy. (I scratched the live CD and tried to install of the duff CD twice).

I have dual boot Karmic 9.10 and Windows XP, on a Dell. Grub 2 is my boot loader.

Here is the results of sudo fdisk -l:

```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        9265    74364885    7  HPFS/NTFS
/dev/sda3            9266       29787   164842965    f  W95 Ext'd (LBA)
/dev/sda4           29788       30393     4867695   db  CP/M / CTOS / ...
/dev/sda5           28922       29787     6956145    7  HPFS/NTFS
/dev/sda6           11009       13275    18209646   83  Linux
/dev/sda7           28483       28921     3526236   82  Linux swap / Solaris
/dev/sda8            9266       10825    12530637   83  Linux
/dev/sda9           10826       11008     1469916   82  Linux swap / Solaris
/dev/sda10          13276       28291   120615988+  83  Linux
/dev/sda11          28292       28465     1397623+  82  Linux swap / Solaris

Partition table entries are not in disk order

```sda1 is some random dell stuff. Sda 2 is windows. Sda 4 is dell restore - it's not part of the extended partition.

Sda 3  is the extended partition. Within this, sda 5 is a windows back up drive. Sda 6, 7, 8,9 and the bodged installations. Sda 10 and 11 are what I'm actually using.

I reckon to fix this the steps are:

1) Be sober!
2) Back everything up
3) Boot from live disk
4) Go into gparted
5) Delete sda 6,7,8,9 (and maybe some of the unwanted Dell partitions) and shuffle around the resulting free space.
6) Check if the partition numbers have changed.
7) run sudo update-grub
8. check /boot/grub/grub.cfg is still pointing at the right place (particularly if I've changed partition numbers)
9) Reboot (not from disk), and cross fingers!

Is this likely to work? One bit that worries me is that presumably the Bios is told to look for Grub 2, which is currently in sda10. If this gets renamed, I may not get to the initial Grub 2 menu.

(Moral of the story: Some things are better done sober.)

---

### Post by JamesParnell on 2010-01-20
I would think that would work...but I'm a newb, so...yeah.

---

### Post by kansasnoob on 2010-01-20
> **weichimaster said:**
> Hi

I was drunk when I installed Ubuntu. As a result, my hard disk partitions are messy. (I scratched the live CD and tried to install of the duff CD twice).

I have dual boot Karmic 9.10 and Windows XP, on a Dell. Grub 2 is my boot loader.

Here is the results of sudo fdisk -l:

```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        9265    74364885    7  HPFS/NTFS
/dev/sda3            9266       29787   164842965    f  W95 Ext'd (LBA)
/dev/sda4           29788       30393     4867695   db  CP/M / CTOS / ...
/dev/sda5           28922       29787     6956145    7  HPFS/NTFS
/dev/sda6           11009       13275    18209646   83  Linux
/dev/sda7           28483       28921     3526236   82  Linux swap / Solaris
/dev/sda8            9266       10825    12530637   83  Linux
/dev/sda9           10826       11008     1469916   82  Linux swap / Solaris
/dev/sda10          13276       28291   120615988+  83  Linux
/dev/sda11          28292       28465     1397623+  82  Linux swap / Solaris

Partition table entries are not in disk order

```sda1 is some random dell stuff. Sda 2 is windows. Sda 4 is dell restore - it's not part of the extended partition.

Sda 3  is the extended partition. Within this, sda 5 is a windows back up drive. Sda 6, 7, 8,9 and the bodged installations. Sda 10 and 11 are what I'm actually using.

I reckon to fix this the steps are:

1) Be sober!
2) Back everything up
3) Boot from live disk
4) Go into gparted
5) Delete sda 6,7,8,9 (and maybe some of the unwanted Dell partitions) and shuffle around the resulting free space.
6) Check if the partition numbers have changed.
7) run sudo update-grub
8. check /boot/grub/grub.cfg is still pointing at the right place (particularly if I've changed partition numbers)
9) Reboot (not from disk), and cross fingers!

Is this likely to work? One bit that worries me is that presumably the Bios is told to look for Grub 2, which is currently in sda10. If this gets renamed, I may not get to the initial Grub 2 menu.

(Moral of the story: Some things are better done sober.)

What doesn't work right?

How about a screenshot of Gparted?

And maybe the output of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Maybe things aren't as bad as you think ;)

---

### Post by weichimaster on 2010-01-20
> **kansasnoob said:**
> What doesn't work right?

How about a screenshot of Gparted?

And maybe the output of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Maybe things aren't as bad as you think ;)

It works perfectly! I'm a big Ubuntu fan. My i-phone is the only thing meaning I'm keeping Windows.

However, it's messy having 4 partitions I don't use - I was thinking of mounting /home to its own partition and thought I'd tidy up beforehand.

Here's the boot script info:
```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #10 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,455   148,842,224   148,729,770   7 HPFS/NTFS
/dev/sda3         148,842,225   478,528,154   329,685,930   f W95 Ext d (LBA)
/dev/sda5         464,615,865   478,528,154    13,912,290   7 HPFS/NTFS
/dev/sda6         176,843,583   213,262,874    36,419,292  83 Linux
/dev/sda7         457,563,393   464,615,864     7,052,472  82 Linux swap / Solaris
/dev/sda8         148,842,351   173,903,624    25,061,274  83 Linux
/dev/sda9         173,903,688   176,843,519     2,939,832  82 Linux swap / Solaris
/dev/sda10        213,262,938   454,494,914   241,231,977  83 Linux
/dev/sda11        454,494,978   457,290,224     2,795,247  82 Linux swap / Solaris
/dev/sda4         478,528,155   488,263,544     9,735,390  db CP/M / CTOS / ...


blkid -c /dev/null: ____________________________________________________________

/dev/sda10: UUID="7b1ec656-75cd-4167-b6fb-da49d6ba2ce6" TYPE="ext4" 
/dev/sda11: UUID="0b6d25a7-5fbe-46ff-9bf9-978a09c6d891" TYPE="swap" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0A11" TYPE="vfat" 
/dev/sda2: UUID="8A54A73B54A72941" TYPE="ntfs" 
/dev/sda4: LABEL="DellRestore" TYPE="vfat" 
/dev/sda5: UUID="0CA0FD1BA0FD0C48" LABEL="Backup" TYPE="ntfs" 
/dev/sda6: UUID="34403796-6754-465a-9521-a559cfb78362" TYPE="ext4" 
/dev/sda7: UUID="2a38bb78-d163-4de8-aa2a-b52d2766d0f8" TYPE="swap" 
/dev/sda8: UUID="929a8e3f-bef1-4c68-92e0-a6bd39571759" TYPE="ext4" 
/dev/sda9: UUID="90091252-b41c-4145-bf0e-3dd4bfa98635" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda10 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=34403796-6754-465a-9521-a559cfb78362 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2a38bb78-d163-4de8-aa2a-b52d2766d0f8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  90.5GB: boot/initrd.img-2.6.31-14-generic
  90.5GB: boot/vmlinuz-2.6.31-14-generic
  90.5GB: initrd.img
  90.5GB: vmlinuz

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=929a8e3f-bef1-4c68-92e0-a6bd39571759 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=90091252-b41c-4145-bf0e-3dd4bfa98635 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

========================== sda10/boot/grub/grub.cfg: ==========================

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
set root=(hd0,10)
search --no-floppy --fs-uuid --set 7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 ro single 
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
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 07d6-0a11
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 8a54a73b54a72941
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda4)" {
    insmod fat
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 0000-0000
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 9.10 (9.10) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 34403796-6754-465a-9521-a559cfb78362
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda6
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=0b6d25a7-5fbe-46ff-9bf9-978a09c6d891 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda10: Location of files loaded by Grub: ===================


 109.1GB: boot/grub/core.img
 109.1GB: boot/grub/grub.cfg
 109.1GB: boot/initrd.img-2.6.31-14-generic
 109.1GB: boot/initrd.img-2.6.31-17-generic
 109.1GB: boot/vmlinuz-2.6.31-14-generic
 109.1GB: boot/vmlinuz-2.6.31-17-generic
 109.1GB: initrd.img
 109.1GB: initrd.img.old
 109.1GB: vmlinuz
 109.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```[IMG]file:///tmp/moz-screenshot.png[/IMG]And here's gparted:

[ATTACH]144306[/ATTACH]

---

### Post by weichimaster on 2010-01-23
Hi

I went ahead with my plan, and as expected my gparted changed the name of my partitions while installing. My main directory is now sda6, and swap is sda7.

The deletion went OK until I tried to mount the drives. I was following the instructions here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I got an error when trying to mount any drives. I ended up quitting the live cd session, and re-booting. As expected, log in failed.

I then logged in via the rescue mode instructions on the same link. These worked excellently - I highly recommend this link.

I've run "sudo update-grub". (I did some othe commands as well, and I've accidentally installed Grub1 as well.)

However, the results of the boot script info are:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #10 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,455   148,842,224   148,729,770   7 HPFS/NTFS
/dev/sda3         148,842,225   478,528,154   329,685,930   f W95 Ext d (LBA)
/dev/sda5         464,615,865   478,528,154    13,912,290   7 HPFS/NTFS
/dev/sda6         148,842,351   461,820,554   312,978,204  83 Linux
/dev/sda7         461,820,618   464,615,864     2,795,247  82 Linux swap / Solaris
/dev/sda4         478,528,155   488,263,544     9,735,390  db CP/M / CTOS / ...


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0A11" TYPE="vfat" 
/dev/sda2: UUID="8A54A73B54A72941" TYPE="ntfs" 
/dev/sda4: LABEL="DellRestore" TYPE="vfat" 
/dev/sda5: UUID="0CA0FD1BA0FD0C48" LABEL="Backup" TYPE="ntfs" 
/dev/sda6: UUID="7b1ec656-75cd-4167-b6fb-da49d6ba2ce6" TYPE="ext4" 
/dev/sda7: UUID="0b6d25a7-5fbe-46ff-9bf9-978a09c6d891" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 7b1ec656-75cd-4167-b6fb-da49d6ba2ce6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 ro single 
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
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=7b1ec656-75cd-4167-b6fb-da49d6ba2ce6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=0b6d25a7-5fbe-46ff-9bf9-978a09c6d891 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  76.2GB: boot/grub/core.img
  76.2GB: boot/grub/grub.cfg
  76.2GB: boot/grub/menu.lst
  76.2GB: boot/initrd.img-2.6.31-14-generic
  76.2GB: boot/initrd.img-2.6.31-17-generic
  76.2GB: boot/vmlinuz-2.6.31-14-generic
  76.2GB: boot/vmlinuz-2.6.31-17-generic
  76.2GB: initrd.img
  76.2GB: initrd.img.old
  76.2GB: vmlinuz
  76.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

The first line of this says that MBR is looking for Grub 2 in sda10, which no longer exists!

So my questions are:
1) How do I correct this?
2) How do unistall grub1?

---

### Post by weichimaster on 2010-01-23
I've logged of and back on.

It's still the same error - I think that the MBR is looking for GRUB in sda10, which doesn't exist. 

I end up at a grub resuce prompt. I can log on from here, but it's very time consuming and I've lost the Windoze option.

Would logging on from a live cd and running ```
grub-setup -d /media/(cd location)/boot/grub /dev/sda
``` help?

---

### Post by weichimaster on 2010-01-23
I've solved it!

I reinstalled Grub2 and got rid of Grub1 by typing

```
$ sudo apt-get install grub2
$ sudo upgrade-from-grub-legacy
$ sudo grub-install
```

And everything now works!

The link [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) is really incredibly good.

---

