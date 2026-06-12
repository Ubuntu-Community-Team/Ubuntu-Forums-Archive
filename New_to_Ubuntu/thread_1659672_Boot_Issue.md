---
title: "Boot Issue"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Razorback on 2011-01-04
I have installed Ubuntu 10.04 on a hard drive by itself on a SATA connection.  It used to boot fine but now it hangs with a blank screen and a blinking cursor.  I have two other hard drives installed on the primary IDE connector - which has Windows XP installed on it and it boots fine when the bios is directed at it.  But if I change the bios to boot on the Ubuntu drive it hangs.  I have two SATA connectors - one with the hard drive with Ubuntu installated and one with a DVD drive.  I have tried swapping the SATA connectors as I recently disconnected everything to move some stuff around.  I have booted a live CD session and see the Ubuntu hard drive with no problem and can explore it.  It also show up fine in the bios.  I am confused why it worked fine before and now it is giving me problems.  Hardware is listed below.  Any help would be appreciated.

---

### Post by Hippytaff on 2011-01-04
Can you post the results.txt by running [this script]("http://sourceforge.net/projects/bootinfoscript/") from the liveCD environment.
 
Also, what graphics card do you have and have you upgraded recently?

---

### Post by Razorback on 2011-01-04
I will try the script when I get home tonight.  I have been using the same vid card - PNY 7800GS.  I was using Ubuntu exclusively so I was not dual booting.  The hardware arrangement is still the same as far as connections.  I mentioned the SATA connectors because I thought reconnecting those devices on the wrong connector might confuse the PC when booting but it did not make any difference.

---

### Post by Razorback on 2011-02-25
A little delayed but here is my boot info script.  One thing I see is there is no boot asterisk on the Ubuntu drive.  I want to keep the drives separate (Windows and Ubuntu) and boot either from the bios.  Do I need to load Grub on the Ubuntu drive.
Thanks

```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/mapper/pdc_cachbgdjcj and looks on 
    the same drive in partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_cachbgdjcj1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   150,294,527   150,292,480  83 Linux
/dev/sdc2         150,296,574   156,301,311     6,004,738   5 Extended
/dev/sdc5         150,296,576   156,301,311     6,004,736  82 Linux swap / Solaris


Drive: pdc_cachbgdjcj ___________________ _____________________________________________________

Disk /dev/mapper/pdc_cachbgdjcj: 80.0 GB, 80026271744 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_cachbgdjcj1   *             63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_cachbgdjcj1 12ECD36CECD3489D                       ntfs       Data Disk 1                   
/dev/mapper/pdc_cachbgdjcj: PTTYPE="dos" 
/dev/sda1        BEC45768C4572247                       ntfs                                     
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        12ECD36CECD3489D                       ntfs       Data Disk 1                   
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdc1        0e4b95d2-8158-42fa-8eb4-8a4a4da9970c   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        08dc311b-3c44-4187-9e9d-53786eb73da5   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=08dc311b-3c44-4187-9e9d-53786eb73da5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
  21.9GB: boot/grub/grub.cfg
  26.0GB: boot/initrd.img-2.6.32-21-generic
  26.8GB: boot/initrd.img-2.6.32-22-generic
  26.8GB: boot/initrd.img-2.6.32-23-generic
  26.8GB: boot/initrd.img-2.6.32-24-generic
  26.9GB: boot/initrd.img-2.6.32-25-generic
  25.9GB: boot/vmlinuz-2.6.32-21-generic
  26.0GB: boot/vmlinuz-2.6.32-22-generic
  26.7GB: boot/vmlinuz-2.6.32-23-generic
  26.8GB: boot/vmlinuz-2.6.32-24-generic
  26.9GB: boot/vmlinuz-2.6.32-25-generic
  26.9GB: initrd.img
  26.8GB: initrd.img.old
  26.9GB: vmlinuz
  26.8GB: vmlinuz.old

```

---

