---
title: "GRUB Help"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by 10up on 2010-07-15
I have several different partitions on my HDD.  I primarily use the Ubuntu partition but occasionally need to boot into Windows for work related things.

I installed Windows 7 Ultimate over the old Windows XP partition earlier today.  Lo and behold it erased my ability to access the GRUB Boot Loader.  I followed instructions found at Ubuntu Geek related to this.  They essentially directed me to boot off a LiveCD and enter the following commands via terminal:

```
sudo grub

> root (hd0,0)

> setup (hd0)

> exit
```

That *did* fix the problem of the Grub not appearing after BIOS loads.  However, now if I try to boot into the available Ubuntu options it doesn't work.  If I choose the top option I receive **ERROR 15: FILE NOT FOUND**.

If I try to boot into the second option (below the "recovery mode") it takes me to what looks like the loading screens from 9.04 or earlier (currently running 10.04) but the system never loads.  A couple of times it got all the way to the desktop but the system would hang before anything loaded entirely.  Forcing me to do a hard shutdown.

I really like the way I finally had Ubuntu running.  I really don't want to reload the entire thing because of a Grub issue, I'm just really not very versed in these things.

Any help on how to get my Ubuntu partition mounted properly would be very much appreciated.  I'm currently running on my new Windows Partition and can give any extra information anyone would need.

---

### Post by drs305 on 2010-07-15
Please run the boot info script and post the results here. You can run the script from the LiveCD. This will tell us whether your system is really using Grub legacy and not Grub 2, etc. It will provide us with the information we need to make an informed proposal.

Please paste the information between code tags, which you generate by pressing the # icon in the posts menu.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by 10up on 2010-07-15
Hey thanks for the quick reply!

Here is the info from the Boot Script
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 362538855.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   311,083,071   311,083,009  83 Linux
/dev/sda2    *    311,098,725   360,441,702    49,342,978   7 HPFS/NTFS
/dev/sda3         603,915,480   611,899,784     7,984,305   5 Extended
/dev/sda5         603,915,543   611,899,784     7,984,242  82 Linux swap / Solaris
/dev/sda4         362,538,855   603,915,479   241,376,625   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        017af26c-bdc5-4f32-983a-991f14aa0dff   ext3                                     
/dev/sda2        0EB84BFCB84BE0B7                       ntfs                                     
/dev/sda4        CE35-61E0                              vfat                                     
/dev/sda5        3df4f8e3-bffb-4f37-a65b-15fa90be9c82   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		8

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=017af26c-bdc5-4f32-983a-991f14aa0dff

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-20-generic
root		(hd0,0)
uuid		017af26c-bdc5-4f32-983a-991f14aa0dff
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro ROOTFLAGS=syncio splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		017af26c-bdc5-4f32-983a-991f14aa0dff
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.28-18-generic
root		(hd0,3)
uuid		017af26c-bdc5-4f32-983a-991f14aa0dff
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro ROOTFLAGS=syncio splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-18-generic (recovery mode)
uuid		017af26c-bdc5-4f32-983a-991f14aa0dff
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.10, memtest86+
uuid		017af26c-bdc5-4f32-983a-991f14aa0dff
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows 7 Ultimate
root (hd0,1)
makeactive
chainloader +1

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
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
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro   quiet splash pciehp.pciehp_force=1
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro   quiet splash pciehp.pciehp_force=1
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro   quiet splash pciehp.pciehp_force=1
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro   quiet splash pciehp.pciehp_force=1
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-18-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
	linux	/boot/vmlinuz-2.6.28-18-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro   quiet splash pciehp.pciehp_force=1
	initrd	/boot/initrd.img-2.6.28-18-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
	echo	'Loading Linux 2.6.28-18-generic ...'
	linux	/boot/vmlinuz-2.6.28-18-generic root=UUID=017af26c-bdc5-4f32-983a-991f14aa0dff ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-18-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 017af26c-bdc5-4f32-983a-991f14aa0dff
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 1649bdf00cd7e947
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=017af26c-bdc5-4f32-983a-991f14aa0dff /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3df4f8e3-bffb-4f37-a65b-15fa90be9c82 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.7GB: boot/grub/core.img
   2.7GB: boot/grub/grub.cfg
   2.7GB: boot/grub/menu.lst
  39.8GB: boot/grub/stage2
   2.7GB: boot/initrd.img-2.6.28-18-generic
   2.6GB: boot/initrd.img-2.6.31-21-generic
   2.8GB: boot/initrd.img-2.6.32-22-generic
   2.9GB: boot/initrd.img-2.6.32-23-generic
   3.0GB: boot/initrd.img-2.6.32-24-generic
   3.0GB: boot/vmlinuz-2.6.28-18-generic
   2.7GB: boot/vmlinuz-2.6.31-21-generic
   2.6GB: boot/vmlinuz-2.6.32-22-generic
   2.9GB: boot/vmlinuz-2.6.32-23-generic
   2.9GB: boot/vmlinuz-2.6.32-24-generic
   3.0GB: initrd.img
   2.9GB: initrd.img.old
   2.9GB: vmlinuz
   2.9GB: vmlinuz.old
```

---

### Post by drs305 on 2010-07-15
> **10up said:**
> 
If I try to boot into the second option (below the "recovery mode") it takes me to what looks like the loading screens from 9.04 or earlier (currently running 10.04) but the system never loads.

Since you appear to be using Lucid, I would recommend reinstalling and using Grub 2. You can do this from the LiveCD. Once installed, Grub 2 should boot properly as well as recognize your Windows partition and provide the means to boot that as well.

To install Grub2, boot a Lucid LiveCD. Mount your Ubuntu paritition (sda1) and then install the Grub 2 files and allow G2 to write to the MBR. Once installed, unmount your Ubuntu partition and reboot. Although it should not be necessary, sometimes you must run "sudo update-grub" for it to find your Windows OS after the initial install.

Boot the Lucid LiveCD. Then:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Note you mount the partition (sda1) in the first command, but do NOT use the partition in the second one (sda).

Once installed, unmount /dev/sda1 and reboot:
```
sudo umount /dev/sda1
```

After rebooting, if the Windows option is not displayed in the Grub2 menu:
```
sudo update-grub
```

---

