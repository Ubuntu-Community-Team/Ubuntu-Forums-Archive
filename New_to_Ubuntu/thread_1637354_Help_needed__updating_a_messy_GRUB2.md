---
title: "Help needed  updating a messy GRUB2"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by CaronMargarete on 2010-12-04
Ok so my laptop is a MESS and I really need some selfish expert care because I really love Ubuntu but am not tech-savvy enough to figure this out on my own.

Let's start with GRUB2. I have Win7 but when I installed it it overwrote my previous Ubuntu install. To fix this I installed a new version (10.04 I think) and then left it there to access the old version and get access to Win7. 

Now though GRUB2 is a mess and I'm forced to access it through the fourth access in the list. Not cool because when it loads the font is much bigger and I know I'm doing it wrong. 

I think (from other posts) that I should do this command but I'm not sure what it'll do.

```
 sudo update-grub
```

How do I:
a) remove the extra Ubuntu 10.04
b) keep Win7 the way it is
c) update the GRUB2 for the 10.10 version I'm using now and get rid of the 3 previous stuffed up versions?

Ideas? Please keep in mind that posts from multiple people make it hard for me to follow so please keep messages succinct and stupidly simple.

Cheers in advance.

---

### Post by oldfred on 2010-12-04
Download and run this script, it will tell us your details:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by CaronMargarete on 2010-12-04
> **oldfred said:**
> Download and run this script, it will tell us your details:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

Thanks for your help and very clear instructions. Here's the info you've asked for. Please not I am on the other side of the world so any further replies may not arrive quickly.

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
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

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

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750    80,035,829    39,070,080  83 Linux
/dev/sda3          80,035,830   617,329,754   537,293,925  83 Linux
/dev/sda4         617,330,686   625,141,759     7,811,074   5 Extended
/dev/sda5         617,330,688   624,685,055     7,354,368  83 Linux
/dev/sda6         624,687,104   625,141,759       454,656  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BAB4E73CB4E6F9B1                       ntfs                                     
/dev/sda2        e66f65d4-0470-4fea-af88-3b8dfbf515d2   ext4                                     
/dev/sda3        ecdfd575-2095-454a-af40-39beb1c07d61   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        30aed0c0-fa06-41e7-a613-11f5a746f9b7   ext4                                     
/dev/sda6        14bebe5e-dd93-4543-9ad8-f75e0539b0bf   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,relatime,errors=remount-ro,commit=0)
/dev/sda3        /home                    ext4       (rw,relatime,commit=0)


=========================== sda2/boot/grub/menu.lst: ===========================

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
timeout		10

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e66f65d4-0470-4fea-af88-3b8dfbf515d2

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
# defoptions=quiet splash

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

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.32-23-generic
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-23-generic (recovery mode)
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.10, kernel 2.6.31-21-generic
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-21-generic (recovery mode)
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.10, kernel 2.6.31-20-generic
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-20-generic (recovery mode)
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.10, kernel 2.6.31-19-generic
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-19-generic (recovery mode)
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 10.10, kernel 2.6.31-17-generic
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-17-generic (recovery mode)
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 10.10, kernel 2.6.31-16-generic
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-16-generic (recovery mode)
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 10.10, kernel 2.6.31-15-generic
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-15-generic (recovery mode)
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 10.10, memtest86+
uuid		e66f65d4-0470-4fea-af88-3b8dfbf515d2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=ecdfd575-2095-454a-af40-39beb1c07d61 /home           ext4    relatime        0       2
# swap was on /dev/sda4 during installation
UUID=8d2892e0-1c15-4d54-a585-a3e9f357c38d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  22.1GB: boot/grub/menu.lst
  22.8GB: boot/grub/stage2
  24.9GB: boot/initrd.img-2.6.31-15-generic
  26.2GB: boot/initrd.img-2.6.31-16-generic
  26.4GB: boot/initrd.img-2.6.31-17-generic
  27.0GB: boot/initrd.img-2.6.31-19-generic
  27.9GB: boot/initrd.img-2.6.31-20-generic
  31.0GB: boot/initrd.img-2.6.31-21-generic
  28.0GB: boot/initrd.img-2.6.32-23-generic
  26.8GB: boot/initrd.img-2.6.35-22-generic
  26.7GB: boot/initrd.img-2.6.35-23-generic
  27.6GB: boot/vmlinuz-2.6.31-15-generic
  24.7GB: boot/vmlinuz-2.6.31-16-generic
  24.2GB: boot/vmlinuz-2.6.31-17-generic
  26.5GB: boot/vmlinuz-2.6.31-19-generic
  27.8GB: boot/vmlinuz-2.6.31-20-generic
  27.8GB: boot/vmlinuz-2.6.31-21-generic
  28.5GB: boot/vmlinuz-2.6.32-23-generic
  28.0GB: boot/vmlinuz-2.6.35-22-generic
  26.3GB: boot/vmlinuz-2.6.35-23-generic
  26.7GB: initrd.img
  26.8GB: initrd.img.old
  26.3GB: vmlinuz
  28.0GB: vmlinuz.old

