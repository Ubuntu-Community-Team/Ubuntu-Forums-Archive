---
title: "Boot with CD from GRUB"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by Sebastianj on 2010-08-25
Hey everybody - 

I am VERY fresh to Ubuntu. I am enjoying it very much and am eager to learn more.   

I am currently running a dual OS booting with GRUB- (Windows XP and Ubuntu GNOME) , each on their respective HDs.  What I am trying to do is reinstall XP. I am trying to boot from the XP CD however booting straight to GRUB will not allow me to. Changing boot order in my BIOS also does not work. Is there a solution to what I wish to do? Ideally I would like to keep my Ubuntu OS as it is and reinstall just XP. However, if I need to wipe both and start over, I am willing to do so.  

Any help is appreciated. Thanks in advnace. 

Sebass

---

### Post by oldfred on 2010-08-25
You probably have grub installed to sda (the windows drive) and nothing in the MBR of the Ubuntu drive. But to be sure of what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Sebastianj on 2010-08-25
Thanks for the quick response. Here are the contents of RESULTS.txt



          ```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   149,468,759   149,388,435   7 HPFS/NTFS
/dev/sda3         149,468,760   156,232,124     6,763,365  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D5-0802                              vfat       DellUtility                   
/dev/sda2        CC08758E087577F2                       ntfs                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6f2571c0-194c-4d3b-b0d4-ac4bd960cda1   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        84919f12-61dc-467c-8dab-395908db8893   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6f2571c0-194c-4d3b-b0d4-ac4bd960cda1
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6f2571c0-194c-4d3b-b0d4-ac4bd960cda1
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6f2571c0-194c-4d3b-b0d4-ac4bd960cda1
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6f2571c0-194c-4d3b-b0d4-ac4bd960cda1
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6f2571c0-194c-4d3b-b0d4-ac4bd960cda1
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6f2571c0-194c-4d3b-b0d4-ac4bd960cda1
    echo    'Loading Linux 2.6.31-19-generic ...'
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6f2571c0-194c-4d3b-b0d4-ac4bd960cda1
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6f2571c0-194c-4d3b-b0d4-ac4bd960cda1
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6f2571c0-194c-4d3b-b0d4-ac4bd960cda1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 6f2571c0-194c-4d3b-b0d4-ac4bd960cda1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set cc08758e087577f2
    drivemap -s (hd0) ${root}
    chainloader +1
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=6f2571c0-194c-4d3b-b0d4-ac4bd960cda1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=84919f12-61dc-467c-8dab-395908db8893 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   3.4GB: boot/grub/core.img
  11.0GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
   1.2GB: boot/initrd.img-2.6.31-19-generic
   1.4GB: boot/initrd.img-2.6.32-22-generic
   1.5GB: boot/initrd.img-2.6.32-24-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-19-generic
   1.0GB: boot/vmlinuz-2.6.32-22-generic
   1.4GB: boot/vmlinuz-2.6.32-24-generic
   1.5GB: initrd.img
   1.4GB: initrd.img.old
   1.4GB: vmlinuz
   1.0GB: vmlinuz.old
```

---

### Post by eriktheblu on 2010-08-25
To install Windows from the CD, you would need to boot to the CD.

This is not a Grub issue, this is a BIOS issue. By the time you get to Grub, it's too late.

> Changing boot order in my BIOS also does not work.To eliminate the obvious, when you changed it, did you set the CD ROM as top priority? If your HDD is first in boot priority, it won't even look at the CD ROM.

Failing that, look for a one time boot option. This will usually display at the same time as the BIOS settings prompt.

---

### Post by oldfred on 2010-08-25
A few BIOS require you to both change the boot priority to CD/DVD in BIOS and use the f12  (or one time boot key) to also choose the CD.

Once you have reinstalled windows you still have grub in the Ubuntu drive. You can boot windows and make sure it works, then in BIOS change to boot the Ubuntu drive. Once in Ubuntu run sudo update-grub and it should find your new windows install and let you boot it also.

---

### Post by Sebastianj on 2010-08-25
Eriktheblu
I understand what you are saying. Indeed these are options before GRUB even loads. I double checked and CD-ROM is first priority in BIOS. Before GRUB loads I also have a choice for a one time boot option. In both cases, regardless of what I choose, GRUB still loads.

---

### Post by Sebastianj on 2010-08-25
My apologies to you both. I over looked a few things in BIOS when setting boot priority. This time when I boot I am told that there are no bootable devices. Possibly an issue with my XP disk?  I have installed using this copy in the past.

---

### Post by eriktheblu on 2010-08-27
It may be the disk, or even the CD drive itself. If you had installed Ubuntu using that same CD drive, that would indicate that the drive is OK. Try booting from an Ubuntu live CD for confirmation. If the live CD fails to boot, play with your BIOS some more, or look for an alternate optical drive.

If a visual inspection of the disk reveals no defects, boot either OS and try to access the disk from there. If you don't see anything that looks like corrupt data, that indicates (but does not confirm) the disk is ok.

Failing all this, you might be able to obtain a backup copy of the XP install disk (ensure the version is identical) and install using your same license.

Does your motherboard support booting from USB? I think I've seen methods to install Windows that way.

---

