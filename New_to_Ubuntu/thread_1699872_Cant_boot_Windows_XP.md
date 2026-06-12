---
title: "Cant boot Windows XP"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by thatoneguy99 on 2011-03-04
Could someone please help me with configuring GRUB to load Windows. I have searched and cant find a definitive answer for my situation. I had Windows instlalled and running perfectly. When I originally installed Windows I made a seperate partition on the hard drive with 100GB. After Windows was installed and running fine I installed Kubuntu 10.10 using a Live CD onto that 100GB partition on the same hard drive as Windows. The Kubuntu install prompted me to install GRUB to the MBR ,which I did, now when the computer boots I didnt have Windows on the GRUB menu. I have since edited the menu.lst file and now I have Windows in the list but it gives me an error when I try to boot it. Could someone give me the procedure to see which partition (e.g HD0,1 or 2 or 3 or whatever it is) my Windows is installed on. Then the correct typing to put into the menu.lst file to load my Windows. Thank you in advance. Also a link to another post with this information in it already would work also.

---

### Post by thatoneguy99 on 2011-03-04
I am not at home with my computer at the moment so I apologize. I am not able to actually do anything or try anything. I cant even tell you what the error was when GRUB tried to load Windows. I will get on my computer as soon as I get home and get this information to you...thank you very much for ANY information.

---

### Post by Rubi1200 on 2011-03-04
Hi and welcome to the forums :)

At the next opportunity, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by thatoneguy99 on 2011-03-04
Thank you for this information. I will do it when I get home. Which is soon hopefully. Ive been sitting here at my desk all morning doing nothing...just waiting to go home.

---

### Post by thatoneguy99 on 2011-03-04
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557  83 Linux
/dev/sda2         204,796,681   781,401,599   576,604,919   f W95 Ext d (LBA)
/dev/sda5         204,796,683   781,401,599   576,604,917   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        d689819f-32fb-424b-a88a-00bc3b9726d5   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        86609CE2609CDA6F                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
# hiddenmenu

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
# kopt=root=UUID=d689819f-32fb-424b-a88a-00bc3b9726d5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d689819f-32fb-424b-a88a-00bc3b9726d5

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

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		d689819f-32fb-424b-a88a-00bc3b9726d5
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=d689819f-32fb-424b-a88a-00bc3b9726d5 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		d689819f-32fb-424b-a88a-00bc3b9726d5
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=d689819f-32fb-424b-a88a-00bc3b9726d5 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		d689819f-32fb-424b-a88a-00bc3b9726d5
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		d689819f-32fb-424b-a88a-00bc3b9726d5
kernel		/boot/memtest86+.bin

title           Windows XP All Day
root            (hd0,1)
makeactive
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d689819f-32fb-424b-a88a-00bc3b9726d5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d689819f-32fb-424b-a88a-00bc3b9726d5
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d689819f-32fb-424b-a88a-00bc3b9726d5
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d689819f-32fb-424b-a88a-00bc3b9726d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d689819f-32fb-424b-a88a-00bc3b9726d5
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d689819f-32fb-424b-a88a-00bc3b9726d5 ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d689819f-32fb-424b-a88a-00bc3b9726d5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d689819f-32fb-424b-a88a-00bc3b9726d5
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

menuentry "Windows XP you punk mother fucker¨{
    insmod ntfs
    set root=(hd0,msdos2)
    search --no-floppy --fs-uuid --set 4a6077fc6077ed57
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/40_custom ###
### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d689819f-32fb-424b-a88a-00bc3b9726d5 /               ext4    errors=remount-ro 0       1

=================== sda1: Location of files loaded by Grub: ===================


  81.7GB: boot/grub/core.img
  43.1GB: boot/grub/grub.cfg
  36.7GB: boot/grub/menu.lst
  81.7GB: boot/grub/stage2
    .3GB: boot/initrd.img-2.6.35-22-generic
  81.7GB: boot/vmlinuz-2.6.35-22-generic
    .3GB: initrd.img
  81.7GB: vmlinuz
```

---

### Post by thatoneguy99 on 2011-03-04
I just realized that the menu.lst and grub.cfg was already in the results so im removing the menu.lst from this post.

---

### Post by thatoneguy99 on 2011-03-04
One more tidbit of information. It doesnt matter what I put in grub.cfg or the /etc/default/grub. I changed some stuff in the grub default folder such as hidden menu and timeout and nothing changed on the GRUB boot menu when i rebooted. It only changes when I change something in menu.lst. Not sure if that helps but I just wanted to let you know. Ill be back shortly to tell you the error I get when trying to load Windows from grub with the way I have it now.

---

### Post by thatoneguy99 on 2011-03-04
error 12: invalid device requested

---

### Post by thatoneguy99 on 2011-03-05
After much research and tinkering I finally decided to redo the whole stinking thing. I stole a harddrive out of an old laptop and installed the OS's seperately onto those hard drives. Making damn sure that windows was installed on the first partition of the hard drive and that GRUB was installed to the mbr of the hard drive Kubuntu was installed on. Selected the Kubuntuhard drive as the first boot device in my BIOS and loaded up kubuntu. Once kubuntu was loaded I updated grub with terminal. Rebooted and the option for windows was in the grub boot menu. Windows booted up perfectly. Lots of headache but I wasn't giving up.

---

