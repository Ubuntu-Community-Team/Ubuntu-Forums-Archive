---
title: "can't boot ubuntu 11.04 after installing fedora 15"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by Pulka on 2011-08-01
Hi.


Decided to try fedora 15 in dual boot with ubuntu 11.04. 

Installed first ubuntu with the following partitions>

/boot
/swap 
/
/home

Then installed Fedora 15 and after that grub doesn't recognize ubuntu
How can i fix this

This is my fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          97      779121   83  Linux
/dev/sda2              98         462     2931862+  82  Linux swap / Solaris
/dev/sda3             463        4109    29294527+  83  Linux
/dev/sda4            4110       19457   123282779+   5  Extended
/dev/sda5            4110       13033    71679994   83  Linux
/dev/sda6           13033       13097      512000   83  Linux
/dev/sda7           13097       19457    51088384   8e  Linux LVM

sda1 - boot partition
sda2 - swap
sda3 - ubuntu root
sda5 - ubuntu home
sda6 - don't know but it has 500mb of size
sda7 - i figure is where fedora is, but in gparted there's a warning that logical volume management is not yet suported

---

### Post by coffeecat on 2011-08-01
This is a common problem. Whereas the Ubuntu installer will detect other Linux operating systems and include them in the grub menu, Fedora will only detect Windows. I can only assume that the Fedora developers can't be bothered to include this fairly basic functionality. But grumbles aside, what you need to do is to edit Fedora's menu.lst file (Fedora still uses legacy grub) to include an Ubuntu entry. Boot into Fedora, open a terminal, su to root, and post the output of these commands:

```
fdisk -lu
blkid
cat /boot/grub/menu.lst
```

We can take advantage of the fact that Ubuntu creates "vmlinuz" and "initrd.img" symlinks to the current kernel in the root of its filesystem. When you post that output, **please** enclose it between [noparse]```
 and 
```[/noparse] tags for legibility. You can use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar for this. With that output I can help you with the editing of Fedora's menu.lst if you want.

---

### Post by amjjawad on 2011-08-01
> **coffeecat said:**
> This is a common problem. Whereas the Ubuntu installer will detect other Linux operating systems and include them in the grub menu, Fedora will only detect Windows. I can only assume that the Fedora developers can't be bothered to include this fairly basic functionality.

Reminds me of the old days :)

I read it some where that with Fedora 16, GRUB2 will be used so hope that will fix the issue but that won't be Fedora, thanks go to GRUB2 :D

---

### Post by Pulka on 2011-08-01
meanwhile i re-installed grub and now i only get a terminal version of grub.

help? :)

---

### Post by coffeecat on 2011-08-01
> **Pulka said:**
> meanwhile i re-installed grub and now i only get a terminal version of grub.

Unfortunate. Ubuntu uses grub2 and Fedora uses legacy grub. I guess you might have mixed and matched, :) and anyway simply re-installing grub was not the answer.

Boot up a live Linux CD. It doesn't matter whether it's Ubuntu or Fedora. Make sure you are connected to the internet and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of your RESULTS.txt file. This will tell us where you went wrong with the grub re-install. It will also give us the output of the commands I posted earlier, so you can forget about those. But as with those commands, **please** enclose the RESULTS.txt contents between [noparse]```
 and 
```[/noparse] tags for legibility. A reminder - you can use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar for this.

Last question: Do you have a Fedora live CD? You may need this.

---

### Post by Pulka on 2011-08-01
Ok, here it is

