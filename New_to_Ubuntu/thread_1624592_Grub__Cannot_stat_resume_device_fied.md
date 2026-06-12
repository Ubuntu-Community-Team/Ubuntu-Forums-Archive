---
title: "Grub:  Cannot stat resume device fied"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by Lefaid on 2010-11-17
Hey, I have been playing around with Ubuntu for the last 3 weeks kind of making a mess of my computer.  I was wondering if I could get some help to make my experience a little more enjoyable.  I should add that I am no expert on computers so some of my observations may not be vaild.

Basically, when I start the computer I get your normal options for booting.  When I select the one with my working version of Ubuntu on it, I get this error

```
resume: libgcrypt version: 1.4.5
resume:  Could not stat the resume device file '/dev/sda8'
Please type in the full path name to try again or press ENTER to boot the system
```

Generally I can type in the partition name of where my working version of Ubuntu is (or strangely enough where Windows 7 is) and it will boot properly.  I would like to fix it so I don't have to type /dev/sda5 (or /dev/sda1).

This error started after I gave the memory inside an empty partition that was to the left of Windows 7 to Windows 7 using a program in Windows 7.  After that I could not boot the computer and went into grub rescue mode.  I figured out how to manually boot the computer and did so.  After that I reinstalled grub or something and this problem occured.

I should also add that really there shouldn't be an sda8.  According to my disk utility in Ubuntu I have sda1 with Windows 7 on it, sda2 which is an extended one containing 3 Linux partitions itself, sda5, sda6, and sda7.  sda5 has my working version of Linux on it, sda6 has the swap on it, and sda7 and empty 40GB partition.

I have reinstalled it a few times though that hasn't fixed the problem at all.  I really want to be able to not only instantly start Ubuntu but also edit the menu itself, just for the fun of it.  Can any of you help me?   really don't wnat to have to reformat my entire drive and thus subsequently reinstalling Windows 7.  Thanks

---

### Post by Hippytaff on 2010-11-18
Hi
 
If you run this boot script and post the results here, people will be better able to help
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Lefaid on 2010-11-18
Thanks for the suggestion, here are the results:

```
        Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
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
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda9: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   468,037,709   468,037,647   7 HPFS/NTFS
/dev/sda2         468,049,919   625,141,759   157,091,841   f W95 Ext d (LBA)
/dev/sda5         468,049,920   543,547,391    75,497,472  83 Linux
/dev/sda6         543,549,440   546,869,247     3,319,808  82 Linux swap / Solaris
/dev/sda7         546,875,392   621,836,287    74,960,896  83 Linux
Invalid MBR Signature found
/dev/sda8     ? 4,763,017,214 4,763,017,213                   Unknown
/dev/sda9     ? 4,763,017,214 4,763,017,213                   Unknown

/dev/sda8 ends after the last sector of /dev/sda
the logical partition /dev/sda8 is not contained in the extended partition /dev/sda2
/dev/sda9 ends after the last sector of /dev/sda
the logical partition /dev/sda9 is not contained in the extended partition /dev/sda2

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        01CB7A3F2A378100                       ntfs       OS                            
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f765f6fd-795d-43b5-a34a-f94f43a930ea   ext4                                     
/dev/sda6        05e0c08b-2d10-4f87-9661-31791aa8ef74   swap                                     
/dev/sda7        95b1e916-1957-42cf-8aca-8b9b48c3a5af   ext4       New Volume                    
/dev/sda: PTTYPE="dos" 
error: /dev/sda8: No such file or directory
error: /dev/sda9: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /media/New Volume        ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set f765f6fd-795d-43b5-a34a-f94f43a930ea
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set f765f6fd-795d-43b5-a34a-f94f43a930ea
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f765f6fd-795d-43b5-a34a-f94f43a930ea
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f765f6fd-795d-43b5-a34a-f94f43a930ea ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f765f6fd-795d-43b5-a34a-f94f43a930ea
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f765f6fd-795d-43b5-a34a-f94f43a930ea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f765f6fd-795d-43b5-a34a-f94f43a930ea
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f765f6fd-795d-43b5-a34a-f94f43a930ea
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 01cb7a3f2a378100
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
# / was on /dev/sda7 during installation
UUID=f765f6fd-795d-43b5-a34a-f94f43a930ea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=05e0c08b-2d10-4f87-9661-31791aa8ef74 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 265.5GB: boot/grub/core.img
 257.7GB: boot/grub/grub.cfg
 240.6GB: boot/initrd.img-2.6.35-22-generic
 265.6GB: boot/vmlinuz-2.6.35-22-generic
 240.6GB: initrd.img.old
 265.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda8


Unknown BootLoader  on sda9



=============================== StdErr Messages: ===============================

hexdump: /dev/sda8: No such file or directory
hexdump: /dev/sda8: No such file or directory
hexdump: /dev/sda9: No such file or directory
hexdump: /dev/sda9: No such file or directory
```

I gotta say, I have not idea what sda9 is.

---

### Post by Hippytaff on 2010-11-18
I'm guessing sda8 and sda9 are (or contain) bootloaders, don't know for what though. might They be recovery partitions for Windows.

Anyway, looks like grub is looking to boot sda8, and it needs to point at the ubuntu partition, but I really am no expert on grub at all. Others here are far more qualified than me to assist yo.

---

### Post by Lefaid on 2010-11-22
Thanks for trying to help.  I should say that after I updated a day or two ago the problem disappeared. I guess there was something wrong with whatever was updated.  Who knows.  Thanks again.

---

