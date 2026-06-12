---
title: "Lost GRUB loader"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by cchaos on 2010-08-31
Hi again! :D

Ive installed Windows (both XP and 7) and lost my GRUB loader. Done a bit of goggling and found instructions on how to get it back, but unfortunate I appear to have a monitor that doesnt want to play ball with either the live CD of rescatux or Ubuntu 10.04 (before the 10.04.1 update) as the monitor is displaying that the sync is out of range (will grab a photo if required).

The situation gets worse: Im going to have to reformat my XP partition Im having problems with it - the SATA connections are in AHCI mode, and after slipstreaming in the required drivers for XP Im getting multiple copies of my sound card and now its crashing as soon as I enter windows. Needless to say Im going to enable native IDE and use the original CD as I think something else got added and that is why it is screwing around. And Windows 7 will have to be reinstalled unless theres a way of repairing the loader for that <-- irrelevant for here I know hence why I dont want that to be answered

So, with 2/3s of a "broken" computer, I think its time for a little "experiment"/ "lets break it even more" :lol: so heres my questions:

1. Will the Linux (ext3 and swap) partitions still boot (once the GRUB has been fixed) if I swap from ACHI to Native IDE?

2. Are there differences in screen resolution in 10.04 and 10.04.1? I am on a slow internet connection and dont really want to download it to "try it out". The live CDs of 9.04 and 9.10 (if I remember correctly) work, but they do not show my USB header card reader as it does in 8.10. I currently have 9.04 on CD in front of me (thanks to a friend of mine, who doesnt really enjoy Linux)

3. Back to the GRUB loader, is there a way of seeing which version of GRUB I have installed? Im pretty certain I upgraded to GRUB 2, but I honestly cannot remember

I am reluctance to format the ubuntu partition as I have had a few issues with ubuntu I have now "solved" [http://ubuntuforums.org/showthread.php?t=1563691](http://ubuntuforums.org/showthread.php?t=1563691) and [http://ubuntuforums.org/showthread.php?t=1563468](http://ubuntuforums.org/showthread.php?t=1563468) but as you can see I have the "fixes" posted exactly in case I do have to reformat

---

### Post by oldfred on 2010-08-31
When I installed a new motherboard I decided to try the ACHI mode. My Ubuntu booted just fine without any hiccups, but then XP did not work. I never have added drivers. I changed back to IDE mode both Ubuntu & XP worked again.

With multiple systems I run this just for my own info. It is very usefull for boot issues.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Karmic 9.10 64 bit installed without any issues on my system but Lucid required me to add nomodeset to get into a low video mode and then install nvidia drivers. Since then it has been very good.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa

---

### Post by cchaos on 2010-08-31
Thankyou for taking the time to read my thread :)

> **oldfred said:**
> When I installed a new motherboard I decided to try the ACHI mode. My Ubuntu booted just fine without any hiccups, but then XP did not work. I never have added drivers. I changed back to IDE mode both Ubuntu & XP worked again.
Thanks for answering that one. So it would appear that once Ive sorted out windows and the GRUB it should be fine :)

> **oldfred said:**
> With multiple systems I run this just for my own info. It is very usefull for boot issues.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.
Thanks for the link. I was looking at that thinking "should I use it?" :)

No need to tell me about code tags: Im forever telling newbies off for posting a huge log without a code(box) tag at where I am super moderator on a forum :) Though with the recent upgrade there, the spoiler tags are proving to have their use now. Anyway Im rabbiting on off topic.

