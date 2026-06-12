---
title: "cannot boot from external hard drive but can restart and boot from it"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by beew on 2010-10-03
Hello,

I had an installation of Ubuntu on an external hard disk. I used to be able to plug it into my dell laptop (and other computers) and boot from it so I had a portable system. Now the other day the thing died (the disk is old and damaged) so I bought a new one and install Ubuntu in it just as before. I use my Dell laptop and a live usb to do the installation (the Dell also has Ubuntu installed in it) Everything goes smoothly but it seems that I can't boog directly from this new external installation any more, at least for the Dell using which this installation was created,---I haven't a chance to check with other computers yet.

On a flesh start the dell always boots into the internal harddrive even when this external one is plugged in  (yes. I check the boot sequence in  the BIOs. It is still set to give boot priority to usb storage device as it was before) But I would be able to boot from the external one if I boot into the internal Ubuntu installation first and then "restart" with the external drive plugged in.

---

### Post by beew on 2010-10-03
Yep, I can boot from it with another machine just like before. Only in the Dell I have to boot into the internal installation first and then restart in order to get into this external one. I think it probably has something to do with grub.

---

### Post by Hippytaff on 2010-10-03
I think I remember reading the need to format an external harddrive as ext3, but Im ight be barking up the wrong tree

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by beew on 2010-10-03
> **Hippytaff said:**
> I think I remember reading the need to format an external harddrive as ext3, but Im ight be barking up the wrong tree

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Thanks for the response but psychocat's tutorial has nothing to do with my problem. ;) I am not trying to create a /home partition (as an aside, I tried to create a separate /home partition following that tutorial a while back and it turned out really badly, had to do a clean install( he didn't really explain what "find . -depth -print0 | cpio --null --sparse -pvd /new/" was supposed to do and it apparently generated a lot of errors that the OS couldn't recover from. But to be fair he did make the disclaimer that this was outdated :))

---

### Post by presence1960 on 2010-10-03
with your external plugged in to the lappie do this:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by beew on 2010-10-03
Hi,

Just run the boot info script and here is the result.

OK, I should have pasted the content instead.

 [QUOTE]Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    76,324,814    76,324,752   7 HPFS/NTFS
/dev/sda2          76,324,864   105,621,503    29,296,640  83 Linux
/dev/sda3         105,623,550   156,299,263    50,675,714   5 Extended
/dev/sda5         105,623,552   152,395,775    46,772,224  83 Linux
/dev/sda6         152,397,824   156,299,263     3,901,440  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    39,063,551    39,061,504  83 Linux
/dev/sdb2          39,065,598   117,188,607    78,123,010   5 Extended
/dev/sdb5          39,065,600   113,283,071    74,217,472  83 Linux
/dev/sdb6         113,285,120   117,188,607     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AA0C1FA30C1F6A19                       ntfs                                     
/dev/sda2        23a71713-5de6-455b-98dc-d28675c25c46   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        f09c7e78-0011-4048-ad9b-cfa34daed283   ext3                                     
/dev/sda6        c5fb6ab0-b621-49f3-9584-e9f8d396ce09   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8b8a6d8e-83b1-4b71-b4ea-a81834354d35   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        dd6de4a7-7399-4cd4-9a42-d6943ec296be   ext4                                     
/dev/sdb6        401f7d9b-bdfd-4527-8074-338d88f3fa20   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb5        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set aa0c1fa30c1f6a19
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=23a71713-5de6-455b-98dc-d28675c25c46 /               ext3    errors=remount-ro 0

---

### Post by beew on 2010-10-03
Opps sorry, should have pasted the content instead

> Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    76,324,814    76,324,752   7 HPFS/NTFS
/dev/sda2          76,324,864   105,621,503    29,296,640  83 Linux
/dev/sda3         105,623,550   156,299,263    50,675,714   5 Extended
/dev/sda5         105,623,552   152,395,775    46,772,224  83 Linux
/dev/sda6         152,397,824   156,299,263     3,901,440  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    39,063,551    39,061,504  83 Linux
/dev/sdb2          39,065,598   117,188,607    78,123,010   5 Extended
/dev/sdb5          39,065,600   113,283,071    74,217,472  83 Linux
/dev/sdb6         113,285,120   117,188,607     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AA0C1FA30C1F6A19                       ntfs                                     
/dev/sda2        23a71713-5de6-455b-98dc-d28675c25c46   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        f09c7e78-0011-4048-ad9b-cfa34daed283   ext3                                     
/dev/sda6        c5fb6ab0-b621-49f3-9584-e9f8d396ce09   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8b8a6d8e-83b1-4b71-b4ea-a81834354d35   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        dd6de4a7-7399-4cd4-9a42-d6943ec296be   ext4                                     
/dev/sdb6        401f7d9b-bdfd-4527-8074-338d88f3fa20   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb5        /home                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set aa0c1fa30c1f6a19
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=23a71713-5de6-455b-98dc-d28675c25c46 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=f09c7e78-0011-4048-ad9b-cfa34daed283 /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=c5fb6ab0-b621-49f3-9584-e9f8d396ce09 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  48.1GB: boot/grub/core.img
  48.1GB: boot/grub/grub.cfg
  48.1GB: boot/initrd.img-2.6.32-25-generic
  48.2GB: boot/vmlinuz-2.6.32-25-generic
  48.1GB: initrd.img
  48.2GB: vmlinuz

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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 8b8a6d8e-83b1-4b71-b4ea-a81834354d35
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 8b8a6d8e-83b1-4b71-b4ea-a81834354d35
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8b8a6d8e-83b1-4b71-b4ea-a81834354d35
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8b8a6d8e-83b1-4b71-b4ea-a81834354d35 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8b8a6d8e-83b1-4b71-b4ea-a81834354d35
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8b8a6d8e-83b1-4b71-b4ea-a81834354d35 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8b8a6d8e-83b1-4b71-b4ea-a81834354d35
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 8b8a6d8e-83b1-4b71-b4ea-a81834354d35
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set aa0c1fa30c1f6a19
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro single
    initrd /boot/initrd.img-2.6.32-25-generic
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=8b8a6d8e-83b1-4b71-b4ea-a81834354d35 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc5 during installation
UUID=dd6de4a7-7399-4cd4-9a42-d6943ec296be /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=c5fb6ab0-b621-49f3-9584-e9f8d396ce09 none            swap    sw              0       0
# swap was on /dev/sdc6 during installation
UUID=401f7d9b-bdfd-4527-8074-338d88f3fa20 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.6GB: boot/grub/core.img
   2.5GB: boot/grub/grub.cfg
   4.7GB: boot/initrd.img-2.6.32-25-generic
  17.7GB: boot/vmlinuz-2.6.32-25-generic
   4.7GB: initrd.img
  17.7GB: vmlinuz

---

