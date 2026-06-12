---
title: "Ubuntu stuck at desktop w/ frozen mouse after apt-upgrade"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by EzioAuditore on 2011-04-03
Hello everyone,

I don't know what went wrong but i'm now able to do almost nothing.. The mouse remain stucked at desktop and nothing works, no keyboard shortcuts even..

The only thing I was doing before it happened was apt-get upgrade which returned some error code (1) and executed the following commands in a hope of removing the screen flickering


```
$ cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
```

```
xrandr --newmode "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
```

```
xrandr --addmode LVDS "1366x768_60.00"
```

```
xrandr --output LVDS --mode "1366x768_60.00"
```
Reference of above commands-- [http://ubuntuforums.org/showthread.php?t=1622639](http://ubuntuforums.org/showthread.php?t=1622639)

Then i saw 'restart to finish installing updates' at the indicator applet.. I thought ok, let it install the ones which it can and restarted.. But now i cant do anything... it goes to desktop just to hang... nothing works..

Tried recovery mode but it too gets hung-up in somewhere middle..

Here's the boot.log file:

```
fsck from util-linux-ng 2.17.2
/dev/sda7: clean, 152391/2629632 files, 3134965/10498469 blocks
init: udevtrigger main process (398) terminated with status 1

init: udevtrigger post-stop process (403) terminated with status 1

init: udevmonitor main process (397) killed by TERM signal

```


Currently, im in the live desktop environment.. (that try before install option)

I'm on dual-boot with Ubuntu 10.10 and Windows 7.

Please help me folks. I have to get it up again, don't want to do a re-install again.

---

### Post by davidmohammed on 2011-04-03
you mentioned that you had graphics issues - maybe this hard-lock is due to some incompatibility.

What is your graphics card?

If it is an nvidia or ATI then suggest try booting with "nomodeset"

n.b. - press shift on booting to display your grub - press e to edit and then find the line ending "quiet splash".  Add "nomodeset" immediately before quiet splash.  Press CTRL+X to boot.

you could also try booting with "acpi=off" or maybe "acpi=off nomodeset"

---

### Post by EzioAuditore on 2011-04-03
> you mentioned that you had graphics issues - maybe this hard-lock is due to some incompatibility.

Just some flickerings at startup.. nothing more.

> What is your graphics card?

ATI 4350


> you could also try booting with "acpi=off" or maybe "acpi=off nomodeset"

Where do I add these?

Also, is there any way to revert to the state before installing the updates and also to undo what those xrandr commands did?

Thanks for your reply though. :)

---

### Post by EzioAuditore on 2011-04-03
> you mentioned that you had graphics issues - maybe this hard-lock is due to some incompatibility.

Just some flickerings at startup.. nothing more.

> What is your graphics card?

ATI 4350


> you could also try booting with "acpi=off" or maybe "acpi=off nomodeset"

Where do I add these?

Also, is there any way to revert to the state before installing the updates and also to undo what those xrandr commands did?

Thanks for your reply though. :)

---

### Post by davidmohammed on 2011-04-03
...

press shift on booting to display your grub - press e to edit and then find the line ending "quiet splash". Add "nomodeset"/"acpi=off" or "acpi=off nomodeset" immediately before quiet splash. 

i.e. the line should look some like

... nomodeset quiet splash --

Press CTRL+X to boot.

---

### Post by EzioAuditore on 2011-04-03
No joy... :-(
Also, when it boots to the desktop (just to get stuck), after around 5minutes, screen goes black and never returns to the desktop.. It doesn't respond to mouse or keyboard. Also, keyboard's indicator lights like nun lock, caps lock doesn't lit up..

---

### Post by davidmohammed on 2011-04-03
hmmm.

My thoughts would be to boot using the 10.10 live CD.  Then access your hard-drive and save any valuable files before trying a fresh installation.

---

### Post by EzioAuditore on 2011-04-03
So, no other way except a fresh install?
I tried recovery mode, but it too gets hung-up. It also displays some '2 orphan inodes deleted', do you know what these mean?
By the way, if i chroot to my installation after booting with a liveCD and then running apt update or apt upgrade or somehow undo-ing the previously done apt upgrade, won't that do some good? Is there any hope?

---

### Post by EzioAuditore on 2011-04-04
*UPDATE*
-------------


Thank you all guys for your time.. Really appreciate it.

But I've a good news and a bad news, good news is that chrooting from a liveCD and reinstalling grub did the job, ubuntu is up and running flawlessly again. Yay! 

Here comes the bad news, i'm not getting the grub boot menu, it directly boots to Ubuntu.. :-/

Here's my grub.cfg file contents:

```
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
search --no-floppy --fs-uuid --set 219f6080-7483-4507-9d41-3d2b766a0f17
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 219f6080-7483-4507-9d41-3d2b766a0f17
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 219f6080-7483-4507-9d41-3d2b766a0f17
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=219f6080-7483-4507-9d41-3d2b766a0f17 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 219f6080-7483-4507-9d41-3d2b766a0f17
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=219f6080-7483-4507-9d41-3d2b766a0f17 ro single 
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 219f6080-7483-4507-9d41-3d2b766a0f17
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 219f6080-7483-4507-9d41-3d2b766a0f17
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
```

And the entry for Windows 7 is also missing in the file, defaulting to ubuntu.. Help me solve it pls..

---

### Post by EzioAuditore on 2011-04-04
Here's the boot info script's result.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,905,039    81,904,977   7 HPFS/NTFS
/dev/sda2          81,915,496   625,137,344   543,221,849   f W95 Ext d (LBA)
/dev/sda5          81,915,498   245,762,369   163,846,872   7 HPFS/NTFS
/dev/sda6         245,762,433   393,721,019   147,958,587   7 HPFS/NTFS
/dev/sda7         393,721,083   477,708,839    83,987,757  83 Linux
/dev/sda8         477,708,903   625,137,344   147,428,442   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6CF4FF44F4FF0F58                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        32D6F054D6F01A35                       ntfs                                     
/dev/sda6        01CBE6A8C2F63280                       ntfs                                     
/dev/sda7        219f6080-7483-4507-9d41-3d2b766a0f17   ext4                                     
/dev/sda8        01CBE6B762BABD00                       ntfs                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660    (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set 219f6080-7483-4507-9d41-3d2b766a0f17
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 219f6080-7483-4507-9d41-3d2b766a0f17
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 219f6080-7483-4507-9d41-3d2b766a0f17
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=219f6080-7483-4507-9d41-3d2b766a0f17 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 219f6080-7483-4507-9d41-3d2b766a0f17
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=219f6080-7483-4507-9d41-3d2b766a0f17 ro single 
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 219f6080-7483-4507-9d41-3d2b766a0f17
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 219f6080-7483-4507-9d41-3d2b766a0f17
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=219f6080-7483-4507-9d41-3d2b766a0f17 /               ext4    errors=remount-ro 0       1
tmpfs     /dev/shm     tmpfs     defaults,noexec,nosuid     0     0

=================== sda7: Location of files loaded by Grub: ===================


 212.4GB: boot/grub/core.img
 203.9GB: boot/grub/grub.cfg
 212.9GB: boot/initrd.img-2.6.35-22-generic
 210.2GB: boot/vmlinuz-2.6.35-22-generic
 212.9GB: initrd.img
 210.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by EzioAuditore on 2011-04-04
Nevermind, solved! 

I just had to delete the previous boot folder in windows partition which contained the grub files and update-grub did it..

---