The result.txt:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00740073

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    99,362,024    99,361,962   7 HPFS/NTFS
/dev/sda2          99,362,025   312,544,574   213,182,550   5 Extended
/dev/sda5          99,362,088   198,724,049    99,361,962   7 HPFS/NTFS
/dev/sda6         198,724,113   308,544,389   109,820,277  83 Linux
/dev/sda7         308,544,453   312,544,574     4,000,122  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2d892d89

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   208,379,114   208,379,052   7 HPFS/NTFS
/dev/sdb2         208,379,115   625,137,344   416,758,230   5 Extended
/dev/sdb5         208,379,178   416,758,229   208,379,052   7 HPFS/NTFS
/dev/sdb6         416,758,293   625,137,344   208,379,052   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BEC46B85C46B3EB1                       ntfs       Windows XP installed          
/dev/sda5        377E52A013268C43                       ntfs       Windows 7                     
/dev/sda6        e8897254-6a69-4dff-bf5d-8f11c6ea6b90   ext3                                     
/dev/sda7        e48a1fa0-f50f-4734-9017-e8fb2e990867   swap                                     
/dev/sdb1        5267653141834915                       ntfs       Phone stuff                   
/dev/sdb5        2E0F274C2AF0A71D                       ntfs       Music                         
/dev/sdb6        1BEF0905203A2B8A                       ntfs       SOF shared installs           

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER


=========================== sda6/boot/grub/menu.lst: ===========================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e8897254-6a69-4dff-bf5d-8f11c6ea6b90

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

title		Chainload into GRUB 2
uuid		e8897254-6a69-4dff-bf5d-8f11c6ea6b90
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Ubuntu 9.10, kernel 2.6.31-22-generic
uuid		e8897254-6a69-4dff-bf5d-8f11c6ea6b90
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 ro quiet splash
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid		e8897254-6a69-4dff-bf5d-8f11c6ea6b90
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 ro single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 9.10, kernel 2.6.28-19-generic
uuid		e8897254-6a69-4dff-bf5d-8f11c6ea6b90
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 ro quiet splash
initrd		/boot/initrd.img-2.6.28-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-19-generic (recovery mode)
uuid		e8897254-6a69-4dff-bf5d-8f11c6ea6b90
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 ro single
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.10, kernel 2.6.27-17-generic
uuid		e8897254-6a69-4dff-bf5d-8f11c6ea6b90
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 ro quiet splash
initrd		/boot/initrd.img-2.6.27-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.27-17-generic (recovery mode)
uuid		e8897254-6a69-4dff-bf5d-8f11c6ea6b90
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 ro single
initrd		/boot/initrd.img-2.6.27-17-generic

title		Ubuntu 9.10, memtest86+
uuid		e8897254-6a69-4dff-bf5d-8f11c6ea6b90
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set e8897254-6a69-4dff-bf5d-8f11c6ea6b90
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e8897254-6a69-4dff-bf5d-8f11c6ea6b90
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e8897254-6a69-4dff-bf5d-8f11c6ea6b90
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.28-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e8897254-6a69-4dff-bf5d-8f11c6ea6b90
	linux	/boot/vmlinuz-2.6.28-19-generic root=UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-19-generic
}
menuentry "Ubuntu, Linux 2.6.28-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e8897254-6a69-4dff-bf5d-8f11c6ea6b90
	linux	/boot/vmlinuz-2.6.28-19-generic root=UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 ro single 
	initrd	/boot/initrd.img-2.6.28-19-generic
}
menuentry "Ubuntu, Linux 2.6.27-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e8897254-6a69-4dff-bf5d-8f11c6ea6b90
	linux	/boot/vmlinuz-2.6.27-17-generic root=UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 ro   quiet splash
	initrd	/boot/initrd.img-2.6.27-17-generic
}
menuentry "Ubuntu, Linux 2.6.27-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e8897254-6a69-4dff-bf5d-8f11c6ea6b90
	linux	/boot/vmlinuz-2.6.27-17-generic root=UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 ro single 
	initrd	/boot/initrd.img-2.6.27-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e8897254-6a69-4dff-bf5d-8f11c6ea6b90 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=e48a1fa0-f50f-4734-9017-e8fb2e990867 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 120.8GB: boot/grub/core.img
 120.9GB: boot/grub/grub.cfg
 120.8GB: boot/grub/menu.lst
 120.9GB: boot/grub/stage2
 120.8GB: boot/initrd.img-2.6.27-17-generic
 120.8GB: boot/initrd.img-2.6.28-19-generic
 120.8GB: boot/initrd.img-2.6.31-22-generic
 120.8GB: boot/vmlinuz-2.6.27-17-generic
 120.8GB: boot/vmlinuz-2.6.28-19-generic
 120.8GB: boot/vmlinuz-2.6.31-22-generic
 120.8GB: initrd.img
 120.8GB: initrd.img.old
 120.8GB: vmlinuz
 120.8GB: vmlinuz.old
