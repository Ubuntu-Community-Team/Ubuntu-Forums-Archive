---
title: "Add GRUB Entry"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by pi3.1415926535... on 2011-03-14
I have just installed Fuduntu from the live DVD, the installer said there was a problem, but all of the files seem to be in the partition. I then updated GRUB, and it found Fuduntu. Though when I rebooted my computer there was no entry for Fuduntu, I then went to GRUB Customizer, which does not show an entry for Fuduntu either. Is there some way I can make GRUB add the entry automatically, or will I have to edit the file manually.

Thank you

---

### Post by andrewthomas on 2011-03-14
Go to 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

follow the instructions and post the results with your reply

---

### Post by pi3.1415926535... on 2011-03-14
Here is the result of the script:
```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Windows Vista/7
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fuduntu release 14 (Laughin) 
                       Kernel on an ()
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sda2         209,717,248   467,388,415   257,671,168   5 Extended
/dev/sda5         209,728,575   232,300,543    22,571,969   7 HPFS/NTFS
/dev/sda6         240,640,000   463,194,111   222,554,112  83 Linux
/dev/sda7         463,196,160   467,388,415     4,192,256  82 Linux swap / Solaris
/dev/sda8         232,302,592   240,637,951     8,335,360  83 Linux
/dev/sda3         467,388,416   488,359,935    20,971,520  1b Hidden W95 FAT32
/dev/sda4         488,359,936   488,392,064        32,129  ef EFI (FAT-12/16/32)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F8126B77126B3A30                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        066C-CC6C                              vfat                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        2C9C24560A3D23C4                       ntfs                                     
/dev/sda6        0a48bbc5-11fe-403c-b558-2c5ff180896c   ext3                                     
/dev/sda7        21e847b6-4b90-4a2d-a542-68041501e362   swap                                     
/dev/sda8        b23b6092-7443-49ee-a141-b2ee3e161308   ext3       _Fuduntu-i386-Li              
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro,user_xattr,commit=0)
/dev/sda1        /media/_                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/sda5              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/menu.lst: ===========================

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows 7
root (hd1,2)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 0a48bbc5-11fe-403c-b558-2c5ff180896c
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 0a48bbc5-11fe-403c-b558-2c5ff180896c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 0a48bbc5-11fe-403c-b558-2c5ff180896c
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=0a48bbc5-11fe-403c-b558-2c5ff180896c ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 0a48bbc5-11fe-403c-b558-2c5ff180896c
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=0a48bbc5-11fe-403c-b558-2c5ff180896c ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 7" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set f8126b77126b3a30
	chainloader +1
}
menuentry "Windows 7 (recovery mode)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 066c-cc6c
	chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
. /boot/grub/themes/sora/clean/theme.cfg
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda1	/media/_	ntfs	auto,defaults,nls=utf8,umask=0222	0	0
/dev/sda5	/media/sda5	ntfs	auto,defaults,nls=utf8,umask=0222	0	0
/dev/sda7	none		swap	sw	0	0
# Commented out by Dropbox
# UUID=	/	ext3	errors=remount-ro	0	1
UUID=	none	swap	sw	0	0
/mnt/512Mb.swap  none  swap  sw  0 0
UUID= / ext3 errors=remount-ro,user_xattr 0 1

=================== sda6: Location of files loaded by Grub: ===================


 193.1GB: boot/grub/core.img
 193.1GB: boot/grub/grub.cfg
 193.1GB: boot/grub/menu.lst
 193.1GB: boot/initrd.img-2.6.35-27-generic
 193.1GB: boot/vmlinuz-2.6.35-27-generic
 193.1GB: initrd.img
 193.1GB: vmlinuz

=============================== sda8/etc/fstab: ===============================

/dev/root  /         ext3    defaults,noatime 0 0
devpts     /dev/pts  devpts  gid=5,mode=620   0 0
tmpfs      /dev/shm  tmpfs   defaults         0 0
proc       /proc     proc    defaults         0 0
sysfs      /sys      sysfs   defaults         0 0
tmpfs /tmp     tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=0755 0 0
```

Thank you

---

### Post by pi3.1415926535... on 2011-03-16
It seems to recognize that the Fuduntu release is there, so how do I make GRUB show it?

Thank you

---

### Post by drs305 on 2011-03-16
I am not familiar with Fuduntu but if you look at what Grub2 finds in sda8 it doesn't include any kernel/initrd or boot files. I don't understand the "Kernel on a ()" part. The only thing it sees is the fstab file. I expect that is why it can't generate a workable menuentry for it.

You could mount the Fuduntu partition and inspect it to see if you can find the necessary boot files (I assume vmlinuz and initrd files in /boot). 

It may be why you got the failure message during the installation.

---

### Post by pi3.1415926535... on 2011-03-16
I did not see those files, I assumes that means that I should re-install.

Thank you

---

### Post by gmargo on 2011-03-17
An almost related question: Does anyone know how to get the Fuduntu LiveDVD onto a USB stick?  usb-creator only works with casper-based .iso images, of which Fuduntu is not. (I wanted to install it on my netbook, which has no optical drive.)

---

### Post by andrewthomas on 2011-03-17
> **gmargo said:**
> An almost related question: Does anyone know how to get the Fuduntu LiveDVD onto a USB stick?  usb-creator only works with casper-based .iso images, of which Fuduntu is not. (I wanted to install it on my netbook, which has no optical drive.)
Try using dd to create the image

 To install, first ensure the USB device is **unmounted** and then issue the following command:

```
 $ dd if=image.iso of=/dev/sd[x]
```where ''image.iso'' is the path to the iso file and ''/dev/sd[x]'' is your USB device.

---

### Post by gmargo on 2011-03-17
> how to get the Fuduntu LiveDVD onto a USB stick? Answering my own question... The Fuduntu DVD includes a script to do just that.  It's described in this Fuduntu forum post:

[http://www.fuduntu.org/forum/viewtopic.php?f=5&t=4](http://www.fuduntu.org/forum/viewtopic.php?f=5&t=4)

I have successfully booted the LiveUSB but have not attempted installation yet.

---

