---
title: "3 OS one little netbook"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by olayak on 2010-11-02
So, long story short, I had an extra, large, partition that I wasn't using.  I also had a partition with win7 and another with ubuntu 10.10.  So I stupidly (as a newb) deleted the extra partition in an attempt to free up space.  It turns out that it was the partition that had grub on it, so now I just it just says "grub rescue>" when I boot up.
Help!

---

### Post by Hippytaff on 2010-11-02
you can reinstall grub with the super grub live cd

[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by Quackers on 2010-11-02
Please boot from your Ubuntu Live cd/usb and after making sure you have an internet connection please go to the site below and download the boot script to your DESKTOP and run the script in a terminal using the command given on the first page of that site. This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. To get CODE tags click on New Reply and then on the # symbol in the toolbar.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by olayak on 2010-11-02
I'm having trouble getting online, I will have to try from another location and post in a little while.

---

### Post by Hippytaff on 2010-11-02
Quackers - I wondered when you were going to turn up :-D

---

### Post by Quackers on 2010-11-02
I'm like a bad penny :-)
olayak, if you boot into the Ubuntu version you want to keep then install gparted through Synaptic Package Manager then when Gparted screen opens up delete the partition with the Ubuntu system you DON'T want to keep. Click on apply (green tick) and then exit Gparted.
Then open up a terminal and run
```
sudo update-grub
```
You should be good then.

---

### Post by olayak on 2010-11-02
```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

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

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   183,421,717   183,419,670   7 HPFS/NTFS
/dev/sda2         336,453,630   488,396,799   151,943,170   5 Extended
/dev/sda5         336,453,632   412,560,435    76,106,804  83 Linux
/dev/sda6         482,439,168   488,396,799     5,957,632  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        188010D98010BF66                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        86ca2c55-8382-4515-b294-f344f78525dc   ext4                                     
/dev/sda6        2b544c2a-3c2e-4655-a6be-74f49a860eb7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         1861-6E30                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
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
search --no-floppy --fs-uuid --set 86ca2c55-8382-4515-b294-f344f78525dc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 86ca2c55-8382-4515-b294-f344f78525dc
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 86ca2c55-8382-4515-b294-f344f78525dc
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=86ca2c55-8382-4515-b294-f344f78525dc ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 86ca2c55-8382-4515-b294-f344f78525dc
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=86ca2c55-8382-4515-b294-f344f78525dc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 86ca2c55-8382-4515-b294-f344f78525dc
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=86ca2c55-8382-4515-b294-f344f78525dc ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 86ca2c55-8382-4515-b294-f344f78525dc
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=86ca2c55-8382-4515-b294-f344f78525dc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 86ca2c55-8382-4515-b294-f344f78525dc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 86ca2c55-8382-4515-b294-f344f78525dc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 188010d98010bf66
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
UUID=86ca2c55-8382-4515-b294-f344f78525dc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2b544c2a-3c2e-4655-a6be-74f49a860eb7 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 172.3GB: boot/grub/core.img
 175.6GB: boot/grub/grub.cfg
 174.1GB: boot/initrd.img-2.6.32-25-generic
 175.0GB: boot/initrd.img-2.6.35-22-generic
 172.3GB: boot/vmlinuz-2.6.32-25-generic
 172.3GB: boot/vmlinuz-2.6.35-22-generic
 175.0GB: initrd.img
 174.1GB: initrd.img.old
 172.3GB: vmlinuz
 172.3GB: vmlinuz.old

==================== sdb: Location of files loaded by Grub: ====================


    ??GB: initrd.gz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200
```

---

### Post by olayak on 2010-11-02
I didn"t end up installing a 3rd version, since I saw your post.  But when I try to run sudo update-grub I get a message that says```
 /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?). 
```

---

### Post by olayak on 2010-11-02
I'll try what you said about gparted and let you know how it goes. Thanks!

---

