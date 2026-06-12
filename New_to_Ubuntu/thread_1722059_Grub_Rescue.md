---
title: "Grub Rescue"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by wsl on 2011-04-05
Hi,
 
I got "Grub Rescue>" and cannot start PC. How should I do? 
W/ WinXP & Lubuntu 10.04 (Grub 2)
 
RESULTS.txt is 
 
 
[PHP] Boot Info Script 0.55    dated February 15th, 2010                    
 
============================= Boot Info Summary: ==============================
 
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 
sda1: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /menu.lst /boot.ini /grldr /ntldr /NTDETECT.COM
 
sda2: _________________________________________________________________________
 
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
 
sda5: _________________________________________________________________________
 
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
 
sda6: _________________________________________________________________________
 
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
 
sda7: _________________________________________________________________________
 
    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda7 starts at sector 48243321.
    Operating System:  
    Boot files/dirs:   
 
sdb1: _________________________________________________________________________
 
    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
=========================== Drive/Partition Info: =============================
 
Drive: sda ___________________ _____________________________________________________
 
Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sda1    *             63    48,243,194    48,243,132   7 HPFS/NTFS
/dev/sda2          48,243,256    80,292,869    32,049,614   f W95 Ext d (LBA)
/dev/sda5          59,665,473    79,120,124    19,454,652  83 Linux
/dev/sda6          79,120,188    80,292,869     1,172,682  82 Linux swap / Solaris
/dev/sda7          48,243,321    59,665,409    11,422,089   c W95 FAT32 (LBA)
 
 
Drive: sdb ___________________ _____________________________________________________
 
Disk /dev/sdb: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sdb1    *             80    15,663,103    15,663,024   c W95 FAT32 (LBA)
 
 
blkid -c /dev/null: ____________________________________________________________
 
Device           UUID                                   TYPE       LABEL                         
 
/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        8E8830AE883096A5                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1d6a7ccd-7a14-4663-b2d2-29ee41aea773   ext3                                     
/dev/sda6        25e0caaa-f554-4ec5-862e-88394ec03296   swap                                     
/dev/sda7        D34C-69AF                              vfat       FAT                           
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3689-1487                              vfat       LEXAR2                        
/dev/sdb: PTTYPE="dos" 
 
============================ "mount | grep ^/dev  output: ===========================
 
Device           Mount_Point              Type       Options
 
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/LEXAR2            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
 
 
================================ sda1/menu.lst: ================================
 
title Install Ubuntu
 
root (hd0,0)
 
kernel /vmlinuz
 
initrd /initrd.lz
================================ sda1/boot.ini: ================================
 
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
c:\grldr="Start GRUB"
=================== sda1: Location of files loaded by Grub: ===================
 
 
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 1d6a7ccd-7a14-4663-b2d2-29ee41aea773
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
search --no-floppy --fs-uuid --set 1d6a7ccd-7a14-4663-b2d2-29ee41aea773
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
menuentry 'LUbuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 1d6a7ccd-7a14-4663-b2d2-29ee41aea773
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1d6a7ccd-7a14-4663-b2d2-29ee41aea773 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'LUbuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 1d6a7ccd-7a14-4663-b2d2-29ee41aea773
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1d6a7ccd-7a14-4663-b2d2-29ee41aea773 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 1d6a7ccd-7a14-4663-b2d2-29ee41aea773
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 1d6a7ccd-7a14-4663-b2d2-29ee41aea773
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8e8830ae883096a5
    drivemap -s (hd0) ${root}
    chainloader +1
}
#menuentry "Ubuntu, kernel 2.6.15-26-386 (on /dev/sda6)" {
#    insmod ext2
#    set root='(hd0,6)'
#    search --no-floppy --fs-uuid --set dfe2c83f-3da1-490d-b5e9-9edaab3620e4
#    linux /boot/vmlinuz-2.6.15-26-386 root=/dev/hda8 ro quiet splash
#    initrd /boot/initrd.img-2.6.15-26-386
#}
#menuentry "Ubuntu, kernel 2.6.15-26-386 (recovery mode) (on /dev/sda6)" {
#    insmod ext2
#    set root='(hd0,6)'
#    search --no-floppy --fs-uuid --set dfe2c83f-3da1-490d-b5e9-9edaab3620e4
#    linux /boot/vmlinuz-2.6.15-26-386 root=/dev/hda8 ro single
#    initrd /boot/initrd.img-2.6.15-26-386
#}
#menuentry "Ubuntu, memtest86+ (on /dev/sda6)" {
#    insmod ext2
#    set root='(hd0,6)'
#    search --no-floppy --fs-uuid --set dfe2c83f-3da1-490d-b5e9-9edaab3620e4
#    linux /boot/memtest86+.bin 
#}
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
/dev/sda7       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=25e0caaa-f554-4ec5-862e-88394ec03296 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
 
