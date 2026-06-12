---
title: "Post Gparted - &quot;Windows Failed to start. &quot; \ubuntu\winboot\wubildr.mbr"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by Liammu on 2010-12-15
Hi good people,
 
I have seen help threads on this subject but none work for me. I am new to linux and at the moment I can't even boot into the OS... I dont' want to re install, I have a development environment I took a long time setting up. Worst case scenario I'll bite the bullet and re install. Hopefully some hero out there can save me the day. There are only 365 after all.
 
HISTORY
I have win 7 installed. I installed Ubuntu 10.1.4. they were both running in sepearte partitions. I dual booted into either at boot up time. 
 
One extra piece of info. Weeks ago. While in Windows7 I relabled the E: drive calling it Ubuntu. This was probably a stupid thing to do. Ubuntu didn't seem to mind at the time. I wonder if gparted got confused during the partition process because of this? Can't remember what default Label was.
 
 
LATE LAST NIGHT
I ran out of space on Ubuntu and used the Gparted Live disk to re partition. Taking away a bit off space on Win 7 and expanding Ubuntu. I went to bed as it did it's thing.
 
THIS MORNING
When I re booted for first time after this. I coudn't boot into any OS. 
I booted with the Win 7 DVD and chose the repair windows option. I got my windows 7 back (and my WIP Thesis ...phew! but I am still an idiot, can't believe I didn't back this up..)
 
Whey I try to boot into Ubuntu (which I am starting to really like ...) I get the error below.
the error referrs to Windows but it should say Ubuntu.
[INDENT][INDENT]"Windows Failed to start. " 
A recent hardware or software change might be the cause. To fix the problem:
Insert your windows installation disc and restart your computer. 
Choose your language settings, and then click "next." 
Click "Repair your computer." 
If you do not have this disc, contact your system administrator or computer manufacturer for assistance.
File: \ubuntu\winboot\wubildr.mbr
status: 0xc000000e
[/INDENT][/INDENT]I can view the E:\ubuntu\winboot\wubildr.mbr from windows7. 
Is there anything I can to to fix it?
Currently I don't even know how to edit a MBR file, if that's the fix. 
 
 
Regards,
Liam.

---

### Post by Rubi1200 on 2010-12-15
Hi and welcome to the forums :)

For Wubi issues and solutions, see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Also take a look at the Wubi Guide, linked near the beginning of the article.

Just so you know, there are times when it is necessary to run the Windows repair for the bootloader 3 times.

It would also be helpful if you run the boot info script (also linked in the first thread).

Thanks.

---

### Post by mastablasta on 2010-12-15
you didn't install to separate partition and instead used a Wubi install. you might be able to recover files (thread was already posted)
 
i wouold just like to add that wubi is ment to test teh system. it can also cause some issues that propper dual boot won't and finnaly since it installs in a large file within windows if that file get's corrupted you can say goodbye to all the data. 
 
so fix htis issue and then do a propper dual boot setup on separate partitions.

---

### Post by bcbc on 2010-12-15
It sounds like you've messed up the bcd boot process by resizing the partition. Maybe the uuid changed. I don't know exactly how bcd entries are setup... but the message you are receiving is from the Windows boot manager, not Ubuntu (which explains the 'windows failed to start' message.

So my recommendation is to search on bcdedit, and figure out what has changed and how to get it fixed.

There are other options I suppose involving data recovery and reinstalling. But note that resizing the ntfs host partition does not increase space to a wubi install - the space is limited to the virtual disk (root.disk, or other virtual disks). 

If you have a separate partition, it is usually best to install directly to it (not use wubi).

---

### Post by Liammu on 2010-12-17
Thanks,
For everyone help so far.  
I ran that [Boot info script]("http://bootinfoscript.sourceforge.net/") courtesy of meierfra. 
See the result below. 

I have installed my UBUNTU into a separate partition, at least I'm pretty sure I have.
Also some extra info on my boot up screen . Windows7 is still my default but it is  below Ubuntu, it used to be on top. Another indication something got  screwed up.

I think this is what I need to do.
( [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) ) 
[SIZE=3]**Solution #1 (10.04):**[/SIZE]

If it is a 10.04 install, the fix is to boot an Ubuntu LiveCD, loop  mount the wubi root.disk and manually edit the grub.cfg file.



               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             210,944    94,679,039    94,468,096   7 HPFS/NTFS
/dev/sda3          94,679,040   117,209,087    22,530,048   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       4263f0d8-b936-4fe1-9645-b5ffc6653e84   ext4                                     
/dev/sda1        8C7074037073F1F6                       ntfs       System Reserved               
/dev/sda2        F8688043687FFF1E                       ntfs                                     
/dev/sda3        145C93E55C93C042                       ntfs       ubuntu                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 145c93e55c93c042
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 145c93e55c93c042
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 145c93e55c93c042
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 145c93e55c93c042
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8c7074037073f1f6
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


    .3GB: boot/grub/grub.cfg
   3.4GB: boot/initrd.img-2.6.32-24-generic
   3.4GB: boot/initrd.img-2.6.32-25-generic
    .9GB: boot/vmlinuz-2.6.32-24-generic
    .2GB: boot/vmlinuz-2.6.32-25-generic
   3.4GB: initrd.img
   3.4GB: initrd.img.old
    .2GB: vmlinuz
    .9GB: vmlinuz.old

---

### Post by bcbc on 2010-12-17
You're not getting as far as the grub.cfg. It's the windows boot manager that is kicking out the error.
Also, that grub.cfg issue is for wubi installed to the same partition as windows (c: drive), not the way you have it.

---

