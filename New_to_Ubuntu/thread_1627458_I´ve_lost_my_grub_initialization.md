---
title: "I´ve lost my grub initialization"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by Jaraqui on 2010-11-21
Hi people,

   Today I really need your kind help.

   Trying to install WinXP in another partion the
Microsoft process erased my grub initialization 
system.

   I executed the steps in
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
RecoveringUbuntuAfterInstallingWindows
  
   But, at the end, after rebooting, I only reach
the "grub>" prompt. I was expecting to see my 
menu of options again and initialize my 10.04 
normally.

   Based on this tutorial, I will pass you
my results:

1)
I am using grub Legacy 0.97

2)
The result of my "mount | tail -1" command was:
/dev/sda1 on /media/29938dba-1217-4db8-8a1b-a8696b67da6f
 type ext3 (rw,nosuid,nodev,uhelper=udisks)


3)
The result of my "sudo grub-install --root-directory=
/media/29938dba-1217-4db8-8a1b-a8696b67da6f /dev/sda
--recheck" command was:

Probing devices to guess BIOS drives. This may take a long time.
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map 
/media/29938dba-1217-4db8-8a1b-a8696b67da6f/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda

4) Additional information:
   -The contents of my device.map file is 

    (hd0) /dev/sda

   -The contents of my menu.lst is:

   timeout 5
   color black/cyan yellow/cyan
   gfxmenu (hd0,0)/gfxmenu
   default 0

   title Linux
   kernel (hd0,0)/vmlinuz BOOT_IMAGE=linux root=/dev/sda3 
   resume=/dev/sda5 splash=silent vga=788 acpi_osi=
   initrd (hd0,0)/initrd.img

   title Recuperacao via HD
   kernel (hd0,0)/vmlinuz BOOT_IMAGE=Recuperacao_via_HD
   root=/dev/sda2 resume=/dev/sda5 splash=silent vga=788
   initrd (hd0,0)/initrd.img

Thank you, in advance
Jaraqui

---

### Post by sikander3786 on 2010-11-21
Please boot into a Live CD and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would give us the clear picture of your current setup.

Please wrap the output using proper code tags # from the post menu. Post it in between the generated codes or highlight your post and press # to wrap it.

---

### Post by Jaraqui on 2010-11-21
Hi,

   Another attempt I made, after this, was to do the
following:
   At the "grub>" prompt I´ve got in the inicialization,
I typed:
   a) "find /boot/grub/stage1"
       The result was:
       (hd0,0)
       (hd0,6)
   b) "root (hd0,0)"
       No result was echoed;
   c) "setup (hd0)"
       The results were:
       Checking if "boot/grub/stage1" exists...yes
       Checking if "boot/grub/stage2" exists...yes
       Checking if "boot/grub/e2fs__stage1_5" exists...yes
       Running "embeb /boot/grub/e2fs_stage1_5 (hd0)" ...
       17 sectors are embedded.
       succeeded
       Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p
       (hd0,0)/boot/grub/stage2/boot/grub/menu.lst"
       succeeded
       Done.
   After this commands I typed "halt" e turned the note
   on. 
   Unfortunately, only the "grub>" prompt was presented
   again...

   Any ideas/suggestions?

Thanks for your cooperation.
Jaraqui

---