### Post by Razorback on 2011-02-25
Never mind - got it fixed.

---

### Post by Hippytaff on 2011-02-28
How did you fix it (so others with the same issue can benefit) and because I'm nosey ;-)

---

### Post by Razorback on 2011-02-28
I found that Grub 2 was not installed on the drive.  So, I booted the Live CD, mounted the hard drive and installed Grub.  Then, updated Grub and it worked like a charm.  Only thing now is when I update Grub, it is not finding my Windows XP install.  Not sure what is going on there.  Still working on that - hoping to get that fixed so I don't have to change drives in the bios.

---

### Post by Hippytaff on 2011-02-28
Good work!!

When you say update grub am I right in understanding doing```
sudo update-grub
```?

---

### Post by Razorback on 2011-02-28
Yes, that is correct.  Now, if I can only find out why it is not finding my Windows install.....  Any ideas?

---

### Post by Hippytaff on 2011-02-28
I have read that if doing ```
sudo update grub
``` doesn't work you might need to do ```
sudo grub-install /dev/sda
``` though I've never had to do this before. Maybe posting the results.txt of the bootinfo script again might help!?

---

### Post by Razorback on 2011-02-28
Well, the reason I installed Grub on the Ubuntu drive is previously I was dual booting with Grub being on the Windows drive.  Then, I reinstalled Windows on a different drive when I started having problems with a previous Windows install.  So, looking at my boot info - sdb was the previous Windows install that is now a data disk, sda is my current Windows install and sdc is the same Ubuntu install.  Funny thing is Grub is still on sdb so I wasn't sure if that was causing issues.  Also, it doesn't hurt having the Windows bootloader on sda, correct?  Shouldn't Grub on the Ubuntu install find Windows on sda with the update-grub command?

---

### Post by Hippytaff on 2011-02-28
It should find is yes. Os prober usually does a good job - your sure windows is still there?

edit -> two seperate HHDs?

---

### Post by Razorback on 2011-02-28
Yep, Windows and Ubuntu both boot fine when the bios is directed at either hard drive.  And yes, they are on separate hard drives.

---

### Post by Hippytaff on 2011-02-28
As long as the bios is set tp boot from the ubuntu HDD first. Doing ```
sudo update-grub
``` should work. Grub will need to be on the ubuntu Hard Drive

---

### Post by Razorback on 2011-02-28
That is how I have it setup right now.  Boot to Ubuntu HDD in bios. Ran update-grub a couple of times after rebooting but to no avail.  Grub is on the Ubuntu drive.

---

### Post by Hippytaff on 2011-02-28
The only thing I can suggest is posting the results of the bootinfo script again to see where everything is.

---

### Post by Razorback on 2011-02-28
I will do that again when I get home from work this evening.  Thanks for the replies.

---

### Post by Hippytaff on 2011-02-28
righo...no probs

---

### Post by Razorback on 2011-02-28
```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   150,294,527   150,292,480  83 Linux
/dev/sdc2         150,296,574   156,301,311     6,004,738   5 Extended
/dev/sdc5         150,296,576   156,301,311     6,004,736  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BEC45768C4572247                       ntfs                                     
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        12ECD36CECD3489D                       ntfs       Data Disk 1                   
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdc1        0e4b95d2-8158-42fa-8eb4-8a4a4da9970c   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        08dc311b-3c44-4187-9e9d-53786eb73da5   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Oblivion          udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sda1        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/Data Disk 1       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=0e4b95d2-8158-42fa-8eb4-8a4a4da9970c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 0e4b95d2-8158-42fa-8eb4-8a4a4da9970c
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=08dc311b-3c44-4187-9e9d-53786eb73da5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  26.0GB: boot/grub/core.img
  26.2GB: boot/grub/grub.cfg
  26.0GB: boot/initrd.img-2.6.32-21-generic
  26.8GB: boot/initrd.img-2.6.32-22-generic
  26.8GB: boot/initrd.img-2.6.32-23-generic
  26.8GB: boot/initrd.img-2.6.32-24-generic
  26.9GB: boot/initrd.img-2.6.32-25-generic
  27.0GB: boot/initrd.img-2.6.32-28-generic
  25.9GB: boot/vmlinuz-2.6.32-21-generic
  26.0GB: boot/vmlinuz-2.6.32-22-generic
  26.7GB: boot/vmlinuz-2.6.32-23-generic
  26.8GB: boot/vmlinuz-2.6.32-24-generic
  26.9GB: boot/vmlinuz-2.6.32-25-generic
  26.9GB: boot/vmlinuz-2.6.32-28-generic
  27.0GB: initrd.img
  26.9GB: initrd.img.old
  26.9GB: vmlinuz
  26.9GB: vmlinuz.old

