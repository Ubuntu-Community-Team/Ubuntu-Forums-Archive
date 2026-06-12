---
title: "Windows complains: &quot;BOOTMGR is missing&quot;"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by vmsda on 2010-09-17
After re-arranging my partitioning with SystemRescueCD, I ran into a problem, since Windows 7 will not boot and issues the subject message. Two 10.04 Linux systems have no problem at all, running from their own partitions.

Here is the output of fdisk -l:```


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              14       16864   135355657+  83  Linux
/dev/sda2   *           1          13      104391    7  HPFS/NTFS
/dev/sda3           16878       23258    51255382+   7  HPFS/NTFS
/dev/sda4           23259       38913   125748787+   5  Extended
/dev/sda5           30622       38913    66605490   83  Linux
/dev/sda6           23260       29926    53552646   83  Linux
/dev/sda7           29927       30621     5582556   82  Linux swap / Solaris
```

/dev/sda1 is my home partition.

Any ideas on how to solve the problem? I rarely use Windows, but I want it operational.  Thanks in advance for your ideas.

---

### Post by 2uk_ on 2010-09-17
Try:

```
sudo os-prober

sudo update-grub
```

I can't remember if I did that in live CD, or in the linux operating system though...
either way, it worked for me.
But that was when Grub only recognised the one partition

---

### Post by cj.surrusco on 2010-09-17
It *could* be that grub is not detecting Windows properly, so you would want to try running 'sudo update-grub' first, but chances are, you need to reinstall the Windows bootloader. You would need to boot into the Windows 7 install CD and choose the option to fix the bootloader.

---

### Post by wilee-nilee on 2010-09-17
If none of the suggested methods get you in shape, post the boot scrip in my signature in code tags as described if you can. This will give us a lot of information that is pertinent.

---

### Post by ipey on 2010-09-17
Maybe reinstalling the MBR using installation dvd will do. This tutorial might be useful:
[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html) :)

---

### Post by vmsda on 2010-09-18
Thank you all for your suggestions, which I followed.

1. 2uk's was the simplest to implement, but unfortunately it did not solve the problem.

2. Next was wilee-nilee's, and here is the output from his script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1             208,845   270,920,159   270,711,315  83 Linux
/dev/sda2    *             63       208,844       208,782   7 HPFS/NTFS
/dev/sda3         271,129,005   373,639,769   102,510,765   7 HPFS/NTFS
/dev/sda4         373,639,770   625,137,344   251,497,575   5 Extended
/dev/sda5         491,926,365   625,137,344   133,210,980  83 Linux
/dev/sda6         373,655,898   480,761,189   107,105,292  83 Linux
/dev/sda7         480,761,253   491,926,364    11,165,112  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6623b0f2-45f9-4553-86fd-0ea9971740ef   ext4                                     
/dev/sda2        295EAD2908A7C06A                       ntfs                                     
/dev/sda3        7620AC5A20AC22DB                       ntfs       eMachines                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c1b36af9-09b1-49af-a48c-af6910bcb351   ext4                                     
/dev/sda6        9a74f174-35b5-4ea2-9cf3-74d4073e9eec   ext4                                     
/dev/sda7        5d1bf418-cbe0-4f95-a636-24d78cdcb388   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set c1b36af9-09b1-49af-a48c-af6910bcb351
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
search --no-floppy --fs-uuid --set c1b36af9-09b1-49af-a48c-af6910bcb351
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c1b36af9-09b1-49af-a48c-af6910bcb351
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=c1b36af9-09b1-49af-a48c-af6910bcb351 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c1b36af9-09b1-49af-a48c-af6910bcb351
	echo	'Loading Linux 2.6.32-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=c1b36af9-09b1-49af-a48c-af6910bcb351 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c1b36af9-09b1-49af-a48c-af6910bcb351
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c1b36af9-09b1-49af-a48c-af6910bcb351
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 4ec0aabac0aaa7a3
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro single
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro single
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro single
	initrd /boot/initrd.img-2.6.31-20-generic
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
UUID=c1b36af9-09b1-49af-a48c-af6910bcb351 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=6623b0f2-45f9-4553-86fd-0ea9971740ef /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=5d1bf418-cbe0-4f95-a636-24d78cdcb388 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 316.4GB: boot/grub/core.img
 254.2GB: boot/grub/grub.cfg
 316.5GB: boot/initrd.img-2.6.32-24-generic-pae
 316.4GB: boot/vmlinuz-2.6.32-24-generic-pae
 316.5GB: initrd.img
 316.4GB: vmlinuz

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
search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
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
search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9a74f174-35b5-4ea2-9cf3-74d4073e9eec
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c1b36af9-09b1-49af-a48c-af6910bcb351
	linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=c1b36af9-09b1-49af-a48c-af6910bcb351 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set c1b36af9-09b1-49af-a48c-af6910bcb351
	linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=c1b36af9-09b1-49af-a48c-af6910bcb351 ro single
	initrd /boot/initrd.img-2.6.32-24-generic-pae
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
# / was on /dev/sda7 during installation
UUID=9a74f174-35b5-4ea2-9cf3-74d4073e9eec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=5d1bf418-cbe0-4f95-a636-24d78cdcb388 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 191.4GB: boot/grub/core.img
 192.7GB: boot/grub/grub.cfg
 192.9GB: boot/initrd.img-2.6.31-20-generic
 192.9GB: boot/initrd.img-2.6.32-21-generic
 192.8GB: boot/initrd.img-2.6.32-22-generic
 193.1GB: boot/initrd.img-2.6.32-23-generic
 193.2GB: boot/initrd.img-2.6.32-24-generic
 192.8GB: boot/vmlinuz-2.6.31-20-generic
 199.3GB: boot/vmlinuz-2.6.32-21-generic
 191.8GB: boot/vmlinuz-2.6.32-22-generic
 192.6GB: boot/vmlinuz-2.6.32-23-generic
 193.0GB: boot/vmlinuz-2.6.32-24-generic
 193.2GB: initrd.img
 193.1GB: initrd.img.old
 193.0GB: vmlinuz
 192.6GB: vmlinuz.old