### Post by presence1960 on 2010-10-03
```
Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #2 for /boot/grub.
=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in
partition #1 for /boot/grub.

sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 10.04.1 LTS
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sda5: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System:
Boot files/dirs:

sda6: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

sdb1: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 10.04.1 LTS
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sdb5: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System:
Boot files/dirs:

sdb6: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 * 63 76,324,814 76,324,752 7 HPFS/NTFS
/dev/sda2 76,324,864 105,621,503 29,296,640 83 Linux
/dev/sda3 105,623,550 156,299,263 50,675,714 5 Extended
/dev/sda5 105,623,552 152,395,775 46,772,224 83 Linux
/dev/sda6 152,397,824 156,299,263 3,901,440 82 Linux swap / Solaris


Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sdb1 * 2,048 39,063,551 39,061,504 83 Linux
/dev/sdb2 39,065,598 117,188,607 78,123,010 5 Extended
/dev/sdb5 39,065,600 113,283,071 74,217,472 83 Linux
/dev/sdb6 113,285,120 117,188,607 3,903,488 82 Linux swap / Solaris


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL

/dev/sda1 AA0C1FA30C1F6A19 ntfs
/dev/sda2 23a71713-5de6-455b-98dc-d28675c25c46 ext3
/dev/sda3: PTTYPE="dos"
/dev/sda5 f09c7e78-0011-4048-ad9b-cfa34daed283 ext3
/dev/sda6 c5fb6ab0-b621-49f3-9584-e9f8d396ce09 swap
/dev/sda: PTTYPE="dos"
/dev/sdb1 8b8a6d8e-83b1-4b71-b4ea-a81834354d35 ext4
/dev/sdb2: PTTYPE="dos"
/dev/sdb5 dd6de4a7-7399-4cd4-9a42-d6943ec296be ext4
/dev/sdb6 401f7d9b-bdfd-4527-8074-338d88f3fa20 swap
/dev/sdb: PTTYPE="dos"

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

/dev/sdb1 / ext4 (rw,errors=remount-ro)
/dev/sdb5 /home ext4 (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
linux /boot/vmlinuz-2.6.32-25-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro quiet splash
initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
echo 'Loading Linux 2.6.32-25-generic ...'
linux /boot/vmlinuz-2.6.32-25-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set aa0c1fa30c1f6a19
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda2 during installation
UUID=23a71713-5de6-455b-98dc-d28675c25c46 / ext3 errors=remount-ro 0 1
# /home was on /dev/sda5 during installation
UUID=f09c7e78-0011-4048-ad9b-cfa34daed283 /home ext3 defaults 0 2
# swap was on /dev/sda6 during installation
UUID=c5fb6ab0-b621-49f3-9584-e9f8d396ce09 none swap sw 0 0

=================== sda2: Location of files loaded by Grub: ===================


48.1GB: boot/grub/core.img
48.1GB: boot/grub/grub.cfg
48.1GB: boot/initrd.img-2.6.32-25-generic
48.2GB: boot/vmlinuz-2.6.32-25-generic
48.1GB: initrd.img
48.2GB: vmlinuz

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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 8b8a6d8e-83b1-4b71-b4ea-a81834354d35
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 8b8a6d8e-83b1-4b71-b4ea-a81834354d35
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 8b8a6d8e-83b1-4b71-b4ea-a81834354d35
linux /boot/vmlinuz-2.6.32-25-generic root=UUID=8b8a6d8e-83b1-4b71-b4ea-a81834354d35 ro quiet splash
initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 8b8a6d8e-83b1-4b71-b4ea-a81834354d35
echo 'Loading Linux 2.6.32-25-generic ...'
linux /boot/vmlinuz-2.6.32-25-generic root=UUID=8b8a6d8e-83b1-4b71-b4ea-a81834354d35 ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 8b8a6d8e-83b1-4b71-b4ea-a81834354d35
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 8b8a6d8e-83b1-4b71-b4ea-a81834354d35
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set aa0c1fa30c1f6a19
drivemap -s (hd0) ${root}
chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda2)" {
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
linux /boot/vmlinuz-2.6.32-25-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro quiet splash
initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda2)" {
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 23a71713-5de6-455b-98dc-d28675c25c46
linux /boot/vmlinuz-2.6.32-25-generic root=UUID=23a71713-5de6-455b-98dc-d28675c25c46 ro single
initrd /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sdc1 during installation
UUID=8b8a6d8e-83b1-4b71-b4ea-a81834354d35 / ext4 errors=remount-ro 0 1
# /home was on /dev/sdc5 during installation
UUID=dd6de4a7-7399-4cd4-9a42-d6943ec296be /home ext4 defaults 0 2
# swap was on /dev/sda6 during installation
UUID=c5fb6ab0-b621-49f3-9584-e9f8d396ce09 none swap sw 0 0
# swap was on /dev/sdc6 during installation
UUID=401f7d9b-bdfd-4527-8074-338d88f3fa20 none swap sw 0 0

=================== sdb1: Location of files loaded by Grub: ===================


17.6GB: boot/grub/core.img
2.5GB: boot/grub/grub.cfg
4.7GB: boot/initrd.img-2.6.32-25-generic
17.7GB: boot/vmlinuz-2.6.32-25-generic
4.7GB: initrd.img
17.7GB: vmlinuz 
```

Next time use the # sign in the tool bar not the quote function so it looks like the above.

I think part of your problem is one disk has ubuntu on an ext 3 file system and the other disk has ubuntu on ext 4. Ext 4 can read/write to ext 3, but extension 3 has no access to ext 4 file systems.

---

### Post by jtarin on 2010-10-03
[Filesystem conversion could be thought about.]("https://help.ubuntu.com/community/ConvertFilesystemToExt4")

---

### Post by beew on 2010-10-03
Presence1960

Thanks for the tips about posting long logs. :-)

> I think part of your problem is one disk has ubuntu on an ext 3 file system and the other disk has ubuntu on ext 4. Ext 4 can read/write to ext 3, but extension 3 has no access to ext 4 file systems.

Sorry for being dense. I can't see how that has to do with booting. This external hdd boots from windows machines just fine, they can read neither ext3 nor ext4.

---

### Post by beew on 2010-10-04
I brought up the one time boot menu on fresh start up (not restart, the laptop boots into the external disk fine on restart) and noticed that the external drive was not even on the boot menu. It only listed the internal hard drive.  It was as though the BIOS didn't detect the external drive even though the light on the external hard drive was flashing. Does it make any sense?

---

