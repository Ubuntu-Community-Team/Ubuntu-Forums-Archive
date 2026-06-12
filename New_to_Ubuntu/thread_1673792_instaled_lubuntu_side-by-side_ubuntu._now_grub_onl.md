---
title: "instaled lubuntu side-by-side ubuntu. now grub only show lubuntu, other OS disappear"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by santhust on 2011-01-22
Hi, thanks in advance.
I installed lubuntu 10.10(to experiment), side by side to my machine, which initially was a dual boot of Ubuntu/Kubuntu 10.10 and Windows Vista. 
Problem: Now the grub gives me option to boot only Lubuntu, and other options, of Ubuntu and Windows Vista are not shown. I have seen that my other "partions" and data therein exists.
I would be very helpful of any help, that would enable to restore the OS options to the grub.
Please ask if any information is needed.
Thanks again.

---

### Post by Quackers on 2011-01-22
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by santhust on 2011-01-22
> **Quackers said:**
> Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Thanks for quick reply. Just attached the required file..

---

### Post by Quackers on 2011-01-22
If you post the contents of the file in code tags it looks like this :-)
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

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

/dev/sda1    *             63   164,489,534   164,489,472   7 HPFS/NTFS
/dev/sda2         164,491,262   488,396,799   323,905,538   5 Extended
/dev/sda5         164,491,264   454,510,107   290,018,844  83 Linux
/dev/sda6         475,168,768   488,396,799    13,228,032  82 Linux swap / Solaris
/dev/sda7         454,510,592   474,177,535    19,666,944  83 Linux
/dev/sda8         474,179,584   475,154,431       974,848  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D4A81E30A81E119A                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        39f21451-811b-4c15-aca4-f6f735f2bc3c   ext4                                     
/dev/sda6        12c3d2b7-6166-45b9-be40-786463ce10d1   swap                                     
/dev/sda7        c6e373c9-3417-43f8-ad0f-0fc4e96ece54   ext4                                     
/dev/sda8        b3be9bb0-a46c-4bf6-a123-80e674c1a519   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d4a81e30a81e119a
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
UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=12c3d2b7-6166-45b9-be40-786463ce10d1 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 232.5GB: boot/grub/core.img
 113.6GB: boot/grub/grub.cfg
 136.9GB: boot/initrd.img-2.6.32-26-generic
 154.1GB: boot/initrd.img-2.6.35-23-generic
 153.7GB: boot/initrd.img-2.6.35-24-generic
 101.4GB: boot/vmlinuz-2.6.32-26-generic
 101.4GB: boot/vmlinuz-2.6.35-23-generic
  95.0GB: boot/vmlinuz-2.6.35-24-generic
 153.7GB: initrd.img
 154.1GB: initrd.img.old
  95.0GB: vmlinuz
 101.4GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=c6e373c9-3417-43f8-ad0f-0fc4e96ece54 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=c6e373c9-3417-43f8-ad0f-0fc4e96ece54 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=c6e373c9-3417-43f8-ad0f-0fc4e96ece54 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=b3be9bb0-a46c-4bf6-a123-80e674c1a519 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 239.5GB: boot/grub/core.img
 235.4GB: boot/grub/grub.cfg
 233.6GB: boot/initrd.img-2.6.35-24-generic-pae
 239.4GB: boot/vmlinuz-2.6.35-24-generic-pae
 233.6GB: initrd.img
 239.4GB: vmlinuz