```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda7: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63     1,558,304     1,558,242  83 Linux
/dev/sda2           1,558,305     7,422,029     5,863,725  82 Linux swap / Solaris
/dev/sda3           7,422,030    66,011,084    58,589,055  83 Linux
/dev/sda4          66,011,146   312,576,704   246,565,559   5 Extended
/dev/sda5          66,011,148   209,371,135   143,359,988  83 Linux
/dev/sda6         209,373,184   210,397,183     1,024,000  83 Linux
/dev/sda7         210,399,232   312,575,999   102,176,768  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        76c0a171-b1d1-46d1-8962-91d7e3d55541   ext4       
/dev/sda2        0517d6ce-f41f-42c9-a0b9-ca947c7efb48   swap       
/dev/sda3        9b63ac15-7a15-41e4-8407-798830674770   ext4       
/dev/sda5        779af84e-92d8-4568-ba4b-cac0dd061700   ext4       
/dev/sda6        b2f2cb27-b772-43d9-ad51-1d060b67bdd6   ext4       
/dev/sda7        5dViJV-h8Nm-7SOV-zmK2-7BYB-kJJ4-Jkcfzy LVM2_member 

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sda1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 9b63ac15-7a15-41e4-8407-798830674770
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 76c0a171-b1d1-46d1-8962-91d7e3d55541
set locale_dir=($root)/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 76c0a171-b1d1-46d1-8962-91d7e3d55541
	linux	/vmlinuz-2.6.38-10-generic root=UUID=9b63ac15-7a15-41e4-8407-798830674770 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 76c0a171-b1d1-46d1-8962-91d7e3d55541
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/vmlinuz-2.6.38-10-generic root=UUID=9b63ac15-7a15-41e4-8407-798830674770 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 76c0a171-b1d1-46d1-8962-91d7e3d55541
	linux	/vmlinuz-2.6.38-8-generic root=UUID=9b63ac15-7a15-41e4-8407-798830674770 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 76c0a171-b1d1-46d1-8962-91d7e3d55541
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/vmlinuz-2.6.38-8-generic root=UUID=9b63ac15-7a15-41e4-8407-798830674770 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 76c0a171-b1d1-46d1-8962-91d7e3d55541
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 76c0a171-b1d1-46d1-8962-91d7e3d55541
	linux16	/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.139411449 = 0.149691904    boot/grub/core.img                             1
   0.151195049 = 0.162344448    grub/core.img                                  1
   0.132857800 = 0.142654976    grub/grub.cfg                                  1
   0.176066875 = 0.189050368    initrd.img-2.6.38-10-generic                   1
   0.148467541 = 0.159415808    initrd.img-2.6.38-8-generic                    2
   0.156589031 = 0.168136192    vmlinuz-2.6.38-10-generic                      1
   0.132522106 = 0.142294528    vmlinuz-2.6.38-8-generic                       1

=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 9b63ac15-7a15-41e4-8407-798830674770
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 9b63ac15-7a15-41e4-8407-798830674770
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=9b63ac15-7a15-41e4-8407-798830674770 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=76c0a171-b1d1-46d1-8962-91d7e3d55541 /boot           ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=779af84e-92d8-4568-ba4b-cac0dd061700 /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sda2 during installation
UUID=0517d6ce-f41f-42c9-a0b9-ca947c7efb48 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  27.665827751 = 29.705956352   boot/grub/core.img                             1
  27.665831566 = 29.705960448   boot/grub/grub.cfg                             1

============================= sda6/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,5)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_fieldslaptop-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,5)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.8-35.fc15.i686)
	root (hd0,5)
	kernel /vmlinuz-2.6.38.8-35.fc15.i686 ro root=/dev/mapper/vg_fieldslaptop-lv_root rd_LVM_LV=vg_fieldslaptop/lv_root rd_LVM_LV=vg_fieldslaptop/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=pt-latin1 rhgb quiet
	initrd /initramfs-2.6.38.8-35.fc15.i686.img
title Fedora (2.6.38.6-26.rc1.fc15.i686)
	root (hd0,5)
	kernel /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_fieldslaptop-lv_root rd_LVM_LV=vg_fieldslaptop/lv_root rd_LVM_LV=vg_fieldslaptop/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=pt-latin1 rhgb quiet
	initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  99.852053642 = 107.215326208  grub/grub.conf                                 1
  99.852053642 = 107.215326208  grub/menu.lst                                  1
  99.850473404 = 107.213629440  grub/stage2                                    1
  99.867722511 = 107.232150528  initramfs-2.6.38.6-26.rc1.fc15.i686.img        2
  99.887136459 = 107.252996096  initramfs-2.6.38.8-35.fc15.i686.img            2
  99.848518372 = 107.211530240  vmlinuz-2.6.38.6-26.rc1.fc15.i686              1
  99.871752739 = 107.236477952  vmlinuz-2.6.38.8-35.fc15.i686                  1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by bodhi.zazen on 2011-08-01
It is easiest to re-install grub 1 for Fedora and then chainload Ubuntu.

Add a stanza like this:

```
title Ubuntu 11.04
root (hd0,x)
kernel /grub/core.img
boot
```

Just be sure to specify the correct partition for root (hd0,x)

Edit OIC you posted =)

Well, assuming ubuntu is in sda3, root (hd0,2)

---

### Post by Pulka on 2011-08-01
And how can i edit the grub file? Already tried with fedora live cd but i can't seem to acess grub file

---

### Post by bodhi.zazen on 2011-08-01
Boot fedora and edit the file as root.

```
su -
vim /boot/grub/menu.lst
```

If you are using the live CD, you would mount your boot partition (sda6) at say /mnt and then 

```
su -
mount /dev/sda6 /mnt
vim /mnt/grub/menu.lst
```

You can use nano or gedit to vim (you will need to install nano first

yum install nano 

)

---

### Post by Pulka on 2011-08-01
Nope.

Still having a text mode grub

---

### Post by oldfred on 2011-08-01
It shows you are booting with grub2 in the MBR, with a /boot in sda1. But you seem to have some file issues with /home.

```
sda5: ____________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I would try this first:
#From liveCD so everything is unmounted,swap off if necessary, change sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda5
#if errors:
sudo e2fsck -f -y -v /dev/sda5

