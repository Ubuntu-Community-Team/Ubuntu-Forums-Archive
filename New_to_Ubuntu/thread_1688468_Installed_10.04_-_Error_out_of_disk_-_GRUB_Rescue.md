---
title: "Installed 10.04 - Error: out of disk - GRUB Rescue"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by wep940 on 2011-02-15
I hope someone can help me out here.  A quick background:
 
I have an older laptop, P4 2.4ghz, 1GB memory, 160gb hard drive.  I installed Windows XP Pro first, then decided to dual boot, so I installed 10.04, choosing manual partitioning as I always have.   Shrunk Windows down to 130gb, created a 8gb (I forgot how much memory I have so I went WAY overboard) swap file and the 32gb remaining I made ext4 and mount point "/".
 
After installation, I went to do the reboot.  It comes up real quick to a screen that just says:
 
Error: Out of disk space
Grub Rescue:
 
I'd *really* like to get past this without losing my partitions, as I have a ton of hours into installing Windows, doing the update to SP3, all the updates since, plus all the drivers, etc..  So, I'd like to know what the error means, and of course I'd like to know how to get around the problem.
 
Thanks in advance!

---

### Post by wep940 on 2011-02-15
BTW, I've already checked one of the howto's for grub2.  It lets me set root, but doesn't recognize "linux" so it doesn't let me set the root device.  Tyring the initrd command results in unknown command as well.
 
Trying to ls any folder on the boot device results in the "out of disk" error.
 
From what I understand, this error normally is saying it can't find the grub.cfg file - hence the commands to try to set the path to root, define the boot device and finally try to initialize the image.
 
I'm really lost here.

---

### Post by Rubi1200 on 2011-02-15
The best thing to do right now is the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by wep940 on 2011-02-15
Sorry it took a while - with the LiveCD my wireless shows available networks, but wouldn't connect to my hidden network when I set it up. So, had to download, put on USB flash, run on Ubuntu, paste the results and come back here. One thing I did notice: the HowTo I was following said to use "XY" in the sdXY statement where X was the drive (0) and Y was the partition (6), but I think it really should be something like sda6. At any rate, not knowing anything, here's the results:
 
```
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
sda2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda6: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdb1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 32.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63   249,371,156   249,371,094   7 HPFS/NTFS
/dev/sda2         249,372,670   312,580,095    63,207,426   5 Extended
/dev/sda5         249,372,672   265,191,423    15,818,752  82 Linux swap / Solaris
/dev/sda6         265,193,472   312,580,095    47,386,624  83 Linux
 
Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 519 MB, 519569408 bytes
129 heads, 32 sectors/track, 245 cylinders, total 1014784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdb1                  32     1,014,783     1,014,752   6 FAT16
 
blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/sda1        2CA8B442A8B40BF8                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3aa9cdd7-0524-41c5-89e3-d257938b7edb   swap                                     
/dev/sda6        5e443ee5-bb97-424c-899b-e698127843ad   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2A29-EDE7                              vfat                                     
/dev/sdb: PTTYPE="dos" 
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/2A29-EDE7         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda6        /media/5e443ee5-bb97-424c-899b-e698127843ad ext4       (rw,nosuid,nodev,uhelper=udisks)
 
================================ sda1/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=========================== sda6/boot/grub/grub.cfg: ===========================
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5e443ee5-bb97-424c-899b-e698127843ad
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 5e443ee5-bb97-424c-899b-e698127843ad
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
 set root='(hd0,6)'
 search --no-floppy --fs-uuid --set 5e443ee5-bb97-424c-899b-e698127843ad
 linux /boot/vmlinuz-2.6.32-24-generic root=UUID=5e443ee5-bb97-424c-899b-e698127843ad ro   quiet splash
 initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,6)'
 search --no-floppy --fs-uuid --set 5e443ee5-bb97-424c-899b-e698127843ad
 echo 'Loading Linux 2.6.32-24-generic ...'
 linux /boot/vmlinuz-2.6.32-24-generic root=UUID=5e443ee5-bb97-424c-899b-e698127843ad ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod ext2
 set root='(hd0,6)'
 search --no-floppy --fs-uuid --set 5e443ee5-bb97-424c-899b-e698127843ad
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod ext2
 set root='(hd0,6)'
 search --no-floppy --fs-uuid --set 5e443ee5-bb97-424c-899b-e698127843ad
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
 insmod ntfs
 set root='(hd0,1)'
 search --no-floppy --fs-uuid --set 2ca8b442a8b40bf8
 drivemap -s (hd0) ${root}
 chainloader +1
}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5e443ee5-bb97-424c-899b-e698127843ad /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda1 during installation
UUID=2CA8B442A8B40BF8 /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=3aa9cdd7-0524-41c5-89e3-d257938b7edb none            swap    sw              0       0
=================== sda6: Location of files loaded by Grub: ===================
 
 138.1GB: boot/grub/core.img
 142.4GB: boot/grub/grub.cfg
 138.1GB: boot/initrd.img-2.6.32-24-generic
 138.1GB: boot/vmlinuz-2.6.32-24-generic
 138.1GB: initrd.img
 138.1GB: vmlinuz

```
 
 
Obviously sda5 is my swap, sda6 is my ext4 partition for all of linux, sda1 is my Windows installation. I'm curious - why does the boot loader info for sda1 show as ntldr -> I thought it would be grub, or does grub come in somehow ahead of this and then direct the boot process to the loader informaion?
 
Thanks again!
 
EDIT: Can't I just boot off the LiveCD and run grub-update (or maybe it's update-grub?) and somehow also be sure the mbr is getting updated correctly?  Also, not understanding any of this, why does it say the Windows mbr is on sdb when I don't have an 2nd drive and why does it also show as some type of start sector location error?

---

### Post by wep940 on 2011-02-15
Hummmmm, I saw something else in reference to the out of disk error - apparently if your partition/data is above 137gb some BIOS's won't access it. I did install an IDE Samsung 160gb drive. The BIOS sees the drive, Windows sees the drive and before I repartitioned for Linux it did show the full 160gb. However, I had noticed that the disk I/O has seemed slow. I checked the BIOS and the info for the drive said it didn't have 32-bit transfers enabled, so I changed it to enabled - I did this after running into this grub rescue problem. Is there a way I can check to see if my BIOS actually supports the drive beyond 137gb?
 
EDIT:  Bingo!!  I checked in the BIOS again and it says maximum supported size is 137gb.  So, even though the installation went through, it might explain why, at the grub rescue prompt, I can set to (hd0,6) but when I try to ls any files in that path nothing shows but the folders in "/".  So, I'm guessing now that the data is actually beyond the 137gb limit.  Also makes me wonder if the installation, though it claimed it was successful, somehow wiped out any of my Windows partition since the addressing was restricted.  I'm going to check on a BIOS update, but I don't think there is one newer.  I'd sure hate to set aside 23gb at the end of the drive as not useable.

---

### Post by wep940 on 2011-02-15
Okay, I re-installed Ubuntu for dual boot, shrinking the Windows partition even more, deleting the existing Ubuntu partitions, allocating a 30gb partition at the end to take up the space I can't address, then added in swap and ext4 for ubuntu and let it install.  I can boot Windows and Ubuntu fine now.
 
I have also found what to me at least is another problem - in the BIOS setup for the drive it says the transfer mode is DMA2 - in other words, the source of things being SLOW.  I can't get to that field in the BIOS setup - it skips over it.  So, I have an oversized disk - does the BIOS detect that it's too big and automatically lower the transfer mode?

---

### Post by wep940 on 2011-02-15
I guess I'll mark this solved and try to find an answer to my hardware question.

---