```

---

### Post by santhust on 2011-01-22
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

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

/dev/sda1    *             63   164,489,534   164,489,472   7 HPFS/NTFS
/dev/sda2         164,491,262   488,396,799   323,905,538   5 Extended
/dev/sda5         164,491,264   454,510,107   290,018,844  83 Linux
/dev/sda6         475,168,768   488,396,799    13,228,032  82 Linux swap / Solaris
/dev/sda7         454,510,592   474,177,535    19,666,944  83 Linux
/dev/sda8         474,179,584   475,154,431       974,848  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D4A81E30A81E119A                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        39f21451-811b-4c15-aca4-f6f735f2bc3c   ext4                                     
/dev/sda6        12c3d2b7-6166-45b9-be40-786463ce10d1   swap                                     
/dev/sda7        c6e373c9-3417-43f8-ad0f-0fc4e96ece54   ext4                                     
/dev/sda8        b3be9bb0-a46c-4bf6-a123-80e674c1a519   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 39f21451-811b-4c15-aca4-f6f735f2bc3c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d4a81e30a81e119a
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
UUID=39f21451-811b-4c15-aca4-f6f735f2bc3c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=12c3d2b7-6166-45b9-be40-786463ce10d1 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 232.5GB: boot/grub/core.img
 113.6GB: boot/grub/grub.cfg
 136.9GB: boot/initrd.img-2.6.32-26-generic
 154.1GB: boot/initrd.img-2.6.35-23-generic
 153.7GB: boot/initrd.img-2.6.35-24-generic
 101.4GB: boot/vmlinuz-2.6.32-26-generic
 101.4GB: boot/vmlinuz-2.6.35-23-generic
  95.0GB: boot/vmlinuz-2.6.35-24-generic
 153.7GB: initrd.img
 154.1GB: initrd.img.old
  95.0GB: vmlinuz
 101.4GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=c6e373c9-3417-43f8-ad0f-0fc4e96ece54 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=c6e373c9-3417-43f8-ad0f-0fc4e96ece54 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c6e373c9-3417-43f8-ad0f-0fc4e96ece54
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=c6e373c9-3417-43f8-ad0f-0fc4e96ece54 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=b3be9bb0-a46c-4bf6-a123-80e674c1a519 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 239.5GB: boot/grub/core.img
 235.4GB: boot/grub/grub.cfg
 233.6GB: boot/initrd.img-2.6.35-24-generic-pae
 239.4GB: boot/vmlinuz-2.6.35-24-generic-pae
 233.6GB: initrd.img
 239.4GB: vmlinuz

```

---

### Post by Quackers on 2011-01-22
Looking at your boot script output I don't see anything for Kubuntu or Lubuntu. Just entries for two Ubuntu 10.10 installations (sda5 and sda7) and one entry for Vista/7 Loader.
Try running ```
sudo update-grub
``` in the terminal and then reboot and see what grub menu shows.

---

### Post by santhust on 2011-01-22
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
```

Kubuntu is not installed separately, but firstly installed ubuntu and the from the synaptic package manage installed kubuntu-desktop, thus giving me option to try kubuntu option at the login screen.

---

### Post by Quackers on 2011-01-22
As you have two installations of Ubuntu 10.10, you have two installations of grub. As such, it would appear that your sda7 installation has control of grub, for the moment. This grub.cfg doesn't pick up Windows or the other Ubuntu.
The sda5 grub.cfg picks up both the other Ubuntu and the Windows loader.
Did you intend on having two installations of Ubuntu 10.10?

---

### Post by santhust on 2011-01-23
> **Quackers said:**
> As you have two installations of Ubuntu 10.10, you have two installations of grub. As such, it would appear that your sda7 installation has control of grub, for the moment. This grub.cfg doesn't pick up Windows or the other Ubuntu.
The sda5 grub.cfg picks up both the other Ubuntu and the Windows loader.
Did you intend on having two installations of Ubuntu 10.10?

The other "ubuntu" is I guess is Lubuntu (unsure as to why Ubuntu appears and Lubuntu nowhere appear in the RESULT.txt), whose installation has caused me this problem.
Preference 1: if it is possible to have both the L/U-buntus and Windows Vista.
Preference 2: if not preference 1, then, as installing Lubuntu was just for experimenting, I won't mind doing away with it, and have my system restored to previous configuration, i.e. ubuntu and Windows Vista only.

---

### Post by nm_geo on 2011-01-23
Quackers I think the sda7 is the Lubuntu.  Strange it also installed another swap file on sda8.  This is exactly why I always install my grub on additional flavors to their own partition and not let them write to the sda.  

How about this idea.. that is if you want Maverick 10.10 to be the primary boot.

```
sudo mount /dev/sda5 /mnt

