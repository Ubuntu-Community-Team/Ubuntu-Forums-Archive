---
title: "Dual boot XP &amp; Ubuntu 9.10 upgraded to Ubuntu 10.04"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by zeckdikalajingga on 2010-05-10
Hi there...

i can't boot my computer at all after i shut it down.
last couple days before, when i open my 9.10 ubuntu it work as usual, i like it... however there is something happen which i do not have control with it, the upgrading system which means it upgraded itself to ubuntu 10.04... i was very glad knowing that this is the latest! wow! i even told my friends that ubuntu have upgraded. the next day when i open my computer i found that my computer does not shows any features on screen, its just black. the CPU running but the screen is black. what i did after that was, i push the On button at the CPU for a few second to put off the CPU and after that i turn it on again to get to bios. after that i save & exit bios to let it run, but still not working.

my computer is : 
intel pentium 4, 1.6 ghz, 160 gb IDE hard disk, 2gb DDR1 RAM. Dual boot XP 32 bit & Ubuntu 9.10

i am very-very new to this. please help me.

---

### Post by narendraD on 2010-05-10
Well  The System does not upgrade itself. This has to be done manually. How do you know it has updated to 10.04?

---

### Post by N8N on 2010-05-10
I bet you have intel video...  known bug... boot into safe mode from GRUB and start your window manager with "safe" graphics...  AFAIK no fix yet

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/568779")

once you're booted, fire up a terminal and do this

sudo cp /etc/X11/xorg.conf.failsafe  /etc/X11/xorg.conf 

that will force your machine to use the failsafe graphics settings even on a normal boot.  then whenever a fix is released you'll have to reconfig.  I bet this is your problem

good luck

nate

(also waiting for the fix, but 10.04 is pretty good on my other machine with nvidia graphics)

---

### Post by cap10Ibraim on 2010-05-11
Did you try to boot with the live CD ? did you get a blank screen too ?

---

### Post by zeckdikalajingga on 2010-05-11
Hi again...

i dont know if i have done anything right or wrong... when last time the Ubuntu 9.10 upgraded by itself, i just follow its instructions and after that my computer restarted i see the purple screen... and the features are exactly like Ubuntu 10.04, that is how i know it was ubutu 10.04...

i have not yet tried the live cd booting because when i go to the BIOS i cannot configure it to boot to CD ROM drive.

however i have successfully open the ubuntu 10.04 by setting up my BIOS, this is the steps:

1) BIOS screen --> select "Advance"
2) go to "chip configuration"
3) select "onboard VGA", then "Enabled"
4) select "graphic Aperture Size", then "256MB"
5) go back by pressing "esc"
6) go to "PCI Configuration"
7) select "PCI/VGA Palette snoop", then "Enabled"
8) select "Primary VGA BIOS", then "Onboard VGA"
9) save changes & exit
10) there you go... it works

but the other problems that i am facing now is... i cannot open my window XP. when i open XP it become black screen again... #(

---

### Post by oldfred on 2010-05-11
When you upgraded did it present a checkbox (s) and tell you to install to all drives, but you also checked all partitions?

IF so this is the fix.
Fix for most, a few have other issues:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If not then we will need a copy of the boot_info script refered to in above link.

---

### Post by zeckdikalajingga on 2010-05-11
> **oldfred said:**
> When you upgraded did it present a checkbox (s) and tell you to install to all drives, but you also checked all partitions?

IF so this is the fix.
Fix for most, a few have other issues:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If not then we will need a copy of the boot_info script refered to in above link.


the problem are not yet solved for xp, but for the ubuntu 10.04, yes it solved. but, may be because of the xp cannot boot, i can't even boot anything. so, the screen remain black again. maybe i need to plug out the power source plug for a day then start my computer tomorrow...

---

### Post by zeckdikalajingga on 2010-05-12
Hi again..

THE PROBLEM OF UBUNTU 10.04 ARE NOW SOLVED BUT MY XP STILL NOT WORKING, MAYBE THE BIOS... I DONT KNOW.



I'VE TYPED THIS TO GET THE BOOT SCRIPT.

uzaini@uzaini-desktop:~$ sudo bash Downloads/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sdb1 for information... 
Finished. The results are in the file RESULTS1.txt located in /home/uzaini/Downloads
uzaini@uzaini-desktop:~$ 




THEN I OPEN THE FOLDER... THIS IS WHAT IT SHOWS...




                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 208017434 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 208014082 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 208017690 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS
/dev/sda2         156,280,320   312,576,704   156,296,385   f W95 Ext d (LBA)
/dev/sda5         156,280,383   207,736,514    51,456,132   7 HPFS/NTFS
/dev/sda6         207,736,578   308,207,024   100,470,447  83 Linux
/dev/sda7         308,207,088   312,576,704     4,369,617  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 249     3,967,487     3,967,239   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C0C80A3BC80A2FE8                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        12ACD564ACD542C1                       ntfs                                     
/dev/sda6        fec39805-5e7b-4d6b-9bc6-810b047d7271   ext4                                     
/dev/sda7        362e97f2-eea1-4bee-bb00-631ff34683a1   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6664-6134                              vfat       ZECK                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set fec39805-5e7b-4d6b-9bc6-810b047d7271
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set fec39805-5e7b-4d6b-9bc6-810b047d7271
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fec39805-5e7b-4d6b-9bc6-810b047d7271
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=fec39805-5e7b-4d6b-9bc6-810b047d7271 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fec39805-5e7b-4d6b-9bc6-810b047d7271
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=fec39805-5e7b-4d6b-9bc6-810b047d7271 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fec39805-5e7b-4d6b-9bc6-810b047d7271
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=fec39805-5e7b-4d6b-9bc6-810b047d7271 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fec39805-5e7b-4d6b-9bc6-810b047d7271
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=fec39805-5e7b-4d6b-9bc6-810b047d7271 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fec39805-5e7b-4d6b-9bc6-810b047d7271
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fec39805-5e7b-4d6b-9bc6-810b047d7271
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c0c80a3bc80a2fe8
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=fec39805-5e7b-4d6b-9bc6-810b047d7271 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=362e97f2-eea1-4bee-bb00-631ff34683a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 106.5GB: boot/grub/core.img
 108.9GB: boot/grub/grub.cfg
 107.5GB: boot/initrd.img-2.6.31-20-generic
 107.8GB: boot/initrd.img-2.6.32-22-generic
 108.1GB: boot/vmlinuz-2.6.31-20-generic
 107.5GB: boot/vmlinuz-2.6.32-22-generic
 107.8GB: initrd.img
 107.5GB: initrd.img.old
 107.5GB: vmlinuz
 108.1GB: vmlinuz.old

---

### Post by oldfred on 2010-05-12
You have grub in the windows boot sector. The fix is in the link I posted before #6.

---

