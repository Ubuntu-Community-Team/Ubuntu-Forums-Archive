---
title: "GRUB on external hdd"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by CuriousSoul on 2010-04-26
Hi there guys, i have XP installed on my internal hdd and Karmic Koala installed on the external one.I have also installed GRUB on the external hdd, so whenever my external hdd is plugged in (external hdd has first priority in the BIOS boot order) it gives me the possibility to start ubuntu or xp, now the problem is that lately it shows " GRUB is starting" and then the computer restarts and keeps doing the same thing. Could somebody help me, thanks in advance.

---

### Post by oldfred on 2010-04-26
Just to be sure where things are at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by CuriousSoul on 2010-04-26
> **oldfred said:**
> Just to be sure where things are at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

Thanks for the reply, i followd your instructions and got this....

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x283f283f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   216,186,704   216,186,642   7 HPFS/NTFS
/dev/sda2         216,186,768   232,332,029    16,145,262   c W95 FAT32 (LBA)
/dev/sda3         232,332,030   234,436,544     2,104,515  d7 Unknown


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1fddead4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   600,686,414   600,686,352   c W95 FAT32 (LBA)
/dev/sdb2         600,686,415   976,768,064   376,081,650   5 Extended
/dev/sdb5         600,686,478   970,759,754   370,073,277  83 Linux
/dev/sdb6         970,759,818   976,768,064     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        18A81589A8156692                       ntfs                                     
/dev/sda2        66CA-4909                              vfat       HP_RECOVERY                   
/dev/sda3        0088522A88521E8A                       ntfs                                     
/dev/sdb1        1A06-0638                              vfat       PACKARDBELL                   
/dev/sdb5        f3476dc8-0f2f-4424-ae50-8325e9c82232   ext4                                     
/dev/sdb6        ba196731-ad0a-4f58-8b26-89beaa97aade   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/PACKARDBELL       vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdb5        /media/disk              ext4       (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda3/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /maxmem=256 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set f3476dc8-0f2f-4424-ae50-8325e9c82232
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set f3476dc8-0f2f-4424-ae50-8325e9c82232
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=f3476dc8-0f2f-4424-ae50-8325e9c82232 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set f3476dc8-0f2f-4424-ae50-8325e9c82232
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=f3476dc8-0f2f-4424-ae50-8325e9c82232 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set f3476dc8-0f2f-4424-ae50-8325e9c82232
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=f3476dc8-0f2f-4424-ae50-8325e9c82232 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set f3476dc8-0f2f-4424-ae50-8325e9c82232
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=f3476dc8-0f2f-4424-ae50-8325e9c82232 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set f3476dc8-0f2f-4424-ae50-8325e9c82232
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=f3476dc8-0f2f-4424-ae50-8325e9c82232 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set f3476dc8-0f2f-4424-ae50-8325e9c82232
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=f3476dc8-0f2f-4424-ae50-8325e9c82232 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set f3476dc8-0f2f-4424-ae50-8325e9c82232
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f3476dc8-0f2f-4424-ae50-8325e9c82232 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set f3476dc8-0f2f-4424-ae50-8325e9c82232
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f3476dc8-0f2f-4424-ae50-8325e9c82232 ro single 
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
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set dca499c4a499a196
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda3)" {
    insmod fat
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 66ca-4909
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=f3476dc8-0f2f-4424-ae50-8325e9c82232 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=ba196731-ad0a-4f58-8b26-89beaa97aade none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 310.5GB: boot/grub/core.img
 312.5GB: boot/grub/grub.cfg
 308.1GB: boot/initrd.img-2.6.31-14-generic
 308.3GB: boot/initrd.img-2.6.31-16-generic
 310.9GB: boot/initrd.img-2.6.31-17-generic
 311.8GB: boot/initrd.img-2.6.31-19-generic
 308.1GB: boot/vmlinuz-2.6.31-14-generic
 308.1GB: boot/vmlinuz-2.6.31-16-generic
 310.8GB: boot/vmlinuz-2.6.31-17-generic
 310.8GB: boot/vmlinuz-2.6.31-19-generic
 311.8GB: initrd.img
 310.9GB: initrd.img.old
 310.8GB: vmlinuz
 310.8GB: vmlinuz.old

```

---

### Post by oldfred on 2010-04-26
I do not see anything wrong with grub or Ubuntu. But your windows in sda2 has a boot.ini for the first not second partition. And the grub boot stanza for windows does not seem to have the correct UUID.

/dev/sda1        [COLOR=DarkRed]18A81589A8156692   [/COLOR]                    ntfs   

menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set [COLOR=DarkRed]dca499c4a499a196[/COLOR]
    drivemap -s (hd0) ${root}
    chainloader +1

from boot.ini in sda2, 1 should be 2:
multi(0)disk(0)rdisk(0)partition([COLOR=Red]1[/COLOR])

this is a list of common boot issues with work arounds,but I do not see one that seems to match yours. You may want to review as the description may be slightly different and you will recognize it.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

Could you print this out also:
/boot/grub/device.map

---