=================== sda3: Location of files loaded by Grub: ===================


 189.2GB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
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
search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=30aed0c0-fa06-41e7-a613-11f5a746f9b7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=30aed0c0-fa06-41e7-a613-11f5a746f9b7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set bab4e73cb4e6f9b1
	chainloader +1
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.32-23-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.31-21-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
	initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-20-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-20-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-19-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-19-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-17-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-17-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-16-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-16-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-15-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-15-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 10.04.1 LTS, memtest86+ (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
	linux /boot/memtest86+.bin 
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
UUID=30aed0c0-fa06-41e7-a613-11f5a746f9b7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=14bebe5e-dd93-4543-9ad8-f75e0539b0bf none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 317.5GB: boot/grub/core.img
 317.5GB: boot/grub/grub.cfg
 317.6GB: boot/initrd.img-2.6.32-24-generic
 317.5GB: boot/vmlinuz-2.6.32-24-generic
 317.6GB: initrd.img
 317.5GB: vmlinuz

```

---

### Post by oldfred on 2010-12-04
You have a wubi install still in windows. If you have copied everything you want out of it you have to delete it from within windows.

If any issues uninstalling:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?")

You newer install in sda5 looks ok but is not using the separate /home sda3 that you had created for the original install in sda2. Not sure how you got the core.img into /home which may have indicated an issue with your old /home?

The osprober is finding all the old kernels in your sda2 install. But you deleted the partition sda4 that it thinks is swap and converted it to the extended partition so I do not think it will boot or will at the minimum give errors on swap partition missing. If you want to boot the older one you can update the fstab with the new correct UUID for your new partition with swap. Litterally copy the swap entry from your new install's fstab to the old installs fstab.

Do you want to keep the old install. If not you can just reformat sda2 and run sudo update-grub and it will not find all those old kernels. If you want to keep it you should boot into it and houseclean old kernels. In between, I think you can just go into sda2's /boot and manually delete the old kernels but that is not the recommended way.

---

### Post by CaronMargarete on 2010-12-04
> **oldfred said:**
> You have a wubi install still in windows. If you have copied everything you want out of it you have to delete it from within windows.

If any issues uninstalling:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?) 

This is complete.

Ok so some of the language you've used is new to me, for example, I have  an idea of what sda2/5/etc are but not their function, I'm going with  name for partition? And kernals, pieces of information that make things  work?
 
 Anyway, let's see if I can understand you a bit better with a few questions because there seems to be several points here. Sorry to dumb this down but I really need to make sure I'm clear. 
 
>  You newer install in sda5 looks ok but is not using the separate /home  sda3 that you had created for the original install in sda2. Not sure how  you got the core.img into /home which may have indicated an issue with  your old /home?


[LIST]
[*]Here you're telling me that partition called sda5 is ok but some information is going to the wrong home folder. Correct? What steps do I follow to put the core.img back into the separate /home sda3 that I created?
[*]For clarities sake can I be sure I'm reading the above coded information correctly. On sda2 is 10.10 and on sda5 I have 10.04 which is the version I had to install to get access to GRUB2 again so I could get into 10.10 again. Ultimately I only want to use one Ubuntu and that's 10.10 and get rid of the other one entirely without stuffing GRUB2 completely.
[*]Is it necessary to move the core.img file if I want to delete the additional version?
[/LIST]
>  The osprober is finding all the old kernels in your sda2 install. But you deleted the partition sda4 that it thinks is swap and converted it to the extended partition so I do not think it will boot or will at the minimum give errors on swap partition missing. If you want to boot the older one you can update the fstab with the new correct UUID for your new partition with swap. Litterally copy the swap entry from your new install's fstab to the old installs fstab. 

[LIST]
[*]What is the osprober and what is its function?
[*]What is swap and what is its function?
[*]How do I reinstall the sda4 partition because there are definite errors occurring in the first entry point of this version?
[*]I'm not sure what you mean by updating the fstab with the new correct UUID. Which sda would I perform this to and how?
[/LIST]
> Do you want to keep the old install. If not you can just reformat sda2 and run sudo update-grub and it will not find all those old kernels. If you want to keep it you should boot into it and houseclean old kernels. In between, I think you can just go into sda2's /boot and manually delete the old kernels but that is not the recommended way.


[LIST]
[*]Old install? There are two. One that I think of as new and not used, 10.04, and the other which is 10.10 that is my old version that I want to keep. So let's go with removing the 10.04 version.
[*]So if my 10.10 version is being kept, do I still need to houseclean the old kernals, if so how?
[*]Regarding, anything that is not 'the recommended way', it's best not to even tell me it's an option unless you want to walk me through it. Honestly, the KISS method applies strictly here.
[/LIST]
Ok so enough questions, am I on the right track, what steps do I follow to proceed?

Many thanks oldfred.

---

### Post by drs305 on 2010-12-04
It looks like *oldfred* has signed off for the night and I am about to as well.

I don't have time to give you the answers, but I can quickly give you the commands to run to restore your 10.10 system on sda2 with /home on sda3 (which it looks is how you have the fstab set up). The instructions will install Grub2, and if you want to have questions answered it might be better to wait.

If you want to follow along on what the commands do, you can refer to the "G2-Chroot" link in my signature line. That guide explains it and you should read it as you go along so you will know how to respond to command prompts.

So, from the running 10.04 Ubuntu or a LiveCD, open a terminal and run these commands:

```
sudo mkdir /mnt/temp /mnt/temp/home
sudo mount /dev/sda2 /mnt/temp
sudo mount /dev/sda3 /mnt/temp/home
for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/temp$i ; done
sudo chroot /mnt/temp

```

You are now "root" in your 10.10 Ubuntu. We will now install Grub 2. You no longer need sudo since you are 'root' for now:
```
apt-get update  # If you don't have an Internet connection, stop and wait until tomorrow
apt-get install --reinstall grub-common
apt-get install grub-pc  # **Read the guide for how to answer the questions. Install Grub2 only to the drive (sda) and not the partition.**
update-grub

```

This should have installed Grub2 (grub-pc) into your 10.10 install. Now exit the chroot:
```
exit
```
Unmount everything:
```
for i in /dev/pts /dev /proc /sys /home / ; do sudo umount /mnt/temp$i ; done
```
Reboot.

As I mentioned, if you have questions and don't get them answered, just ask and wait for someone to respond.

---

### Post by madjr on 2010-12-04
this helped me too :)

---

### Post by oldfred on 2010-12-04
I am around only for a few more minutes and will not be back until late Sunday or Mon AM. But will check then if you are not totally solved by then.

Windows does not differentiate between drives (different hard drives) and partitions (parts of the hard drive) and calls them all drives.

In Linux sda, sdb, sdc etc are physical hard drives. Under MBR you can have 4 primary partitions sda1, sda2, sda3 or sda4. One primary can be converted to an extended which is just a container for many more logical drives always starting at sda5 even if you converted sda2 to the extended and did not use sda3 nor sda4. This is all part of the original IBM PC's definition of Master Boot Record MBR in the early 1980's.
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Osprober is part of grub that looks for other operating systems on all your drives & partitions and adds boot stanzas to the grub menu so you can also boot them.

Swap is for memory overflow and hibernation.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Also to fix your 10.10 install in sda2 you need to update fstab. You can boot into your 10.04 and edit the fstab.

Open your current fstab in 10.04 that has an entry for the new swap in sda6.

gedit /etc/fstab
you should see this that I copied from the boot scritp:
```
# swap was on /dev/sda6 during installation
UUID=[COLOR=Red]14bebe5e-dd93-4543-9ad8-f75e0539b0bf[/COLOR] none            swap    sw              0       0


```then we want to open the copy in you 10.10 install:
mkdir mav
sudo mount /dev/sda2 ~/mav
gksudo gedit /mav/etc/fstab

That should open the open the copy on sda2
Near the bottom should be this, which you want delete and replace (copy & paste) with the swap entry from above version.

```
# swap was on /dev/sda4 during installation
UUID=[COLOR=Red]8d2892e0-1c15-4d54-a585-a3e9f357c38d[/COLOR] none            swap    sw              0       0

```The only difference is the UUID which you can just change instead of replacing the entire entry. The UUID is a unique identifier for each partition.

Then unmount with umount (spelling is correct)
sudo umount mav
and remove the temporary directory we made
rmdir mav

---

### Post by CaronMargarete on 2010-12-07
Wow oh wow! 

Thanks all! I'm pretty swamped with work and preparing to move countries at the mo but I'm aiming to get to this Friday with a print out of all you've written. For now it all seems pretty clear and I'm sure I'll get through it. 

FYI I'm going with oldfred's version of information since I started this with him and the information seems clearer that doesn't redirect me to another site. 

Thanks all for your help thus far.

---

### Post by CaronMargarete on 2010-12-25
Hi *oldfred*, I wish I'd done this at the time when it was fresh in my mind but sadly, life's not that polite. 
 
When I began this it seemed to flow but I've hit a glitch... I've written the following as I followed your information.
 
Before I begin, I have to clarify the version I'm using again because the information in GRUB2 doesn't read correctly. Refer to the photo I've attached. The first version on the list is *Ubuntu, with Linux* and when I log in and go to System > About Ubuntu it tells me the version is 10.04. This is the version I've used for the below commands.
 
Note the highlighted line. This is the version I'm now going into to access 10.10, irrespective of the fact that it says 10.04. 
 
> **oldfred said:**
>  
Also to fix your 10.10 install in sda2 you need to update fstab. You can boot into your 10.04 and edit the fstab. Open your current fstab in 10.04 that has an entry for the new swap in sda6.
 
gedit /etc/fstab
you should see this that I copied from the boot scritp:
```
# swap was on /dev/sda6 during installation
UUID=[COLOR=red]14bebe5e-dd93-4543-9ad8-f75e0539b0bf[/COLOR] none            swap    sw              0       0

 
Ok so I went into 10.04, opened a terminal, typed the commands which opened a Read Only file titled *fstab,* within it I located the above UUID. 
 
> 
```then we want to open the copy in you 10.10 install:
mkdir mav
sudo mount /dev/sda2 ~/mav
gksudo gedit /mav/etc/fstab

 
Here I make the assumption to use the same terminal window and type *mkdir mav*. Only it doesn't appear to do anything so I open a second terminal tab and do it again. I'm given the message that it's already created so I proceed to the next command *sudo mount /dev/sda2 ~/mav, *it prompts for my password and again appears not to do anything. Ignoring this I proceed to the last command* gksudo gedit /mav/etc/fstab*.
 
> 
That should open the open the copy on sda2
Near the bottom should be this, which you want delete and replace (copy & paste) with the swap entry from above version.

 
It opens another fstab, but it's blank so I cannot follow the copy/paste information below.
 
> 
```
# swap was on /dev/sda4 during installation
UUID=[COLOR=red]8d2892e0-1c15-4d54-a585-a3e9f357c38d[/COLOR] none            swap    sw              0       0

```The only difference is the UUID which you can just change instead of replacing the entire entry. The UUID is a unique identifier for each partition.

 
I close without saving both fstabs (because this is all it would allow me to do) and decide to do the following commands in the hope it undoes what I started. 
 
> 
Then unmount with umount (spelling is correct)
sudo umount mav
and remove the temporary directory we made
rmdir mav 
 
Have I done something wrong? Can we try an alternative?
 
Remembering that I do not actually want/ need Ubuntu, with Linux (10.04) and want to correct the Ubuntu 10.04 to actually say 10.10, the version it is and get back to the first kernal... What would you recommend???
 
Also, can you please help me to understand why there are so many kernals when the Ubuntu, with Linux (10.04) doesn't have any?
 
Many thanks in advance.

---

### Post by oldfred on 2010-12-25
I usually want to fix things, just for my (and yours) knowledge of the system, and often to salvage important data. But in this case it may be better just to reinstall 10.10 to sda2. If you use manual install and choose sda2 as root & reformat it, then it will overwrite the current install in sda2. You also select sda3 as /home but do NOT format it, if it has your data in it. It will find swap automatically and reuse it. If you do have data in sda2 your want we can still repair it or you can back it up first.

If you want to repair sda2, lets repost the boot script to see if any changes were made and let us know what does work or not. Can you boot 10.04, windows, even the 10.10 (I do not think so)?

---

### Post by CaronMargarete on 2011-01-08
> **oldfred said:**
> I usually want to fix things, just for my (and yours) knowledge of the system, and often to salvage important data. But in this case it may be better just to reinstall 10.10 to sda2. If you use manual install and choose sda2 as root & reformat it, then it will overwrite the current install in sda2. You also select sda3 as /home but do NOT format it, if it has your data in it. It will find swap automatically and reuse it. If you do have data in sda2 your want we can still repair it or you can back it up first.

If you want to repair sda2, lets repost the boot script to see if any changes were made and let us know what does work or not. Can you boot 10.04, windows, even the 10.10 (I do not think so)?

Hey oldfred, I agree. I like to fix things but not in this instance. In the end I decided to reformat and reinstall everything. 

It took less than 2hours to fix it all up and I am a lot more sane for it!

Thanks for all your help. I appreciated your guidance.

---

### Post by oldfred on 2011-01-08
Glad it is now working for you.:)

But I am disappointed, we could have spent the last few days and many hours fixing things and you go and reinstall everything in only 2 hours.:(

Actually I only back up my data,  /home, & list of installed apps, and if I ever have a major system crash would reinstall anyway as once you have installed several times it is pretty easy. It can be intimidating for new users the first time or two and some users do not have backups and you have to do repairs just to salvage data.

---

### Post by CaronMargarete on 2011-01-08
> **oldfred said:**
> Glad it is now working for you.:)

But I am disappointed, we could have spent the last few days and many hours fixing things and you go and reinstall everything in only 2 hours.:(

Actually I only back up my data,  /home, & list of installed apps, and if I ever have a major system crash would reinstall anyway as once you have installed several times it is pretty easy. It can be intimidating for new users the first time or two and some users do not have backups and you have to do repairs just to salvage data.

Hmmm I'd be sorrier for your disappointment if I weren't bathing in functional-ubuntu glory right now  :P

Although, you might have insight to one weird thing that's happened is that even though we reformatted and adjusted the partitions the install seems to have duplicated itself. The version I'm using is on sda5 but for the life of me don't know why there's another one on sda7.

Here's the Boot Info:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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

/dev/sda1    *             63   143,364,059   143,363,997   7 HPFS/NTFS
/dev/sda2         143,364,060   380,869,019   237,504,960  83 Linux
/dev/sda3         380,874,750   625,141,759   244,267,010   5 Extended
/dev/sda5         617,330,688   624,685,055     7,354,368  83 Linux
/dev/sda6         624,687,104   625,141,759       454,656  82 Linux swap / Solaris
/dev/sda7         380,874,752   607,633,407   226,758,656  83 Linux
/dev/sda8         607,635,456   617,330,687     9,695,232  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C884ED4A84ED3C16                       ntfs                                     
/dev/sda2        3f8a9f9e-ed82-4a19-aa38-ecd3434e2a39   ext4       Jamie                         
/dev/sda3: PTTYPE="dos" 
/dev/sda5        30aed0c0-fa06-41e7-a613-11f5a746f9b7   ext4                                     
/dev/sda6        14bebe5e-dd93-4543-9ad8-f75e0539b0bf   swap                                     
/dev/sda7        ca0899d2-2531-469e-b276-24093a29fead   ext4       Ubuntu                        
/dev/sda8        273b6a20-9bea-4f8e-b225-57048126373a   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
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
search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=30aed0c0-fa06-41e7-a613-11f5a746f9b7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=30aed0c0-fa06-41e7-a613-11f5a746f9b7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set bab4e73cb4e6f9b1
    chainloader +1
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.32-22-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.31-21-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
    initrd /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-20-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-20-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.31-20-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-19-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-19-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-17-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-17-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-16-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-16-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-15-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro quiet splash
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 10.04.1 LTS, kernel 2.6.31-15-generic (recovery mode) (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=e66f65d4-0470-4fea-af88-3b8dfbf515d2 ro single
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 10.04.1 LTS, memtest86+ (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e66f65d4-0470-4fea-af88-3b8dfbf515d2
    linux /boot/memtest86+.bin 
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
UUID=30aed0c0-fa06-41e7-a613-11f5a746f9b7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=14bebe5e-dd93-4543-9ad8-f75e0539b0bf none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 317.5GB: boot/grub/core.img
 317.5GB: boot/grub/grub.cfg
 317.6GB: boot/initrd.img-2.6.32-24-generic
 317.5GB: boot/vmlinuz-2.6.32-24-generic
 317.6GB: initrd.img
 317.5GB: vmlinuz

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
search --no-floppy --fs-uuid --set ca0899d2-2531-469e-b276-24093a29fead
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
search --no-floppy --fs-uuid --set ca0899d2-2531-469e-b276-24093a29fead
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
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set ca0899d2-2531-469e-b276-24093a29fead
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ca0899d2-2531-469e-b276-24093a29fead ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set ca0899d2-2531-469e-b276-24093a29fead
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ca0899d2-2531-469e-b276-24093a29fead ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set ca0899d2-2531-469e-b276-24093a29fead
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set ca0899d2-2531-469e-b276-24093a29fead
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c884ed4a84ed3c16
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=30aed0c0-fa06-41e7-a613-11f5a746f9b7 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 30aed0c0-fa06-41e7-a613-11f5a746f9b7
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=30aed0c0-fa06-41e7-a613-11f5a746f9b7 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=ca0899d2-2531-469e-b276-24093a29fead /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=273b6a20-9bea-4f8e-b225-57048126373a none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 276.8GB: boot/grub/core.img
 201.6GB: boot/grub/grub.cfg
 276.8GB: boot/initrd.img-2.6.32-24-generic
 276.7GB: boot/vmlinuz-2.6.32-24-generic
 276.8GB: initrd.img
 276.7GB: vmlinuz

```

My mate that helped me with all this has reminded me that there were two small seemingly insignificant partitions that may have something to do with this. We didn't actually change them or reformat them because they amounted to about 3.5G...

So let's now spend those exhausting days trying to work out how I could stuff up something that was meant to be simple... meanwhile I'll enjoy the beauty of sda5.

---

### Post by oldfred on 2011-01-09
Grub has you booting into sda7 and the install in sda5 looks like it only has room for  a minimal install. Each install has its own swap, so you also have two swaps. I would not necessarily recommend changing that.

If it is working that is fine, but sda5 is not really used. I keep several installs on my system.  You do have room to shrink your sda7 partition and make a shared NTFS partition if you want to share some data between windows & Ubuntu. I prefer not to write directly into other system partitions if I can avoid it for reliability.

I have multiple Ubuntu's - last install, current install, & next install for testing, but I keep all my data in two data only partitions. One data partition was from when I still used XP a lot, and has data I might want in both XP & Ubuntu including Firefox & Thunderbird profiles. So whatever I boot I have same bookmarks & email. 

My other /data partition is all the data folders in /home and some of the hidden data folders in /home, so my /home only has user settings. I then link each data partition into each system install. Then each system install can be small with the large partitions being data.

---

### Post by CaronMargarete on 2011-01-10
> **oldfred said:**
> Grub has you booting into sda7 and the install in sda5 looks like it only has room for  a minimal install. Each install has its own swap, so you also have two swaps. I would not necessarily recommend changing that.

If it is working that is fine, but sda5 is not really used. I keep several installs on my system.  You do have room to shrink your sda7 partition and make a shared NTFS partition if you want to share some data between windows & Ubuntu. I prefer not to write directly into other system partitions if I can avoid it for reliability.

I have multiple Ubuntu's - last install, current install, & next install for testing, but I keep all my data in two data only partitions. One data partition was from when I still used XP a lot, and has data I might want in both XP & Ubuntu including Firefox & Thunderbird profiles. So whatever I boot I have same bookmarks & email. 

My other /data partition is all the data folders in /home and some of the hidden data folders in /home, so my /home only has user settings. I then link each data partition into each system install. Then each system install can be small with the large partitions being data.

Thanks. I'll use sda7 and leave sda5 alone. Just seemed odd to me that there would be two but if there's no impact then no worries. 

Case closed. Thanks for all your help! You are one example of why I love Ubuntu so much!

---