```

3. Then I remembered I had already run wilee-nilee's script a few days ago when working with SystemRescueCD and trying to have things under control. So I went looking for the results, and I still had them. The big difference is in /dev/sda2, which used to read like this in Results.txt:
```
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD
```

So now there is nothing under "Boot files/dirs", so I obviously corrupted the partition.

Questions:
1. Do I have to go back to a Win 7 DVD (which I do not have at hand in these days of pre-loaded boxes), or is there some other way to repair /dev/sda2 and fool Windows?

2. If I correct the problem through Windows, won't it corrupt the MBR and render my Linuxes inoperational instead? In this case, I wonder if running 2uk's suggestion might then be the solution.

Thank you again for your patience.

---

### Post by wilee-nilee on 2010-09-18
Your definitely missing those boot files from sda2, good eye. I believe that if you had a install DVD you could reload them, although I'm not familiar with doing that.

Your going to need more qualified help here with the missing stuff. It is also really late where I am and I am going to crash. Usually during the day US time there are several forum members that are on daily that are specialist in this area amongst others, so look for them to reply they probably will.

I didn't look in real detail through the whole script as I am really tired and I want to error on the side of caution here.

---

### Post by candtalan on 2010-09-18
You say that the linux boots are done from their own partitions I think.

Does this mean that you only booted Windows 7 from its normal boot manager? For example, my usual method of mutibooting  uses the grub which comes with ubuntu or distro and the default method is to let grub pick up and include the Windows booting also. 

In my case if there is a minor booting problem I can run the last installed Ubuntu (which took over the active grub2 in the machine) and do simple things including update-grub, which again picks up Windows if it is present.

If you only ever booted Windows from its own Windows boot loader, then the obvious repair method would be to use a fixmbr or similar windows command (may be different for win7) using a bootable windows cd or whatever. A windows rescue cd is not the same as a windows re install CD, however I do not know if a Windows rescue CD will do what you need.

Alternatively, I wonder if it is possible to re install or reconfigure grub in one of your (Ubuntu) installs so it boots also offering Windows in the Grub startup boot list.

It will be important to know first which versions of Grub you have in the installs. Grub 1 or grub 2 whatever.

hth

---

### Post by vmsda on 2010-09-18
> **candtalan said:**
> You say that the linux boots are done from their own partitions I think. Does this mean that you only booted Windows 7 from its normal boot manager? ...

When I said that my linuxes boot "from their own partitions" I really meant that they are ok with MBR and GRUB as they are configured. By the way, GRUB does recognize that Win7 is present, it gives me the option to boot it, but when I choose it things fail as described before. So, obviously, it is Win7 which is complaining.

Some history: everything was running ok, including Win7, until I decided that I wanted to have a much larger /home in /dev/sda1. To accommodate this requirement I naturally had to move /dev/sda2 down, and Win7 did not like it; so I re-arranged things to have /dev/sda2 back in the beginning of the disk. But the problem persisted, and thanks to wilee-nilee's script,  I am concluding that when I moved down /dev/sda2, I did something that corrupted it; moving it back did not help.

One doubt: I am here talking about /dev/sda2 back and forth, and am not even sure whether Win7 really needs a boot partition all its own; I was just assuming it does, from the way things worked before.

---

### Post by Mark Phelps on 2010-09-18
> **vmsda said:**
> I am concluding that when I moved down /dev/sda2, I did something that corrupted it; moving it back did not help.
So, have you booted from a Win7 Repair CD or Install DVD and run Startup Repair to fix the Win7 boot loader problems?

> One doubt: I am here talking about /dev/sda2 back and forth, and am not even sure whether Win7 really needs a boot partition all its own; I was just assuming it does, from the way things worked before.

It doesn't NEED a separate boot partition.  It generally comes that way on preinstalled machines because OEM vendors choose to do that.  It will actually work fine with the boot folder and program contained inside the OS partition.

---

### Post by vmsda on 2010-09-18
I do not have any Win7 cd/dvd, so I have not tried what you suggest.

One other strange thing: the initial GRUB screen no longer gives me the Win7 loader option, ie. I am no longer able to get that "BOOTMGR is missing" message! I tried "sudo update-grub", but it did not solve the problem.

---

### Post by vmsda on 2010-09-23
> **Mark Phelps said:**
> So, have you booted from a Win7 Repair CD or Install DVD and run Startup Repair to fix the Win7 boot loader problems?

It doesn't NEED a separate boot partition.  It generally comes that way on preinstalled machines because OEM vendors choose to do that.  It will actually work fine with the boot folder and program contained inside the OS partition.

Ok, I managed to get hold of an Install DVD, ran Startup Repair, then "sudo update-grub" and everything ran smoothly as expected.

But now, a partitition id (SD2) is being wasted just for the sake of the Win7 loader (Win7 itself is in SD3). So my question now is: what do I have to do in order to make Win7 boot from SD3?

Thank you again for your support.

---

### Post by Mark Phelps on 2010-09-23
> **vmsda said:**
> But now, a partitition id (SD2) is being wasted just for the sake of the Win7 loader (Win7 itself is in SD3). So my question now is: what do I have to do in order to make Win7 boot from SD3?

The easiest way to do this is to download the EasyBCD app from the NeoSmart Technology forums and install it.  When you launch it, it provides an option of moving the Win7 bootloader stuff to a different partition.  In this case, you could move it to your Win7 OS partition.

If you want details, you should check in the NeoSmart Technology forums.  They have FAQs that deal with this in detail.

---

### Post by vmsda on 2010-09-23
> **Mark Phelps said:**
> The easiest way to do this is to download the EasyBCD app from the NeoSmart Technology forums and install it.  When you launch it, it provides an option of moving the Win7 bootloader stuff to a different partition.  In this case, you could move it to your Win7 OS partition.

If you want details, you should check in the NeoSmart Technology forums.  They have FAQs that deal with this in detail.

Unfortunately, it did not turn out to be "the easiest way". After getting EasyBCD and the advice, I did as directed and it turns out that Win7 destroyed the MBR and now I do not have access to the linux partitions. EasyBCD has an option to install GRUB2 in the MBR and configure it automatically, but all it does is to create two entries besides Win7: a so-called Neogrub bootloader and a Neosmart Linux; when choosing either of these, all you get is a message saying "try (hd0,0): ext2", and action stops there. Ridiculous.

Where can I go from here? Thank in advance for suggestions.

---

### Post by JC Cheloven on 2010-09-23
> **vmsda said:**
> Where can I go from here? Thank in advance for suggestions.
Sorry if I jump here with that may look as a simplistic approach, but I see you've spent almost a whole week with this _windows_ problem. I can't resist: 
--> At some point, you should consider re-installing everything in a way that is known to work <--
A first primary partition for windows, and an extended partition containing all other partitions you may need could be an example.

EDIT: Some explanation on my point. Given the following:[INDENT]- A big share of linux installing problems are actually windows problems, if it is around
- Even extending "by the right" a win2 partition may cause boot problems. Happened to me. 
- Installing win2 first, in the first partition, and don't touching it, is (hopefully) "known to work"
[/INDENT]
You may prosecute your problem, and surely you'll find eventually a fix. But, is it worth? You could have already reinstalled everything x3 so far. It's a windows problem actually, which you "rarely use" anyway. So I'd take the easy way with this (btw, did you considered virtualization inside ubuntu?), and spend your time in fixing possible problems of the OS you use primarily, if any.

---

### Post by vmsda on 2010-09-24
Thank you for your suggestions, Cheloven. But ...

I can spend months with a Windows problem since I rarely use it :guitar:.

Yesterday, when Win7 mucked up the MBR, I spent a total of one hour without access to my Linuxes. I went into the Ubuntu forums, found out how to reconstruct the MBR from the Ubuntu LiveCD, rebooted, updated Grub, and lo & behold, now I can boot at will from any of the OS on the disk, and saved that partition id in the bargain.

Although I understand the temptation to make a clean breast of things when facing a persistent problem, I tend to favour the workaround approach: one may waste more time but, if successful, it is far more instructive.

Cheers and thanks to everybody for the help and suggestions.

---

### Post by JC Cheloven on 2010-09-24
> **vmsda said:**
> one may waste more time but, if successful, it is far more instructive.
Ok, agree :)

So you marked this as solved, but ... what did you do exactly? Your explanation suggests that you did the standard reinstallation of grub2 from live CD ([this one]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")). Perhaps "method 3" using chroot? And, can you also boot windows now?

It would be nice to know for future users looking at this thread. 
Glad you solved it anyway

JC

---

### Post by vmsda on 2010-09-24
I did not use Method 3, I used the first one, SIMPLEST - Copy GRUB 2 Files from the LiveCD. And, as I said, I can now boot Win7 or any of the Linux systems.

---

