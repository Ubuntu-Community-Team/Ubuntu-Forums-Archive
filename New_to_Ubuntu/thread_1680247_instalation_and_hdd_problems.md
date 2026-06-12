---
title: "instalation and hdd problems"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by XSindy on 2011-02-02
before I start: yes you may laugh and call me an idiot

yesterday I got a new laptop with win7 ultimate installed. Since it's ultimate and all (and I'll need it for school) I decided to leave it and make a dual boot with ubuntu. 

I've always "manualy" partitioned my hdd, but now I found one extra primary partition (100mb) that win needed for something (system reserved). I decided to trust the automatic partitioning that the installation provides. And installed it like that. But ubuntu wouldn't load. 
So I decided to reinstall it ... and I swear I took the whole partition option and not the whole disk one but I saw that the other partitions were vanishing and panicked and... turned of the computer.

so now I'm stuck with daring to try to install ubuntu again, crying after the win, being an idiot and writing this from the liveCD

---

### Post by mikewhatever on 2011-02-02
Well, first, I hope you have a way to reinstall or recover W7, if its partitions are not there. Check that by running **sudo fdisk -l** from a terminal window.

---

### Post by mastablasta on 2011-02-02
ha, ha... well it's actually not funny but since you said we may laugh :KS
 
anyway it's a common porblem and many users face it. the laptop manufacturers find it funny and create 4 disk parititons that are primary. i guess they try to get rid of anyone trying linux or something.
 
you will need to make one partition into extended partition. if you have recovery CD use that one to recover windows. if not, demand one.
then:
[http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/](http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/)

---

### Post by XSindy on 2011-02-02
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       37767   303355904   83  Linux
/dev/sda2           37767       38914     9212929    5  Extended
/dev/sda5           37767       38914     9212928   82  Linux swap / Solaris

no win :S

I just hope I didn't damage the hdd :/
I've found something that could be a recovery disc. If it doesn't work, I'll just start hunting down a win instalation

the interesting thing is that the liveCD is working perfectly so far, but the installed ubuntu wouldn't even boot. :s

---

### Post by Quackers on 2011-02-02
It does seem as though you have over-written Windows (not necessarily your fault, if using the 10.10 installer). But, having said that, your new Ubuntu installation should boot.
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by XSindy on 2011-02-02
@mastablasta laughing is good for the soul :D

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   167,774,207   167,772,160  83 Linux
/dev/sda2         167,774,208   174,065,663     6,291,456  82 Linux swap / Solaris
/dev/sda3         174,065,664   625,141,759   451,076,096  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        fe61bba3-941d-4f39-a992-439b38693e0a   ext4                                     
/dev/sda2        86b12168-4166-43d9-aa99-4b81a44c460e   swap                                     
/dev/sda3        f69bcb02-a3d7-45c8-928b-5707a8ffde79   ext2                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/fe61bba3-941d-4f39-a992-439b38693e0a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda3        /media/f69bcb02-a3d7-45c8-928b-5707a8ffde79 ext2       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set fe61bba3-941d-4f39-a992-439b38693e0a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set fe61bba3-941d-4f39-a992-439b38693e0a
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fe61bba3-941d-4f39-a992-439b38693e0a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fe61bba3-941d-4f39-a992-439b38693e0a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fe61bba3-941d-4f39-a992-439b38693e0a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fe61bba3-941d-4f39-a992-439b38693e0a ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fe61bba3-941d-4f39-a992-439b38693e0a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fe61bba3-941d-4f39-a992-439b38693e0a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fe61bba3-941d-4f39-a992-439b38693e0a /               ext4    errors=remount-ro 0       1
/dev/sda3       /home           ext2    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=86b12168-4166-43d9-aa99-4b81a44c460e none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  66.7GB: boot/grub/core.img
  13.1GB: boot/grub/grub.cfg
  38.9GB: boot/initrd.img-2.6.35-22-generic
  66.7GB: boot/vmlinuz-2.6.35-22-generic
  38.9GB: initrd.img
  66.7GB: vmlinuz
```

:? :-s

---

### Post by mikewhatever on 2011-02-02
I am no expert with W7, but you could try asking the vendor for installation media. After all, you payed for it.

What happens exactly when you try booting Ubuntu?
It's odd, but the output you posted looks different from that of the fdisk -l.

---

### Post by sydbat on 2011-02-02
> **XSindy said:**
> yesterday I got a new laptop with win7 ultimate installed.This is what I would do - zero out the HDD, then bring the laptop back to the store you bought it from and say that, when you decided to try out your new laptop this morning, you found out there was no OS installed. Ask them to either install one for you or give you a new laptop. Then, in a somewhat disgusted manner, have them boot it to prove the OS is installed (otherwise they might figure out you borked the thing).

I dunno...worth a try...

---