### Post by Jaraqui on 2010-11-21
Hi sikander, here is my RESULTS.TXT file:
```

#################################################################
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2008.0 
                       (Official) for i586 Kernel 2.6.24.7-desktop-7mdvoem on 
                       a Dual-processor i686 /
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2008.0 
                       (Official) for i586 Kernel 2.6.24.7-desktop-7mdvoem on 
                       a Dual-processor i686 /
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

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

/dev/sda1    *             63       112,454       112,392  83 Linux
/dev/sda2             112,455     5,992,244     5,879,790  83 Linux
/dev/sda3           5,992,245    27,487,214    21,494,970  83 Linux
/dev/sda4          27,487,215   625,137,344   597,650,130   5 Extended
/dev/sda5          27,487,278    29,463,209     1,975,932  82 Linux swap / Solaris
/dev/sda6          29,463,273   377,302,589   347,839,317   e W95 FAT16 (LBA)
/dev/sda7         377,302,653   614,984,264   237,681,612  83 Linux
/dev/sda8         614,984,328   625,137,344    10,153,017  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        29938dba-1217-4db8-8a1b-a8696b67da6f   ext3                                     
/dev/sda2        16cbed0e-5371-41bb-9049-4fbf222e84a1   ext3                                     
/dev/sda3        00fd0d22-744e-11dc-9872-0019db8f5cdb   ext3                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        a52a66a2-75c2-11de-99b6-a1a7d40a93ee   swap                                     
/dev/sda7        b8704e2b-16f6-42ea-b148-afaf0cf34b37   ext4                                     
/dev/sda8        7e895643-4315-41e1-8fd0-b62cfe5670ee   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/menu.lst: =============================

timeout 5
color black/cyan yellow/cyan
gfxmenu (hd0,0)/gfxmenu
default 0

title Linux
kernel (hd0,0)/vmlinuz BOOT_IMAGE=linux root=/dev/sda3 resume=/dev/sda5 splash=silent vga=788 acpi_osi=
initrd (hd0,0)/initrd.img

title Recuperacao via HD
kernel (hd0,0)/vmlinuz BOOT_IMAGE=Recuperacao_via_HD root=/dev/sda2 resume=/dev/sda5 splash=silent vga=788
initrd (hd0,0)/initrd.img

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/stage2
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd-2.6.24.7-desktop-7mdvoem.img
    .0GB: initrd-2.6.24.7-desktop-7mdvoem.img-resize
    .0GB: initrd-desktop.img
    .0GB: initrd.img
    .0GB: vmlinuz
    .0GB: vmlinuz-2.6.24.7-desktop-7mdvoem
    .0GB: vmlinuz-desktop

=============================== sda2/etc/fstab: ===============================

/dev/sda1 /boot ext3 relatime 1 1
/dev/sda2 / ext3 relatime 1 1
/dev/cdrom /media/cdrom auto umask=0022,users,iocharset=utf8,noauto,ro,exec 0 0
none /proc proc defaults 0 0
/dev/sda5 swap swap defaults 0 0

=============================== sda3/etc/fstab: ===============================

/dev/sda1 /boot ext3 relatime 1 1
/dev/sda3 / ext3 relatime 1 1
/dev/sda6 /home ext3 relatime 1 2
/dev/sr0 /media/cdrom auto umask=0022,users,iocharset=utf8,noauto,ro,exec 0 0
none /proc proc defaults 0 0
/dev/sda5 swap swap defaults 0 0


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set b8704e2b-16f6-42ea-b148-afaf0cf34b37
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set b8704e2b-16f6-42ea-b148-afaf0cf34b37
set locale_dir=($root)/boot/grub/locale
set lang=pt
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
menuentry 'Ubuntu, com Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b8704e2b-16f6-42ea-b148-afaf0cf34b37
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b8704e2b-16f6-42ea-b148-afaf0cf34b37 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, com Linux 2.6.32-25-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b8704e2b-16f6-42ea-b148-afaf0cf34b37
	echo	'Carregando Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b8704e2b-16f6-42ea-b148-afaf0cf34b37 ro single 
	echo	'Carregando ramdisk inicial ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, com Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b8704e2b-16f6-42ea-b148-afaf0cf34b37
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b8704e2b-16f6-42ea-b148-afaf0cf34b37 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, com Linux 2.6.32-24-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b8704e2b-16f6-42ea-b148-afaf0cf34b37
	echo	'Carregando Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b8704e2b-16f6-42ea-b148-afaf0cf34b37 ro single 
	echo	'Carregando ramdisk inicial ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, com Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b8704e2b-16f6-42ea-b148-afaf0cf34b37
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b8704e2b-16f6-42ea-b148-afaf0cf34b37 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, com Linux 2.6.32-23-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b8704e2b-16f6-42ea-b148-afaf0cf34b37
	echo	'Carregando Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b8704e2b-16f6-42ea-b148-afaf0cf34b37 ro single 
	echo	'Carregando ramdisk inicial ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, com Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b8704e2b-16f6-42ea-b148-afaf0cf34b37
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b8704e2b-16f6-42ea-b148-afaf0cf34b37 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, com Linux 2.6.32-22-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b8704e2b-16f6-42ea-b148-afaf0cf34b37
	echo	'Carregando Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b8704e2b-16f6-42ea-b148-afaf0cf34b37 ro single 
	echo	'Carregando ramdisk inicial ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b8704e2b-16f6-42ea-b148-afaf0cf34b37
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set b8704e2b-16f6-42ea-b148-afaf0cf34b37
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 29938dba-1217-4db8-8a1b-a8696b67da6f
	linux /vmlinuz BOOT_IMAGE=linux root=/dev/sda3 resume=/dev/sda5 splash=silent vga=788 acpi_osi=
	initrd (hd0,0)/initrd.img
}
menuentry "Recuperacao via HD (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 29938dba-1217-4db8-8a1b-a8696b67da6f
	linux /vmlinuz BOOT_IMAGE=Recuperacao_via_HD root=/dev/sda2 resume=/dev/sda5 splash=silent vga=788
	initrd (hd0,0)/initrd.img
}
menuentry "Linux (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 29938dba-1217-4db8-8a1b-a8696b67da6f
	linux /vmlinuz BOOT_IMAGE=linux root=/dev/sda3 resume=/dev/sda5 splash=silent vga=788 acpi_osi=
	initrd (hd0,0)/initrd.img
}
menuentry "Recuperacao via HD (on /dev/sda3)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 29938dba-1217-4db8-8a1b-a8696b67da6f
	linux /vmlinuz BOOT_IMAGE=Recuperacao_via_HD root=/dev/sda2 resume=/dev/sda5 splash=silent vga=788
	initrd (hd0,0)/initrd.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=b8704e2b-16f6-42ea-b148-afaf0cf34b37 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=7e895643-4315-41e1-8fd0-b62cfe5670ee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 193.3GB: boot/grub/core.img
 201.6GB: boot/grub/grub.cfg
 193.4GB: boot/grub/stage2
 195.7GB: boot/initrd.img-2.6.32-22-generic
 195.7GB: boot/initrd.img-2.6.32-23-generic
 197.2GB: boot/initrd.img-2.6.32-24-generic
 265.9GB: boot/initrd.img-2.6.32-25-generic
 194.9GB: boot/vmlinuz-2.6.32-22-generic
 194.9GB: boot/vmlinuz-2.6.32-23-generic
 195.3GB: boot/vmlinuz-2.6.32-24-generic
 197.5GB: boot/vmlinuz-2.6.32-25-generic
 265.9GB: initrd.img
 197.2GB: initrd.img.old
 197.5GB: vmlinuz
 195.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000200
###################################################################

```

---

### Post by sikander3786 on 2010-11-21
You have an installation of Ubuntu 10.04 and that uses grub2 not the Grub legacy which you have installed previously.

Instead, from a Live CD of Ubuntu 9.10 or above, use these commands to reinstall Grub2.

```
sudo mount /dev/sda7 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note, for the 2nd command it is just sda and not sda7.

Grub2 should find all your Mandriva installs and add them to the Grub menu.

If it doesn't do that automatically, run

```
sudo update-grub
```

After booting your Ubuntu install.

Good Luck!

---

### Post by Jaraqui on 2010-11-21
oh my God.

   Thank you, man.
   Thank you very much.

   Everything is ok now.

Jaraqui

---

### Post by sikander3786 on 2010-11-21
You are Welcome :-)

Glad it is sorted out now. You can mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

