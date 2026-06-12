---
title: "grub confusion"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by stevepoppers on 2010-07-03
I have Vista, Ubuntu, and Crunchbang installed. The Vista's kinda irrelevant, but I'm having trouble configuring grub across both Linux installs. I'm basically confused because I don't know which to use to configure it. Both list boot options in almost completely opposite orders. My Lucid default option is 0 (itself), CrunchBang says it's 5 (Lucid), and the actual default option is CrunchBang. I also think CrunchBang has Grub 1 installed as it's based on Jaunty and has different files, and I don't know what that means for configuration. While in CrunchBang, I installed startupmanager and configure it that way and it actually worked. I may just be missing a step in the process, but I would really like to understand which OS actually controls my Grub and how I should really be controlling my setup. I installed Lucid before CrunchBang, so Grub should be version 2 and maybe CrunchBang just doesn't know that is doesn't control it?

tl;dr Which OS controls my Grub and why wouldn't the boot default I set actually work?

---

### Post by wojox on 2010-07-03
Just reinstall Grub 2 from a live CD. [Grub 2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") .

Then boot into Ubuntu and run

```
sudo update-grub2
```

---

### Post by oldfred on 2010-07-03
Anyone with multiple installs and/or multiple drives should use this tool. I use it to document where everything is at before and after I make changes to my system.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by Rubi1200 on 2010-07-03
> **oldfred said:**
> Anyone with multiple installs and/or multiple drives should use this tool. I use it to document where everything is at before and after I make changes to my system.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

I have to say that I concur with oldfred's assessment of the situation. 

No disrespect to your knowledge and experience wojox, but I have seen too many posts already from people who ran into problems, were told to just reinstall GRUB only to discover that the problem lay somewhere else (e.g. disks incorrectly partitioned etc. etc.).

Better to play it safe and use the Bootscript before advising someone how to proceed.

---

### Post by stevepoppers on 2010-07-03
I may just want to install grub myself as per the first response for simplicity's sake. This could be interesting, though.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   179,590,634   179,588,587   7 HPFS/NTFS
/dev/sda2         179,591,168   199,120,895    19,529,728  83 Linux
/dev/sda3         199,125,736   976,773,119   777,647,384   5 Extended
/dev/sda5         209,616,120   970,599,104   760,982,985  83 Linux
/dev/sda6         970,606,592   976,773,119     6,166,528  82 Linux swap / Solaris
/dev/sda7         199,125,738   209,616,119    10,490,382  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3A240EDB240E99D1                       ntfs       ACER                          
/dev/sda2        90626350-fd24-4263-ba8f-f162df0ad4de   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        cdb66c8c-a462-4d8c-9304-f33adc619c70   ext4                                     
/dev/sda6        f7238468-d659-4da1-a9cf-8498b640a907   swap                                     
/dev/sda7        57a6197a-910b-425c-b37e-d3d3977e7667   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/sda1              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /home                    ext4       (rw)


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
search --no-floppy --fs-uuid --set 90626350-fd24-4263-ba8f-f162df0ad4de
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
search --no-floppy --fs-uuid --set 90626350-fd24-4263-ba8f-f162df0ad4de
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 90626350-fd24-4263-ba8f-f162df0ad4de
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=90626350-fd24-4263-ba8f-f162df0ad4de ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 90626350-fd24-4263-ba8f-f162df0ad4de
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=90626350-fd24-4263-ba8f-f162df0ad4de ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 90626350-fd24-4263-ba8f-f162df0ad4de
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=90626350-fd24-4263-ba8f-f162df0ad4de ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 90626350-fd24-4263-ba8f-f162df0ad4de
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=90626350-fd24-4263-ba8f-f162df0ad4de ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 90626350-fd24-4263-ba8f-f162df0ad4de
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=90626350-fd24-4263-ba8f-f162df0ad4de ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 90626350-fd24-4263-ba8f-f162df0ad4de
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=90626350-fd24-4263-ba8f-f162df0ad4de ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 90626350-fd24-4263-ba8f-f162df0ad4de
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 90626350-fd24-4263-ba8f-f162df0ad4de
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3a240edb240e99d1
	chainloader +1
}
menuentry "CrunchBang, kernel 2.6.28-13-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 57a6197a-910b-425c-b37e-d3d3977e7667
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=57a6197a-910b-425c-b37e-d3d3977e7667 ro quiet splash
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "CrunchBang, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 57a6197a-910b-425c-b37e-d3d3977e7667
	linux /boot/vmlinuz-2.6.28-13-generic root=UUID=57a6197a-910b-425c-b37e-d3d3977e7667 ro single
	initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "CrunchBang, memtest86+ (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 57a6197a-910b-425c-b37e-d3d3977e7667
	linux /boot/memtest86+.bin 
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
UUID=90626350-fd24-4263-ba8f-f162df0ad4de /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=cdb66c8c-a462-4d8c-9304-f33adc619c70 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=f7238468-d659-4da1-a9cf-8498b640a907 none            swap    sw              0       0
UUID=3A240EDB240E99D1 /media/sda1 ntfs-3g users 0 0

=================== sda2: Location of files loaded by Grub: ===================


  94.3GB: boot/grub/core.img
  96.5GB: boot/grub/grub.cfg
  97.6GB: boot/initrd.img-2.6.32-21-generic
  99.2GB: boot/initrd.img-2.6.32-22-generic
  99.6GB: boot/initrd.img-2.6.32-23-generic
  95.3GB: boot/vmlinuz-2.6.32-21-generic
  99.1GB: boot/vmlinuz-2.6.32-22-generic
  99.2GB: boot/vmlinuz-2.6.32-23-generic
  99.6GB: initrd.img
  99.2GB: initrd.img.old
  99.2GB: vmlinuz
  99.1GB: vmlinuz.old

