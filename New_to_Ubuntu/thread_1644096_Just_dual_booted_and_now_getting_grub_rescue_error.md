---
title: "Just dual booted and now getting grub rescue error"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by kit21 on 2010-12-12
Hi.

I'm basically in a massive panic.

I just installed ubuntu 10.10 as a dual boot with Windows 7. I booted from a disk and installed ubuntu alongside windows 7. All seemed to be working fine. I turned off my laptop and rebooted in windows 7.  All seems to be working fine.  I think click restart in windows 7 and it turns off and in resuming I just get a black screen with:

Error: unknown filesystem
grub rescue>

I have tried to boot from my windows recovery cds I made, however it cannot find an image to boot from on these.

I have literally no idea what to do and am currently very worried I may have just completely killed a week old new laptop.....

Help would be eternally appreciated!

Fran :-(

---

### Post by Quackers on 2010-12-12
It's not dead, but it may need fixing :-)
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kit21 on 2010-12-12
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    22,362,111    22,360,064  27 Hidden HPFS/NTFS
/dev/sda2    *     22,362,112    22,566,911       204,800   7 HPFS/NTFS
/dev/sda3          22,566,912   685,442,239   662,875,328   7 HPFS/NTFS
/dev/sda4         685,443,070   976,771,071   291,328,002   f W95 Ext d (LBA)
/dev/sda5         685,443,072   864,241,663   178,798,592  83 Linux
/dev/sda6         864,243,712   871,911,423     7,667,712  82 Linux swap / Solaris
/dev/sda7         871,913,472   976,771,071   104,857,600   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        74B44F93B44F5730                       ntfs       Recovery                      
/dev/sda2        A29EFC979EFC6567                       ntfs       System Reserved               
/dev/sda3        BA94FE3994FDF7A9                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        923e411d-9a4e-44b6-bea1-be099a124fdd   ext4                                     
/dev/sda6        5cf6ec53-9da4-4684-9625-cdf6522fa251   swap                                     
/dev/sda7        54E8B0F1E8B0D28A                       ntfs       Win7 Ubuntu File Share        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 923e411d-9a4e-44b6-bea1-be099a124fdd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 923e411d-9a4e-44b6-bea1-be099a124fdd
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 923e411d-9a4e-44b6-bea1-be099a124fdd
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=923e411d-9a4e-44b6-bea1-be099a124fdd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 923e411d-9a4e-44b6-bea1-be099a124fdd
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=923e411d-9a4e-44b6-bea1-be099a124fdd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 923e411d-9a4e-44b6-bea1-be099a124fdd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=923e411d-9a4e-44b6-bea1-be099a124fdd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 923e411d-9a4e-44b6-bea1-be099a124fdd
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=923e411d-9a4e-44b6-bea1-be099a124fdd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 923e411d-9a4e-44b6-bea1-be099a124fdd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 923e411d-9a4e-44b6-bea1-be099a124fdd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 74b44f93b44f5730
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set a29efc979efc6567
    chainloader +1
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=923e411d-9a4e-44b6-bea1-be099a124fdd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=5cf6ec53-9da4-4684-9625-cdf6522fa251 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 430.5GB: boot/grub/core.img
 394.0GB: boot/grub/grub.cfg
 351.7GB: boot/initrd.img-2.6.35-22-generic
 351.7GB: boot/initrd.img-2.6.35-23-generic
 430.5GB: boot/vmlinuz-2.6.35-22-generic
 430.5GB: boot/vmlinuz-2.6.35-23-generic
 351.7GB: initrd.img
 351.7GB: initrd.img.old
 430.5GB: vmlinuz
 430.5GB: vmlinuz.old 
```Hope that works with the code tags.....

Thanks so much for your help...i was very concerned!

---

### Post by oldfred on 2010-12-12
I looks like you moved some partitions around. Grub is trying to boot from sda6, but you install is now in sda5.

Reinstall grub to the MBR with it using sda5.

#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Quackers on 2010-12-12
Whatever he said :-)

---

### Post by kit21 on 2010-12-12
At the risk of sounding really dim, how on earth do I do that?!  

What is MBR and how do I install it from the live disk?  And then what do I do?

Im sorry to ask, I'm really new to linux.

---

### Post by kit21 on 2010-12-12
In fact, scrap that.  Its sorted :)  I just followed the "How to restore the Ubuntu/XP/Vista/7 bootloader" instructions.  

Thank you both so much for taking the time to help me.  You guys on the forum are amazing!!

Woohooooooo :-)

Fran

---

### Post by wilee-nilee on 2010-12-12
Never mind you have it fixed yah.;)

---

### Post by Quackers on 2010-12-12
Excellent :-) Well done!

---

### Post by oldfred on 2010-12-12
Fran, glad you got it working.

Just for my info. I am regularly accused to being too complex on some of my responses and am trying to be less so for those that need more help. I thought I had just posted the specific instructions for you to run which were the same as the link. If it is possible we try to post answers not just links, but sometimes links explain more.

What would have made my response better? I will probably always post too much technical info as that is me, but I would still like to be able to help those that need specific instructions?

---

### Post by kit21 on 2010-12-13
Oldfred, the content was spot on of course!  I just wasn't quite sure what to do with the info once you posted it!  In hindsight it was mainly me being a little dim.  

I read the first #instruction I didn't quite know what to do as I really had no idea what MBR or sda5 were or what I was looking for.  Once i ran the first bit of code in the terminal though it made much more sense along with the link you gave.  It just took me a while to grasp it as I'm completely new to ubuntu and never really use command prompt in Windows and such.

Thanks again for your help!  :D

---

