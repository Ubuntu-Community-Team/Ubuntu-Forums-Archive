---
title: "vista won't boot after 10.04 upgrade"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by keroman on 2010-05-07
hi all totally new to this hope you can help

have been enjoying ubuntu 9.10 on a dual boot with vista, asus laptop had vista home premium on and I installed ubuntu afterwards, all has been o.k. until I upgraded to 10.04:-(.

 starts up o.k. and runs ubuntu with no problems, but if I select vista, I get a loading bar at bottom of screen and then it opens up to windows cannot open this may be to some software, please insert recovery disc to repair?  sorry for being so long winded, I have tried "how to restore boot loader" and read alot, but don't seem to able to sort it .

if anyone can point me in the right direction, I would be grateful:p
thanks

---

### Post by Tikhon03 on 2010-05-07
This is a fairly well known issue, but I haven't seen any indication of a fix yet, which is why I have decided not to upgrade yet (I am also dual-booting).  One thing you could try is uninstalling the new kernel along with the other packages that were installed with it (a newer version of grub2 perhaps).

---

### Post by keroman on 2010-05-07
thanks for info, looks like I may have to wait a while for a fix, not  confident enough to start removing things, don't want to loose it all together

---

### Post by louieb on 2010-05-07
Upgrading to 10.04 should not have affected your Vista install. But please take a look.
Get run and put the results.txt in your next post [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/")

Information provided by the script should show what needs to be done to get everything working again.

---

### Post by Paul T. on 2010-05-07
I had the same problem with XP Home, only solution I found was to first re-install Windows MBR then re-install Grub2, long winded but it does work. :roll:

---

### Post by kansasnoob on 2010-05-07
> **louieb said:**
> Upgrading to 10.04 should not have affected your Vista install. But please take a look.
Get run and put the results.txt in your next post [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/")

Information provided by the script should show what needs to be done to get everything working again.

+1! It may be this problem:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But we'll only know when we see the output of the Boot Info Script.

---

### Post by keroman on 2010-05-08
hello louieb
do you want all the info text or a certain part ofi, as there seems to be a lot

---

### Post by keroman on 2010-05-08
also a new thead has started and this has been posted as a solution?

sudo update-initramfs -u -k all
sudo update-grub

---

### Post by keroman on 2010-05-08
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32 sudo bash ~/Desktop/boot_info_script*.sh 
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 32. But according to the info from fdisk, 
                       sda5 starts at sector 131559456.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    14,338,047    14,336,000  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     14,338,048   131,557,375   117,219,328   7 HPFS/NTFS
/dev/sda3         131,559,360   488,397,095   356,837,736   f W95 Ext d (LBA)
/dev/sda5         131,559,456   383,377,845   251,818,390   7 HPFS/NTFS
/dev/sda6         383,378,200   484,011,095   100,632,896  83 Linux
/dev/sda7         484,011,100   488,397,095     4,385,996  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        80E9-C15B                              vfat       RECOVERY                      
/dev/sda2        B660ECF460ECBC6D                       ntfs       VistaOS                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        FE90F0A990F06A13                       ntfs       DATA                          
/dev/sda6        a3cc7f47-3d45-465d-b772-a70a197128db   ext4                                     
/dev/sda7        4e4fc065-6cff-4c17-900d-bec00f5e9081   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set a3cc7f47-3d45-465d-b772-a70a197128db
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
search --no-floppy --fs-uuid --set a3cc7f47-3d45-465d-b772-a70a197128db
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a3cc7f47-3d45-465d-b772-a70a197128db
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a3cc7f47-3d45-465d-b772-a70a197128db ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a3cc7f47-3d45-465d-b772-a70a197128db
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a3cc7f47-3d45-465d-b772-a70a197128db ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a3cc7f47-3d45-465d-b772-a70a197128db
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a3cc7f47-3d45-465d-b772-a70a197128db ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a3cc7f47-3d45-465d-b772-a70a197128db
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a3cc7f47-3d45-465d-b772-a70a197128db ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a3cc7f47-3d45-465d-b772-a70a197128db
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=a3cc7f47-3d45-465d-b772-a70a197128db ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a3cc7f47-3d45-465d-b772-a70a197128db
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=a3cc7f47-3d45-465d-b772-a70a197128db ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a3cc7f47-3d45-465d-b772-a70a197128db
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set a3cc7f47-3d45-465d-b772-a70a197128db
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 80e9-c15b
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b660ecf460ecbc6d
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=a3cc7f47-3d45-465d-b772-a70a197128db /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4e4fc065-6cff-4c17-900d-bec00f5e9081 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 196.4GB: boot/grub/core.img
 196.6GB: boot/grub/grub.cfg
 209.2GB: boot/initrd.img-2.6.31-21-generic
 211.8GB: boot/initrd.img-2.6.32-21-generic
 197.2GB: boot/initrd.img-2.6.32-22-generic
 204.9GB: boot/vmlinuz-2.6.31-21-generic
 209.2GB: boot/vmlinuz-2.6.32-21-generic
 197.2GB: boot/vmlinuz-2.6.32-22-generic
 197.2GB: initrd.img
 211.8GB: initrd.img.old
 197.2GB: vmlinuz
 209.2GB: vmlinuz.old

---

### Post by louieb on 2010-05-08
The Good and Bad news is - don't see anything wrong. Except for the labels on the Vista entries. - Have you tried both?  Looks like Vista and Vista recovery are labeled backwards.  

BTW: Yes i wanted to look at all of it - never know which sections might be relevant. 
Also next time use code tags (the # on the tool bar).

---

### Post by keroman on 2010-05-08
hi louieb

:-) that worked,thankyou very much, I did'nt try that, but like you say they are swapped, don't think they were before, forgot how sllloooow vista is, have'nt been in since 1st april, only by chance I wanted to load vista, its busy updating itself, so I have got the wifes notebook. once again thanks very much indeed. well solved

p.s. can you explain #

---

### Post by cosaki on 2010-05-10
I think he means that when you post a reply with the information he requested, you need to highlight that part of the information and then click the "#" icon in the message toolbar.  That puts everything in a box in the reply message :)

---

### Post by keroman on 2010-05-11
thanks, had a look at that, will remember for next time. everything is o.k. now

---