```
sda is windows XP, Windows 7 and Ubuntu with SWAP
sdb doesnt have any operating system installed on it: Ive formatted all of the partitions to NTFS (for windows sharing purposes)

> **oldfred said:**
> Karmic 9.10 64 bit installed without any issues on my system but Lucid required me to add nomodeset to get into a low video mode and then install nvidia drivers. Since then it has been very good.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
Sounds like a failsafe plan if I cant get the GRUB back (which I think I can do with everyones help)

---

### Post by Rubi1200 on 2010-08-31
According to the bootscript GRUB is not installed to the MBR.

Working from a LiveCD you can reinstall it:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Install GRUB to sda, mounting sda6 in the process.

For the rest; as oldfred has already advised.

---

### Post by cchaos on 2010-08-31
> **Rubi1200 said:**
> According to the bootscript GRUB is not installed to the MBR.

Working from a LiveCD you can reinstall it:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Install GRUB to sda, mounting sda6 in the process.
Thats probably as it is wiped out everytime you install Windows.

I assume that the install of GRUB2 will work no matter the GRUB version I had/have (though looking at it I would say that it was GRUB2)?

---

### Post by Rubi1200 on 2010-08-31
> **cchaos said:**
> Thats probably as it is wiped out everytime you install Windows.

I assume that the install of GRUB2 will work no matter the GRUB version I had/have (though looking at it I would say that it was GRUB2)?
Yes, Windows will overwrite GRUB when its bootloader is installed.

Karmic and later uses GRUB2, so as long as you have either a Karmic or Lucid CD you will be reinstalling GRUB2.

---

### Post by cchaos on 2010-08-31
> **Rubi1200 said:**
> Karmic and later uses GRUB2, so as long as you have either a Karmic or Lucid CD you will be reinstalling GRUB2.
Right. Just that I started out on 8.10 and upgraded through to 9.10  (sorry, I dont know their "codenames". Give me a Sony Ericsson phone and I will state its codename to you :lol:), but on the other hand I do recall seeing that page when I think I updated the GRUB.

I do apologise if I am being "over cautious" and asking more questions than are needed but I want to be 100% certain this is going to work before I attempt to do anything :)

---

### Post by Rubi1200 on 2010-08-31
Better to be cautious and get it right than have a system that is messed up and requires all kinds of fixing.

If you have other questions, feel free to ask.

:)

---

### Post by cchaos on 2010-08-31
Yeah, thats what Im thinking ;)

Anyway going back to topic, if I do install the GRUB 2 loader and it wasnt GRUB2 would it still work?

Will probably visit here with my laptop as I work on the desktop so no real worries there about not having a computer ;)

---

### Post by Rubi1200 on 2010-08-31
This should help answer a lot of your questions:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by cchaos on 2010-08-31
Bit the bullet. Followed the instructions and it worked :) (I used SIMPLEST - Copy GRUB2 Files from the LiveCD)

Last question:

Took a picture of the GRUB, how do I get rid of those "old" ubuntu entries that no longer work? I seem to recall some posts that said remove the old packages (completely) then update the grub (using *sudo update-grub* ) Am I correct?

---

### Post by oldfred on 2010-08-31
Uninstall extra kernels:-------------------------
In synaptic search for linux-image to choose to delete old ones
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

I like to keep two incase the new one has issues.

I also do not delete to often but modify grub to only show two.

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305 see #2
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by cchaos on 2010-09-01
Thanks for the links :)

All done and dusted (for now :lol:)

---