=================== sda5: Location of files loaded by Grub: ===================
 
 
  36.6GB: boot/grub/core.img
  36.6GB: boot/grub/grub.cfg
  36.6GB: boot/initrd.img-2.6.32-21-generic
  36.7GB: boot/vmlinuz-2.6.32-21-generic
  36.6GB: initrd.img
  36.7GB: vmlinuz
[/PHP]
 
 
 
By the way, I added "#" in Grub.cfg.
E.g.
 
[PHP]#menuentry "Ubuntu, kernel 2.6.15-26-386 (on /dev/sda6)" {
#    insmod ext2
#    set root='(hd0,6)'
#    search --no-floppy --fs-uuid --set dfe2c83f-3da1-490d-b5e9-9edaab3620e4
#    linux /boot/vmlinuz-2.6.15-26-386 root=/dev/hda8 ro quiet splash
#    initrd /boot/initrd.img-2.6.15-26-386
#}[/PHP]

---

### Post by wsl on 2011-04-05
Hi,
 
In grub rescue>
 
[PHP]
grub rescue> set
prefix=(hd0,7)/boot/grub
root=hd0,7
grub rescue> ls /boot
error: unknown filesystem.
grub rescue>unset prefix
grub rescue>unset root
grub rescue>set prefix=(hd0,5)/boot/grub
grub rescue>set root=(hd0,5)
grub rescue>ls /boot
./  ../  grub/ System.map-2.6.32-21-generic abi-2.6.32-21-generic config-2.6.32-21-generic 
...
[/PHP]
but no *.mod
 
[PHP]
grub rescue>insmod /boot/grub/linux.mod
grub rescue>linux /vmlinux root=/dev/sd50 ro
grub rescue>initrd /initrd.img
grub rescue>boot
.
.
.
[/PHP]
 
[PHP]
[   2.729552] Console: switching to colour frame buffer device 80x30
ALERT! /dev/sd50 does not exit. Dropping to a shell!
 
BusyBox v1.13.3 (Ubuntu ...) built-in shell (ash) 
Enter 'help' for a list of built-in commands.
 
(initramfs)
[/PHP]
 
 
Seemingly, the problem was due to the change of hda7 to hda5. When I installed Lubuntu 10.04, that partition was hda7. After installed, I formated and worked some partitions and after restart, Lubuntu auto pointed this partition from hda7 to hda5  but Grub didn't know it. I don't know exactly. Can someone help me. It will be appreciated!

---

### Post by andrewthomas on 2011-04-05
Looks like you have been busy deleting partitions and editing your grub.cfg file.  You need to purge grub2 and reinstall from a live cd

You need the doctor's help.

**HOWTO: Purge and Reinstall Grub 2 from the Live CD**
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by wilee-nilee on 2011-04-05
sda1: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   **/menu.lst** /boot.ini /grldr /ntldr /NTDETECT.COM

The highlighted portion here is also part of grub-legacy, can probably be removed manually.

---

### Post by psusi on 2011-04-05
> **wsl said:**
> 
[PHP]
grub rescue>set prefix=(hd0,5)/boot/grub
grub rescue>set root=(hd0,5)
[/PHP]

At this point, type the command "normal" to exit rescue mode and you should get your normal boot menu and be able to boot.  Then you will need to reinstall grub:

```
sudo grub-install /dev/sda
```

> **wsl said:**
> 
but no *.mod

That is because they live in /boot/grub/ not /boot/.

---

### Post by wsl on 2011-04-05
> **wilee-nilee said:**
> sda1: _________________________________________________________________________
 
File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: **/menu.lst** /boot.ini /grldr /ntldr /NTDETECT.COM
 
The highlighted portion here is also part of grub-legacy, can probably be removed manually.
 
 
Thank you. You really read carefully and found this point. Actually, I don't think this would be an issue because menu.lst is for Grub1 but Lubuntu 10.04 is using Grub 2 which will not read menu.lst. 
 
To AndrewThomos:
 
Thank you very much, too. I think I better reinstall again because I afraid even I solve the Grub2 issue, Lubuntu still can not run well because of fdisk issues.

---

### Post by wsl on 2011-04-05
> **psusi said:**
> At this point, type the command "normal" to exit rescue mode and you should get your normal boot menu and be able to boot. Then you will need to reinstall grub:
 
```
sudo grub-install /dev/sda
```
 
 
 
That is because they live in /boot/grub/ not /boot/.
 
 
Thank you so much. Indeed, I tried "normal" one time but not 2nd and 3rd times. Yet, sorry, I have started to re-install it. Anyway, I would like to post the link of grub rescue> commands for Grub2:
 
[https://help.ubuntu.com/community/Grub2#Command](https://help.ubuntu.com/community/Grub2#Command) 
 
for anyone would have the similar problem.

---

