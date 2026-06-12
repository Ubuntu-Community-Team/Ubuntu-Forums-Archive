---
title: "boot disk error"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by DarinB on 2010-07-01
i can't boot
after messing with virtualbox and attempt to install xp in it
i can access my hdds with live cd...i even reinstalled lucid. 
could i have killed my mbr????
or is it an hdd problem.
i have been able to save my home folder onto an extra hdd. 
any ideas on what i can do? 
i thought reinstalling lucid would bring back the bootability.
i did make the home drive  / not /boot not sure if that also made things worse. but i have never chosen /boot only / i simply chose not to reformat in order to try to save my home ???
HELP

---

### Post by arrange on 2010-07-01
Can you post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/")? (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)

---

### Post by DarinB on 2010-07-01
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   772,595,703   772,593,656   7 HPFS/NTFS
/dev/sda2         772,598,041 1,465,144,064   692,546,024   5 Extended
/dev/sda5         772,598,043 1,446,910,289   674,312,247  83 Linux
/dev/sda6       1,446,910,353 1,465,144,064    18,233,712  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,465,144,064 1,465,144,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,260,347,444 1,260,347,382  83 Linux
/dev/sdc2       1,260,347,445 1,465,144,064   204,796,620  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B2C27621C275EA4D                       ntfs       System                        
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6237f2fc-580f-4f64-b45a-71d0753debbd   ext4                                     
/dev/sda6        751c0a41-95f0-41b0-ab41-8964640b0a2c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        63705dc6-133e-449e-9c9d-114a2a760102   ext3       music                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4242b0bf-b298-4911-bfc2-af4d442c195e   ext4                                     
/dev/sdc2        9a66b32b-8213-4469-a52b-ed24ba8357f7   ext4                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found
error: /dev/sdi: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/System            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/4242b0bf-b298-4911-bfc2-af4d442c195e ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc2        /media/9a66b32b-8213-4469-a52b-ed24ba8357f7 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/6237f2fc-580f-4f64-b45a-71d0753debbd ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /mnt                     ext4       (rw)


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
search --no-floppy --fs-uuid --set 6237f2fc-580f-4f64-b45a-71d0753debbd
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
search --no-floppy --fs-uuid --set 6237f2fc-580f-4f64-b45a-71d0753debbd
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 6237f2fc-580f-4f64-b45a-71d0753debbd
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6237f2fc-580f-4f64-b45a-71d0753debbd
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=6237f2fc-580f-4f64-b45a-71d0753debbd ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6237f2fc-580f-4f64-b45a-71d0753debbd
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=6237f2fc-580f-4f64-b45a-71d0753debbd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6237f2fc-580f-4f64-b45a-71d0753debbd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6237f2fc-580f-4f64-b45a-71d0753debbd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2c27621c275ea4d
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
UUID=6237f2fc-580f-4f64-b45a-71d0753debbd /               ext4    errors=remount-ro 0       1
# /mnt/music was on /dev/sdb1 during installation
UUID=63705dc6-133e-449e-9c9d-114a2a760102 /mnt/music      ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=751c0a41-95f0-41b0-ab41-8964640b0a2c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 556.7GB: boot/grub/core.img
 438.7GB: boot/grub/grub.cfg
 558.2GB: boot/initrd.img-2.6.32-21-generic
 558.2GB: boot/vmlinuz-2.6.32-21-generic
 558.2GB: initrd.img
 558.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh sdi

---

### Post by arrange on 2010-07-01
I don't see any *lucid* installed, only *Mint* on *sda5*. Are you able to boot into *Mint*? Can you see the Grub menu when you boot?

---

### Post by DarinB on 2010-07-01
I am using linux mint build from lucid lynx???

---

### Post by DarinB on 2010-07-01
sorry no boot menu only boot failure message.
this occurred after trying to install xp on virtualbox i think it did something to my mbr or something like that but i really don't know much about it all
I can not boot at all

---

### Post by DarinB on 2010-07-01
anybody i am kind of freaking out...
even a reinstall of lm9 did not fix it. i am at a loss.

---

### Post by arrange on 2010-07-01
Does BIOS see the disks?
If so, can you try installing Grub on another disk and set BIOS to boot from that?
Or you can boot into a LiveCD and choose *Boot from first hard disk*.

---

### Post by DarinB on 2010-07-01
i can boot to cd live i am on it now
can i check the bios with out rebooting?
how do i put grub on another disk?

---

### Post by DarinB on 2010-07-01
booting from fist disk did not work i tried it earlier

---

### Post by DarinB on 2010-07-01
the problem was a bios switch 
when i had the live cd in and clicked boot from first hard drive nothing i got the same error. 
eventually after i found out that the mbr and grub were there
i checked again and the bios was set to boot from the 2 hdd not the 1 hdd 
i wonder if the virtualbox changed that.
no idea but i am back and it works

---

