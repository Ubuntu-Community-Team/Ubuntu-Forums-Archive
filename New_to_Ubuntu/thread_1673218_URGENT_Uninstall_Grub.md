---
title: "URGENT: Uninstall Grub"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by thunderstruck1 on 2011-01-22
Hi guys, I have the following problem: my hdd had two partitions - one for Windows7 and one for recovery. I decided to try Ubuntu so I shrinked the win7 partition, created a new one and installed ubuntu on it. After the installation i couldn't get windows7 run again and I also couldn't deal with ubuntu so I formatted the newly created partition alongside the one with the recovery. :oops: Now when I turn on the computer I get the following message:
 
Error: unknown filesystem
grub rescue
 
I read alot about this problem over the past 10 hours but the problem is that I don't have any windows7 dvd to remove grub. It was preinstalled when I bought my laptop.
 
Is there any way out of this situation? :( Please help as soon as you can, because I'm a student in the middle of exams and I need my laptop. THANK YOU!!!

---

### Post by Rubi1200 on 2011-01-22
Hi and welcome to the forums :)

You need to boot the computer with either a LiveCD or LiveUSB, then do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Once we see the results, we can advise you further.

---

### Post by thunderstruck1 on 2011-01-22
Firts of all, thanks for the quick response! Second, I reinstalled Ubuntu so I can recover my files if anything goes wrong. Now here's the output:
 
>                 Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________
    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe
sda4: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda6: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdc1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2               2,048       409,599       407,552  42 SFS
/dev/sda3    *        409,600   533,604,351   533,194,752  42 SFS
/dev/sda4         533,606,398   625,141,759    91,535,362   5 Extended
/dev/sda5         533,606,400   621,301,759    87,695,360  83 Linux
/dev/sda6         621,303,808   625,141,759     3,837,952  82 Linux swap / Solaris

Drive: sdc ___________________ _____________________________________________________
Disk /dev/sdc: 4127 MB, 4127195136 bytes
255 heads, 63 sectors/track, 501 cylinders, total 8060928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdc1    *            128     8,060,927     8,060,800   6 FAT16

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/sda2        D83055903055770A                       ntfs       SYSTEM                        
/dev/sda3        68B0AEDBB0AEAF4E                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        7d758b35-cd3c-4ce8-b5a6-0e81632e3920   ext4                                     
/dev/sda6        dd67a20e-e0d2-4391-9147-b0bb59993e67   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        166C-367B                              vfat                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/166C-367B         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

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
search --no-floppy --fs-uuid --set 7d758b35-cd3c-4ce8-b5a6-0e81632e3920
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
search --no-floppy --fs-uuid --set 7d758b35-cd3c-4ce8-b5a6-0e81632e3920
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
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 7d758b35-cd3c-4ce8-b5a6-0e81632e3920
 linux /boot/vmlinuz-2.6.32-21-generic root=UUID=7d758b35-cd3c-4ce8-b5a6-0e81632e3920 ro   quiet splash
 initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 7d758b35-cd3c-4ce8-b5a6-0e81632e3920
 echo 'Loading Linux 2.6.32-21-generic ...'
 linux /boot/vmlinuz-2.6.32-21-generic root=UUID=7d758b35-cd3c-4ce8-b5a6-0e81632e3920 ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 7d758b35-cd3c-4ce8-b5a6-0e81632e3920
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod ext2
 set root='(hd0,5)'
 search --no-floppy --fs-uuid --set 7d758b35-cd3c-4ce8-b5a6-0e81632e3920
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
 insmod ntfs
 set root='(hd0,2)'
 search --no-floppy --fs-uuid --set d83055903055770a
 chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
 insmod ntfs
 set root='(hd0,3)'
 search --no-floppy --fs-uuid --set 68b0aedbb0aeaf4e
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
UUID=7d758b35-cd3c-4ce8-b5a6-0e81632e3920 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=dd67a20e-e0d2-4391-9147-b0bb59993e67 none            swap    sw              0       0
=================== sda5: Location of files loaded by Grub: ===================

 297.0GB: boot/grub/core.img
 286.3GB: boot/grub/grub.cfg
 297.1GB: boot/initrd.img-2.6.32-21-generic
 297.1GB: boot/vmlinuz-2.6.32-21-generic
 297.1GB: initrd.img
 297.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============
sdb 


---

### Post by bryanl on 2011-01-22
It looks like the boot information script is getting quite popular! Its output may help some folks suggest specific things you can do.

On a more generic level, from your description, there are a couple of things to note. 

First is that you have code at the very bottom of your disk in an area called the master boot record (MBR) that starts the boot process. This code finds the extra code needed to boot whatever system(s) you have. You don't 'uninstall' the GRUB2 bootloader here, you have to _replace_ it.

GRUB2 needs a few extra files in a system it can read to do its thing. When you installed Linux, you installed GRUB2 including putting those extra files in /boot of your installation. Deleting that Linux installation removed those files which is why GRUB failed to boot. Your error message is the MBR bootloader complaining that it can't find the extra files it needs.

Since you don't have a Windows DVD or Windows live CD or whatnot to run Windows and 'rescue' your MBR by replacing the GRUB2 code with the native Windows bootstrapping code, you are looking at getting GRUB2 back up and functional. That can be done be re-installing Linux or, maybe, by putting its /boot files on the Windows partition (I don't know whether this last would work or not) or maybe setting up a small boot partition for these GRUB2 files. Then you can run grub-install from the Linux live CD and tell it where those extra files are.

You still have the problem of booting the Windows system. Without a specific error message and without a bootable Windows DVD, that can be a challenge. The caveat here is the fact you resized the Windows partition which may have complicated things, maybe. I always run Windows after doing this sort of thing so it can check its file systems and I know it is OK. If you do have a bootable Windows 7 on that partition, it should boot if your bootloader can find its bootable code.

One reason for some Window 7 boot problems after re-arranging partitions is that the file BootMgr needed by the W7 boot process wasn't on the main W7 system disk. A lot of times, it is in its own small (100 MB) partition. If that file is missing on your W7 partition, you'll need to find a copy and put it there. I hear you can do a plain copy. The W7 DVD repair utilities will also fix this and there are some utilities you can download from the I'net that will also repair common boot problems - but you need to be able to run Windows to use them and you will need a copy of the BootMgr file to copy as well.

If you get your bootloader straightened out, and if it finds your Windows partition, and if you have the BootMgr file on that partition and it still won't bring up Windows, you have a problem that is likely going to need some rather specific W7 help.

---