```

---

### Post by Hippytaff on 2011-03-01
Looks like grub is installed on sdb (which looks to be a windows partition) and sdc. Are you using 3 seperate HDD's? you have sda, sdb and sdc. Not sure whats happening here. But you only need geyb to be on the same partition as ubuntu (which appears to be sdc)

---

### Post by Razorback on 2011-03-01
Yeah, I saw where sdb had grub on it too.  It was used previously as a Windows install that had issues.  I then reinstalled Windows on sda and moved backup data to sdb.  I believe that was the old Grub used for dual booting when Windows was on it.  I thought about uninstalling Grub from sdb.  What do you think?  Thanks.

---

### Post by Hippytaff on 2011-03-01
I would remove grub from sdb and see if that allows the corret grub on sdc to do it's thing. I've read that the grub on the same partition HDD as ubuntu needs to be the one that finds windows and controls the boot process

---

### Post by Razorback on 2011-03-01
I will give that a shot tonight.  I guess when you muck around with installations you have artifact stuff left over.

---

### Post by Hippytaff on 2011-03-01
Crud and fluff yeah. The number of times I've killed my ubuntu you would not belive - my best one was removing python. That was wise :roll:
 
Let me know how it goes :-)

---

### Post by Razorback on 2011-03-02
Well, I did some changes to the system.  First, I blew away the partition on sdb and reformatted it.  But Grub 2 still showed up in the boot script.  Sorry, didn't get a chance to post it.  Funny thing is, if you look at my first boot script, a device shows up at the bottom which is /dev/mapper/.....  I wasn't sure what that was but looked around on the net and found it had to do with RAID.  I am not running RAID - did several years ago but removed it and set things up normally.  I guess I am wondering does the RAID configuration get written somehow to the hard drives and remain even though they have been repartitioned and reformatted?  Anyway, it has been intriguing.  Next thing we be to remove Grub2 and reinstall, I guess.

---

### Post by Razorback on 2011-03-03
Thanks Hippytaff for the help and input!

---

### Post by Hippytaff on 2011-03-03
Your welcome - Glad you sorted it. How did you sort it though? so others with the same issue can benefit, and I am intruiged :-)

---

### Post by Razorback on 2011-03-03
My cmos battery had to be changed a little while ago.  With bios defaults, the onboard Promise RAID controller gets enabled.  dmraid must have gotten enabled when Ubuntu was started and from that point it was affecting Grubs ability to find Windows.  I made sure the RAID controller was disabled in the bios and then removed the dmraid setup on the IDE drives.  Those were the ones with the /device/mapper/pdc... entries.  Anyway, once done, I updated Grub and it found Windows and is working fine.  Funny though, I still have Grub showing up on sdb and sdc but it isn't affecting the dual boot.  I will still uninstall it.  It bugs me...but I am not OCD about it. :)  

[http://osdir.com/ml/linux.kernel.device-mapper.devel/2007-04/msg00014.html](http://osdir.com/ml/linux.kernel.device-mapper.devel/2007-04/msg00014.html)

---

### Post by Hippytaff on 2011-03-03
Excellent :-D

---

