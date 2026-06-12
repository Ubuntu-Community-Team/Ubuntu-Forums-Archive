---
title: "Ubuntu not starting, it's a black screen with a blinking line"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by mckinnes on 2010-09-17
this is my first post so if i screw something up sorry.

this morning i booted Ubuntu 10.10 fine. i was running and update on it and it asked me to do a partial upgrade so i did and it ran through that fine until it got to a file i can't quite remember it had smb something
anyway it said there where 2 mins remanding and i let it do it's thing. well 10 mins latter i had to leave and shut down the computer. now when i boot Ubuntu it starts the splash screen then goes to a black screen that says "automatic write through cache" something like that. then a small white line appears under it and continues to blink for as long as the computer is on. 
i have no clue what i did but i have stuff i need to get off Ubuntu 

i have it duel booted with windows 7 64 bit

---

### Post by Rubi1200 on 2010-09-17
Use the LiveCD to get your files.

If you are using 10.10 have you read this?

> **This is a beta release. Do not install it on production machines. The final stable version will be released on October 10, 2010.**
[http://www.ubuntu.com/testing/maverick/beta](http://www.ubuntu.com/testing/maverick/beta)

Beta=bugs and is not intended for stable environments.

That said, can you boot into Ubuntu at all and what graphics card do you have installed?

Can you boot into Windows?

---

### Post by mckinnes on 2010-09-19
It's not booting the GUI at all and i'm using Nvidia GeForce 9400 GT it's plugged into my TV and windows works fine. the only thing that changed about the Grub screen is the count down doesn't happen anymore.

---

### Post by Rubi1200 on 2010-09-19
If you need to rescue files from the Ubuntu installation, boot the computer with the LiveCD and get them off.

Then, while still on the LiveCD, post the results of the bootscript linked to at the bottom of my post please.

---

### Post by mckinnes on 2010-09-21
ok i ran the scrip and got this




                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

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
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,911   482,519,521   482,312,611   7 HPFS/NTFS
/dev/sda3         600,258,560   625,139,711    24,881,152   7 HPFS/NTFS
/dev/sda4         482,521,086   600,258,559   117,737,474   5 Extended
/dev/sda5         482,521,088   595,359,743   112,838,656  83 Linux
/dev/sda6         595,361,792   600,258,559     4,896,768  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,576,704   312,576,642   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        10C0AFE2C0AFCC72                       ntfs       SYSTEM                        
/dev/sda2        0E6A864C6A86310F                       ntfs       HP                            
/dev/sda3        C8944D5F944D50DC                       ntfs       FACTORY_IMAGE                 
/dev/sda4: PTTYPE="dos" 
/dev/sda5        ac1cb468-b2e3-41f4-9180-1573fe89f534   ext4                                     
/dev/sda6        2b7f6220-3b16-4c26-a6c7-46f96c044250   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1A04-0628                              vfat       TOSHIBA EXT                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/ac1cb468-b2e3-41f4-9180-1573fe89f534 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/TOSHIBA EXT       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
set default="10"
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set ac1cb468-b2e3-41f4-9180-1573fe89f534
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set ac1cb468-b2e3-41f4-9180-1573fe89f534
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ac1cb468-b2e3-41f4-9180-1573fe89f534
    linux    /boot/vmlinuz-2.6.35-20-generic root=UUID=ac1cb468-b2e3-41f4-9180-1573fe89f534 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ac1cb468-b2e3-41f4-9180-1573fe89f534
    echo    'Loading Linux 2.6.35-20-generic ...'
    linux    /boot/vmlinuz-2.6.35-20-generic root=UUID=ac1cb468-b2e3-41f4-9180-1573fe89f534 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ac1cb468-b2e3-41f4-9180-1573fe89f534
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=ac1cb468-b2e3-41f4-9180-1573fe89f534 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ac1cb468-b2e3-41f4-9180-1573fe89f534
    echo    'Loading Linux 2.6.35-19-generic ...'
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=ac1cb468-b2e3-41f4-9180-1573fe89f534 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ac1cb468-b2e3-41f4-9180-1573fe89f534
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ac1cb468-b2e3-41f4-9180-1573fe89f534 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ac1cb468-b2e3-41f4-9180-1573fe89f534
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ac1cb468-b2e3-41f4-9180-1573fe89f534 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ac1cb468-b2e3-41f4-9180-1573fe89f534
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ac1cb468-b2e3-41f4-9180-1573fe89f534
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ac1cb468-b2e3-41f4-9180-1573fe89f534
    multiboot    /boot/memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set ac1cb468-b2e3-41f4-9180-1573fe89f534
    multiboot    /boot/memtest86+_multiboot.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 10c0afe2c0afcc72
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set c8944d5f944d50dc
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
# / was on /dev/sda5 during installation
UUID=ac1cb468-b2e3-41f4-9180-1573fe89f534 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2b7f6220-3b16-4c26-a6c7-46f96c044250 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 288.0GB: boot/grub/core.img
 260.0GB: boot/grub/grub.cfg
 253.8GB: boot/initrd.img-2.6.32-24-generic
 254.7GB: boot/initrd.img-2.6.35-19-generic
 254.8GB: boot/initrd.img-2.6.35-20-generic
 288.9GB: boot/vmlinuz-2.6.32-24-generic
 253.4GB: boot/vmlinuz-2.6.35-19-generic
 289.1GB: boot/vmlinuz-2.6.35-20-generic
 289.0GB: boot/vmlinuz-2.6.35-21-generic
 254.8GB: initrd.img
 254.7GB: initrd.img.old
 289.1GB: vmlinuz
 253.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c8 b9 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c8  b9 06 00 c0 4a 00 00 00  |............J...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Rubi1200 on 2010-09-21
You could try reinstalling GRUB, but as I said before 10.10 is in beta and you have to expect that there will be bugs etc.

The first method works in most cases:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by coffeecat on 2010-09-21
@mckinnes, if you do manage to get your 10.10 working again, you need to know this:

**Never do a partial upgrade before a release goes final.**

> **mckinnes said:**
> i was running and update on it and it asked me to do a partial upgrade so i did

More here:

[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

Apart from that, if you are new to Linux, running a pre-release is not a good idea. Even when a release goes final there are often niggling teething troubles for a month or so.

If you can't get it going again, use the live CD (**please** use the 10.04 CD) to backup your files and then install 10.04. Use the 10.04.1 updated version.

---

### Post by mckinnes on 2010-09-23
well thanks for all your help guys but i think i'm just going to reinstall it. i got all the important things moved to my external HDD. thanks for the help even if it didn't fix the problem, and thanks for the advice.

---