``````
sudo grub-install --root-directory=/mnt /dev/sda

```sudo update-grub

Reboot 

What do you think?

---

### Post by nm_geo on 2011-01-23
> **santhust said:**
> The other "ubuntu" is I guess is Lubuntu (unsure as to why Ubuntu appears and Lubuntu nowhere appear in the RESULT.txt), whose installation has caused me this problem.
Preference 1: if it is possible to have both the L/U-buntus and Windows Vista.
Preference 2: if not preference 1, then, as installing Lubuntu was just for experimenting, I won't mind doing away with it, and have my system restored to previous configuration, i.e. ubuntu and Windows Vista only.

Yes it is your lubuntu on sda7..

Here is portion of my mess I will show you a Kubuntu that is like your sort of.
```
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 534686216 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4  [COLOR=Red](Kubuntu I added this line)[/COLOR]
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

```

I do have two Nattys for testing purposes.

---

### Post by santhust on 2011-01-23
@nm_geo:  I guess the same i.e. sda7 is Lubuntu.

---

### Post by Quackers on 2011-01-23
That would work nm_geo, but I'm thinking that if the sda7 installation is Lubuntu, it may have installed without os-prober, which has happened once or twice recently.
Santhust, which installation are you booted into at the moment, sda5 or sda7?
If you are in sda7, go to synaptic package manager and enter in the search box "os-prober". When it appears in the main window, does it have a green box to its left (ie is it installed)? If not, please install it then run sudo update-grub again in the terminal.

---

### Post by nm_geo on 2011-01-23
Yes I agree. I wish they would add that sometimes they do like the last two on mine.

Now if you want go back to the grub changing post and read it.

---

### Post by nm_geo on 2011-01-23
> **Quackers said:**
> That would work nm_geo, but I'm thinking that if the sda7 installation is Lubuntu, it may have installed without os-prober, which has happened once or twice recently.
Santhust, which installation are you booted into at the moment, sda5 or sda7?
If you are in sda7, go to synaptic package manager and enter in the search box "os-prober". When it appears in the main window, does it have a green box to its left (ie is it installed)? If not, please install it then run sudo update-grub again in the terminal.

good point Quackers.   I am sure he is booting from sda7 right now that is his problem and it can't see window or maverick.

---

### Post by santhust on 2011-01-23
> **Quackers said:**
> That would work nm_geo, but I'm thinking that if the sda7 installation is Lubuntu, it may have installed without os-prober, which has happened once or twice recently.
Santhust, which installation are you booted into at the moment, sda5 or sda7?
If you are in sda7, go to synaptic package manager and enter in the search box "os-prober". When it appears in the main window, does it have a green box to its left (ie is it installed)? If not, please install it then run sudo update-grub again in the terminal.

At the moment i am booted into sda7 (ruinning Lubuntu on the same machine)
the "os-prober" was not installed; I installed it and ran sudo update-grub. the output is:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Ubuntu 10.10 (10.10) on /dev/sda5
done

```

I noticed that this time ubuntu and windows vista have appeared (opposite to previous run of 'sudo update-grub'). Will rebooting now set the things to order?

---

### Post by nm_geo on 2011-01-23
excellent check back and mark Solved.. 
Nice call Quackers OUT

By the way if you do decide to have primary boot as Maverick you can change the 
Grub boot as I explained earlier.

---

### Post by Quackers on 2011-01-23
I would say so :-)
Hopefully all operating systems should now be choosable from the grub menu, whichever version of grub is in control.

---

### Post by santhust on 2011-01-23
=D>
thanks quackers and nm_geo. Thanks a ton for quick replies.
:guitar: \\:D/

---