---

### Post by Pulka on 2011-08-01
thank u for your help, but decided to do a fresh install.

---

### Post by bodhi.zazen on 2011-08-01
> **Pulka said:**
> thank u for your help, but decided to do a fresh install.

I recall those days.

Keep learning and your need for a "fresh install" will decrease.

---

### Post by beew on 2011-08-01
> **Pulka said:**
> thank u for your help, but decided to do a fresh install.

If you do a fresh install of Fedora make sure you choose _not _to install the bootloader, that option is available. After that log into Ubuntu and run "sudo update-grub" and it will detect Fedora and add it to the boot menu.

EDITED: Also, remember to log in to Ubuntu and run "sudo update-grub" whenever there is a kernel update in Fedora.

---

### Post by beew on 2011-08-01
> **amjjawad said:**
> Reminds me of the old days :)

I read it some where that with Fedora 16, GRUB2 will be used so hope that will fix the issue but that won't be Fedora, thanks go to GRUB2 :D

Yup, I think grub2 is great, meanwhile there are some people (old timers I suspect) still complaining and whining about grub2 and say grub legacy is sooo much better.  I just can't see what their points are other than,--hate to say that,--fear of change. :)

---

### Post by EkuquoL on 2011-08-01
You possibly have  a conflicting boot manager problem and/or a segmented Partition. Re-install -- with only one swap and one partition.

---

### Post by amjjawad on 2011-08-02
> **beew said:**
> If you do a fresh install of Fedora make sure you choose _not _to install the bootloader, that option is available. After that log into Ubuntu and run "sudo update-grub" and it will detect Fedora and add it to the boot menu.

EDITED: Also, remember to log in to Ubuntu and run "sudo update-grub" whenever there is a kernel update in Fedora.

When it comes to Fedora and their endless love to GRUB Legacy, I have learned one thing from my previous experience with it.

The Boot-Loader SHOULD be installed in PBR instead of MBR otherwise, Fedora won't be bootable.
Of course I'm talking about Dual-Boot or Multi-Boot Systems.
Then, the magical command: "sudo update-grub" and enjoy your life :)


