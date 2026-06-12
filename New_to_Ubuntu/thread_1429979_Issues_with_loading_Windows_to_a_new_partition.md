---
title: "Issues with loading Windows to a new partition"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by SumthingWicked5 on 2010-03-14
I made a new partition on my hard drive to add Windows. I installed it and everything went fine. Then, as expected, when I restarted, I lost my Grub loader.Just windows stared. So, I googled how to reinstall my grub and I found [this site]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

It walked me through pretty well and I did all the steps.

Once I restart, my grub loader came up and offered me a few options (not Windows, but whatever, that's not the issue yet) I chose the top option, because usually that's my most recent functioning load of Ubuntu (just a guess, but it's always the one I've chosen before and it works)

It goes black, I get the white Ubuntu symbol in the center of the screen for a few seconds, and then nothing. Just blank black screen. Forever. Help!

---

### Post by bradmayne04 on 2010-03-14
I'm wondering if this is your first install of linux on the computer in question????  Did you do this w/ WUBI or a live disk (.iso)??  A network install?  Lemme know!

---

### Post by SumthingWicked5 on 2010-03-14
I essentially started fresh. I had loaded Hardy before, but when I tried to upgrade, I did it wrong, so I had to format the drive. I loaded Karmic first, and then made the partition using GParted on my liveCD, then loaded Windows. Then went back in with my liveCD to try to fix my loader.

---

### Post by SumthingWicked5 on 2010-03-14
When I boot my system I get my BIOS stuff, and then in stead of auto booting to Ubuntu, or Windows, which is what it used to do, I get a list

Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
Ubuntu, Linus 2.6.31-19-generic 
etc. etc.

When I used to have Hardy dual booted, Windows would be at the bottom of this list, but it's not. 

Hitting Enter on the top (2.6.31-20 generic) takes me to the Ubuntu symbol which used to precede loading, and then just a black screen. Though my monitor is still receiving the black,  since it doesn't say "no signal" or cut to standby.

Please help. I have to steal my girlfriend's laptop to even be on here, and I'd really rather not have to format my partition again. I just got it set up the way I like it.

---

### Post by wilee-nilee on 2010-03-14
Did you run Karmic after resizing it for the W7 install.

Here is a little better wiki for grub2. Step 1 in #11 reinstalling grub2 gas worked for me every time.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by presence1960 on 2010-03-14
I would rather not guess or poke in the dark, need more detailed info about your machine's setup. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by SumthingWicked5 on 2010-03-14
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8af88af8

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   259,032,059   259,031,997  83 Linux
/dev/sda2    *    259,032,060   300,495,824    41,463,765   7 HPFS/NTFS
/dev/sda3         300,495,825   312,576,704    12,080,880   5 Extended
/dev/sda5         300,495,888   312,576,704    12,080,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        60425434-7adf-4444-91b7-8a970070abda   ext4                                     
/dev/sda2        CEBCCB9BBCCB7C89                       ntfs                                     
/dev/sda5        38d6066d-c676-429e-9209-40710b5a62c7   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-20-generic root=/dev/sdb1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-20-generic root=/dev/sdb1 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-19-generic root=/dev/sdb1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-19-generic root=/dev/sdb1 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
UUID=60425434-7adf-4444-91b7-8a970070abda /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=38d6066d-c676-429e-9209-40710b5a62c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .9GB: boot/grub/core.img
  42.3GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .7GB: boot/initrd.img-2.6.31-19-generic
   1.5GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-19-generic
   1.2GB: boot/vmlinuz-2.6.31-20-generic
   1.5GB: initrd.img
    .7GB: initrd.img.old
   1.2GB: vmlinuz
    .6GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```
[CODE][CODE]
```[/CODE][/CODE]

---