=========================== sda7/boot/grub/menu.lst: ===========================

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
default		5

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
# kopt=root=UUID=57a6197a-910b-425c-b37e-d3d3977e7667 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=57a6197a-910b-425c-b37e-d3d3977e7667

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
# defoptions=quiet splash vga=771

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

title		CrunchBang, kernel 2.6.28-13-generic
uuid		57a6197a-910b-425c-b37e-d3d3977e7667
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=57a6197a-910b-425c-b37e-d3d3977e7667 ro quiet splash vga=771 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		CrunchBang, kernel 2.6.28-13-generic (recovery mode)
uuid		57a6197a-910b-425c-b37e-d3d3977e7667
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=57a6197a-910b-425c-b37e-d3d3977e7667 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		CrunchBang, memtest86+
uuid		57a6197a-910b-425c-b37e-d3d3977e7667
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=90626350-fd24-4263-ba8f-f162df0ad4de ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=90626350-fd24-4263-ba8f-f162df0ad4de ro single 
initrd		/boot/initrd.img-2.6.32-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=90626350-fd24-4263-ba8f-f162df0ad4de ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=90626350-fd24-4263-ba8f-f162df0ad4de ro single 
initrd		/boot/initrd.img-2.6.32-21-generic
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=57a6197a-910b-425c-b37e-d3d3977e7667 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=cdb66c8c-a462-4d8c-9304-f33adc619c70 /home           ext4    relatime        0       2
# swap was on /dev/sda6 during installation
UUID=f7238468-d659-4da1-a9cf-8498b640a907 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 104.0GB: boot/grub/menu.lst
 103.7GB: boot/grub/stage2
 104.3GB: boot/initrd.img-2.6.28-13-generic
 102.0GB: boot/vmlinuz-2.6.28-13-generic
 104.3GB: initrd.img
 102.0GB: vmlinuz
```

---

### Post by oldfred on 2010-07-03
Are you able to boot Ubuntu from the old grub menu.lst? If so you can just reinstall grub2 to the MBR from that boot.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
[COLOR=DarkRed]sudo grub-install /dev/sda[/COLOR]
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

You can install from the liveCD but do not have to. When you install from a working system to the MBR you do not have to mount the partition like you do with the liveCD.

---

### Post by stevepoppers on 2010-07-03
> **oldfred said:**
> Are you able to boot Ubuntu from the old grub menu.lst?

You mean with grub working as it is? Yes, I'm on Lucid right now. I can boot fine, I just couldn't get it to go to the default that I *thought* I was setting, which led to further confusion and my initial question.

I may try that, but as some said, I'd like to get some direct responses to the bit of code I posted. I mean, I'd rather not reinstall if that's not the problem.

---

### Post by oldfred on 2010-07-03
All you need to do is install grub2 from Ubuntu into the MBR to overwrite the old grub currently in the MBR.

---

### Post by Miljet on 2010-07-03
> Which OS controls my Grub and why wouldn't the boot default I set actually work?

This basic misconception seems to be the source of your confusion. None of your operating systems CONTROL Grub. Actually, it is more the other way around. You can have any number of Grub installs on your disk, but whichever Grub is installed in the MBR (Master Boot Record) of your hard disk determines which Grub files load.

That is why OldFred suggested that you reinstall Grub2 in your MBR.

---

### Post by stevepoppers on 2010-07-03
Ok, I'll (re)install Grub 2 from inside Lucid.

If the installed systems don't control Grub, then why do I have configuration files for Grub inside them? Or are the directories symbolic in some way? Where in my partition table is the MBR?

I guess CrunchBang installed Old Grub with itself, huh?

And I still don't see why changing the default in the relevant config files made no actual difference when booting.

---

### Post by -kg- on 2010-07-04
> **Miljet said:**
> This basic misconception seems to be the source of your confusion. None of your operating systems CONTROL Grub. Actually, it is more the other way around. You can have any number of Grub installs on your disk, but whichever Grub is installed in the MBR (Master Boot Record) of your hard disk determines which Grub files load.

That is why OldFred suggested that you reinstall Grub2 in your MBR.

True.  That's why, when describing it, I usually say that the installation which installed GRUB in the MBR ***"_OWNS_"*** GRUB, although actually, nothing owns or controls anything.

The code segment installed by the installation which "owns" GRUB is actually a very small part of GRUB...GRUB Stage One.  It looks to subsequent stages of GRUB to display the "menu.lst" file, which resides in the /boot directory, either on the root partition, or it can be on a separate /boot partition.

When you select an OS from the menu, GRUB stage one will look to this same directory for information on which partition to look in to continue booting your selection.  The MBR is much too small (512 byte) to contain all this code and information.  That is why, if you delete the partition that owns the segment in the MBR, you will render your system completely unbootable, until you install GRUB from another installation. GRUB Stage 1 needs its subsequent Stage 1.5 and/or 2 for further information.

This boot-up chain of events is well described at the following link:

[http://www.dedoimedo.com/computers/grub.html#mozTocId616834]("http://www.dedoimedo.com/computers/grub.html#mozTocId616834")

> Where in my partition table is the MBR?

Actually, your Partition Table is in the MBR.  The MBR isn't really a Partition.  The MBR is the very first portion of your physical hard drive that contains the Partition Table and a bootloader, if you installed one there.  The following gives a good description of the MBR:

[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm]("http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm")

It also describes the reason that there is a "4 Primary Partition" limit on hard drives, which I didn't precisely know before.

---