Perhaps there is another way to make it work but why go all the way and try to fix that while it's so easy to just install the boot loader to the PBR instead of MBR :)

Well, guess it's time for another test :D


> **beew said:**
> Yup, I think grub2 is great, meanwhile there are  some people (old timers I suspect) still complaining and whining about  grub2 and say grub legacy is sooo much better.  I just can't see what  their points are other than,--hate to say that,--fear of change. :smile:

Couldn't agree more ;)

---

### Post by amjjawad on 2011-08-02
> **bodhi.zazen said:**
> Keep learning and your need for a "fresh install" will decrease.

+1

Good one, bodhi :)

---

### Post by coffeecat on 2011-08-02
> **beew said:**
> If you do a fresh install of Fedora make sure you choose _not _to install the bootloader, that option is available. After that log into Ubuntu and run "sudo update-grub" and it will detect Fedora and add it to the boot menu.

@Pulka, this is good advice.

Also - a couple of other suggestions to ensure that it's easier for Fedora to live with Ubuntu. Don't let the Fedora installer choose the partitions for you and don't let it create an LVM volume. That *may* prevent Ubuntu's grub from seeing it. And don't let it create a separate boot partition - an unnecessary complication. Install Fedora to one ext4 partition.

---

### Post by amjjawad on 2011-08-02
> **amjjawad said:**
> When it comes to Fedora and their endless love to GRUB Legacy, I have learned one thing from my previous experience with it.

The Boot-Loader SHOULD be installed in PBR instead of MBR otherwise, Fedora won't be bootable.
Of course I'm talking about Dual-Boot or Multi-Boot Systems.
Then, the magical command: "sudo update-grub" and enjoy your life :)

Well, guess it's time for another test :D




It seems I was wrong about what I wrote above in my previous post.

I just installed Fedora 15 and have XP, Ubuntu 11.04 and Fedora 15 on one machine, one HDD:


```
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    39,086,144    39,086,082   7 NTFS / exFAT / HPFS
/dev/sda2          39,092,224    57,966,591    18,874,368  83 Linux
/dev/sda3          75,925,504    78,176,255     2,250,752  82 Linux swap / Solaris
/dev/sda4          57,966,592    75,925,503    17,958,912  83 Linux

```And you guys were right. There is NO need to install the boot-loader, just un-tick/un-check that option during installation.

However, I'm surprised because I remember that before, I had Multi-Boot Setup (9 OS's) and Fedora 13 at that time **wouldn't boot unless I install its boot-loader to PBR in the same partition where Fedora is installed**, then run "update-grub" and that's all.
Now, it's different case. GRUB Legacy shouldn't be installed on the first place.

Testing that myself was needed to keep myself updated of what's going on :)
Sorry if I posted something not 100% correct.


```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    39,086,144    39,086,082   7 NTFS / exFAT / HPFS
/dev/sda2          39,092,224    57,966,591    18,874,368  83 Linux
/dev/sda3          75,925,504    78,176,255     2,250,752  82 Linux swap / Solaris
/dev/sda4          57,966,592    75,925,503    17,958,912  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CA30BBCC30BBBDAF                       ntfs       
/dev/sda2        c4285560-d05e-4080-87ac-628e7136df0a   ext4       
/dev/sda3        dbb84bf5-4ffb-42de-9988-75eeb79742ca   swap       
/dev/sda4        ac82c457-eb90-4d6b-b747-859ddc74774f   ext4       _Fedora-15-i686-

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c4285560-d05e-4080-87ac-628e7136df0a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c4285560-d05e-4080-87ac-628e7136df0a
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root c4285560-d05e-4080-87ac-628e7136df0a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c4285560-d05e-4080-87ac-628e7136df0a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root c4285560-d05e-4080-87ac-628e7136df0a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c4285560-d05e-4080-87ac-628e7136df0a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root c4285560-d05e-4080-87ac-628e7136df0a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root c4285560-d05e-4080-87ac-628e7136df0a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root CA30BBCC30BBBDAF
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Fedora release 15 (Lovelock) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root ac82c457-eb90-4d6b-b747-859ddc74774f
    linux /boot/vmlinuz-2.6.38.6-26.rc1.fc15.i686 root=/dev/sda4
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.i686.img
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
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=c4285560-d05e-4080-87ac-628e7136df0a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=f1891946-988d-431b-9b54-1d8030b6dedd none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  20.247383118 = 21.740462080   boot/grub/core.img                             1
  20.984458923 = 22.531891200   boot/grub/grub.cfg                             1
  19.300334930 = 20.723576832   boot/initrd.img-2.6.38-8-generic               2
  20.245674133 = 21.738627072   boot/vmlinuz-2.6.38-8-generic                  1
  19.300334930 = 20.723576832   initrd.img                                     2
  20.245674133 = 21.738627072   vmlinuz                                        1

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Tue Aug  2 15:52:08 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=ac82c457-eb90-4d6b-b747-859ddc74774f /                       ext4    defaults        1 1
UUID=dbb84bf5-4ffb-42de-9988-75eeb79742ca swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  29.809860229 = 32.008093696   boot/initramfs-2.6.38.6-26.rc1.fc15.i686.img   1
  28.887588501 = 31.017811968   boot/vmlinuz-2.6.38.6-26.rc1.fc15.i686         1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```Note:
```
sudo update-grub
```is required and it's a must after installing Fedora without its boot loader.

---

### Post by Pulka on 2011-08-02
Everything is alright after a fresh install.

Installed first Ubuntu 11.04 and left a free space in the hardrive.
Installed second Fedora 15 choosing the free space and not installing boot manager.

After both installed, went to ubuntu and did ```
update-grub
```. After that, grub gives me ubuntu and fedora.

All is well.

About the learning part...i miss the old days when ubuntu was giving his first steps. I learned a lot searching in the forums and messing around in terminal. The last versions of Ubuntu turned me into a lazy boy and there's no need to "dig in the dirt". It's good of course, but there's always the geek part that will never die.

Thank you all for your suggestions and help.

---

### Post by bodhi.zazen on 2011-08-02
That works and there is nothing wrong with it.

If you install Fedora second, and install grub, see my previous post for what to add to the grub menu in Fedora to chainload Ubuntu.

That is a "minor edit" and should be rather trivial.

---

### Post by beew on 2011-08-03
> **amjjawad said:**
> When it comes to Fedora and their endless love to GRUB Legacy, I have learned one thing from my previous experience with it.

The Boot-Loader SHOULD be installed in PBR instead of MBR otherwise, Fedora won't be bootable.
Of course I'm talking about Dual-Boot or Multi-Boot Systems.



Just don't install the bootloader and you'll be fine. I have a multiboot system with several flavours of Ubuntu and Fedora. I let Ubuntu 11.04  control grub and didn't install bootloader for Fedora and that's it. It is actually more tricky to dual boot two buntus. Only one should control grub but Ubuntu doesn't have the option of not installing bootloader so you have to install it in the partition instead of the drive (PBR instead of MBR) if you don't want it to control grub, took me a while to find that out. :)

PS Just saw your next post, should have read further before I replied. :)

---

### Post by amjjawad on 2011-08-03
> **beew said:**
> Ubuntu doesn't have the option of not installing bootloader so you have to install it in the partition instead of the drive (PBR instead of MBR) if you don't want it to control grub


Aha, looks like I'm officially getting old :D
I do remember this, I had to install GRUB to the partition, otherwise it wouldn't boot. Right, now I remember, thanks :)

> took me a while to find that out. 

I had to create a multi-boot system to figure that out but that was in the past, almost a year now so I totally forgot it. Thanks for the reminder :D


> PS Just saw your next post, should have read further before I replied. :)
Don't worry my friend, I do have the same habit :P

---

