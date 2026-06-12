---
title: "GRUB not showing after 10.04 install"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by RapidDissent on 2010-08-19
I feel bad making this thread, as I'm sure it's been answered elsewhere. It's not as though I've not been looking; may be that I'm asking the wrong question =-/

All right; so I have a windows 7 ultimate 64-bit installation on my system drive, and I've installed 10.04 on another partition of the drive. Because I want a /home partition, I used the manual option to configure my drives (I'm sure this is the problem...), and as the title indicates, after the install completes and the system is restarted, Windows just boots right up. 

Possibly related; on loading the live CD, it immediately tells me that the installer has encountered a critical / unrecoverable error, and that it's just going to hand off to the live CD so I can fix the problem (little does it know... heh). After that, Ubuntu seems to install fine, so I didn't really pay much attention.

On a 500Gb drive, 350 are for Win7, 100 are for /home, .5 are for /boot (first logical partition), 1Gb for /swap and ~30 for /. All applicable partitions are ext4.

Did I screw up the partitions? Do I need to make a Super GRUB Boot Disk and run that?


EDIT: Goofing with it another hour, and relegating myself to formatting my win7 into oblivion, I think I may have found out what I was doing wrong. I have 2 storage drives on the system, and on the very last step (summary of install) of the installation, there is an 'advanced' button, wherein is an option to select install location of the boot loader. For some reason, it was auto-selecting my largest drive, indicating there's a win7 loader present (o.O the hell?). 

SO! Setting the proper install point for GRUB, and setting the boot partition to a primary instead of a logical partition, I think I've got this figured out.


EDIT 2: Okay... that didn't work, nor has anything I've found online, including [this]("http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html"). Looked like the perfect newbie install guide, and aside from using GParted instead of the installer's partitioning tool and the boot partition, I was doing everything they suggested. 

After having installed Ubuntu yet again, this time with his / her layout, I'm still not seeing GRUB show up at startup. Pretty sure I'm just not setting the boot manager's location correctly. To correct this, I downloaded Super GRUB Disk, and have been trying that. It's unintuitive, but I'm told it is the 'bee's knees' as far as boot management goes... doesn't seem to be doing much for me =-/

Intuition is saying that the boot manager is still installed in the wrong location, thus it's never called on at the proper time, but is detectable by Super GRUB. Going to reinstall... the entire, freaking, system, AGAIN, so I can get at the advanced options to install the boot manager elsewhere. Before I was trying to put it on a boot partition, then I went back to default as the other guide indicated I should. Now I'm going to install on the first partition of the system drive, and hope the MBR is there.

---

### Post by corrytonapple on 2010-08-19
So you solved your own problem? If so, mark this thread as solved.

---

### Post by RapidDissent on 2010-08-19
No, it is not solved. My question seems to be boiling down to:

"Where do I install the boot manager on my system?"

2 hours on google and this problem which is 1 step away from being a non-issue is still eluding me. Trial and error is taking all night, due to the number of partition schemes and install locations I've tried. 

[RANT]
I know I'm using advanced options that are out of my league, but seriuosly, why am I unable to find a clear, concise, _complete_, guide on how to use them? 90% say "we'll go with the default partition scheme", and the other 10% fail to explain the boot manager, and where you're looking to install them.
[/RANT]

Current drive configuration (sdb2 is no longer present; indicated I did not need it in the link in the first post):

sda1- ntfs- 1.5TB - storage drive

sdb1- ntfs- 350GB - Win7 Partition
******Earlier configuration*****
sdb2- ext4- 0.1GB- /boot
*****/Earlier configuration*****
sdb5- ext4- 35GB - /
sdb6- swap- 6GB - Swap space
sdb7- ext4- ~100GB- /home

sdc1- ntfs- 1TB- storage drive

---

### Post by corrytonapple on 2010-08-19
Did you try this:
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+basics](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+basics)
He might have your issue in there. Also, hitting shift on most computers will bring up GRUB so you can select your os.

---

### Post by garvinrick4 on 2010-08-19
Always in page 8 of install in advance tab put your boot in sda or if you want sdb and so on. Never put in sda1 or sda5 or sdb1 or sdb5 and so on just in sda or sdb whichever you want to boot from. Here is a link that you can use in a live cd of Ubuntu and post on this thread and will be able to see what is happening. Lots of help will come if you post this.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Just download this to desktop and use this code below in terminal and a text file will appear on your desktop that will tell what is happening.

```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by wilee-nilee on 2010-08-19
Post the boot script in my signature in code tags as described.

---

### Post by RapidDissent on 2010-08-19
OOOHHHHHH-KAY!

Installed GRUB on the LIveCD, opened the shell to find the stage1 files. Error 15 Q.Q

Cursed, cried, laughed, more crying... LOTS more cursing.

The fact that the installer was auto-selecting sda to install the boot loader was intriguing, so I decided to reinstall both OS's on a freshly reformatted drive with the 2 storage drives disconnected. As the LiveCD loaded so I could format my drive, I humored myself and restarted w/o the CD to see if anything would load.

The GRUB frontend came up, with all the expected options present. 0.O

........ BIOS setting?... maybe? What the bloody hell?


EDIT: Just popped into make that reply, and missed the 2 new posts (sorry, it's been a slow thread, thus far). Should I still run the bootinfo script? Should I have the 2 storage drives installed as well? I'm assuming yes to both, so I'm going to get to work on that.

EDIT 2: Both drives connected, restarted to get into LiveCD, but forgot I needed it in the drive =-P

...GRUB loads anyway...  either installing GRUB while in the liveCD (only to have it error 15 me?) or disconnecting the drives for a boot has somehow brought the MBR(?) into line? Perhaps permanently?

According to fdisk, all of the drive naming conventions remain unchanged.

---

### Post by RapidDissent on 2010-08-19
Hot off the press (and finally on the desktop again! ^_^ b)

Thanks to those who have been helping, by the way! I really appreciate it, though it may not show though my agitation with my computer =-/

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   716,802,047   716,800,000   7 HPFS/NTFS
/dev/sdb2         716,804,296   976,768,064   259,963,769   5 Extended
/dev/sdb5         716,804,298   788,486,264    71,681,967  83 Linux
/dev/sdb6         788,486,328   800,775,989    12,289,662  82 Linux swap / Solaris
/dev/sdb7         800,776,053   976,768,064   175,992,012  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        24F6E274F6E24620                       ntfs       Depot Daddy                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        04C69048C6903C3C                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        c9e2fa72-86df-40f8-b773-7825a872840a   ext4       rewt                          
/dev/sdb6        b5872b4a-aae7-464c-85e3-5985c74bdec4   swap                                     
/dev/sdb7        2202c0fa-0d36-4774-94d7-a1fcaf5211a9   ext4       Holme                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        86D2FC6ED2FC63B9                       ntfs       Big Bertha                    
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb7        /home                    ext4       (rw)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set c9e2fa72-86df-40f8-b773-7825a872840a
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set c9e2fa72-86df-40f8-b773-7825a872840a
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
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set c9e2fa72-86df-40f8-b773-7825a872840a
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=c9e2fa72-86df-40f8-b773-7825a872840a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set c9e2fa72-86df-40f8-b773-7825a872840a
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=c9e2fa72-86df-40f8-b773-7825a872840a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set c9e2fa72-86df-40f8-b773-7825a872840a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set c9e2fa72-86df-40f8-b773-7825a872840a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 24f6e274f6e24620
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 86d2fc6ed2fc63b9
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=c9e2fa72-86df-40f8-b773-7825a872840a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=2202c0fa-0d36-4774-94d7-a1fcaf5211a9 /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=b5872b4a-aae7-464c-85e3-5985c74bdec4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 386.6GB: boot/grub/core.img
 369.4GB: boot/grub/grub.cfg
 386.5GB: boot/grub/stage2
 386.6GB: boot/initrd.img-2.6.32-24-generic
 386.6GB: boot/vmlinuz-2.6.32-24-generic
 386.6GB: initrd.img
 386.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd 

```

---

### Post by wilee-nilee on 2010-08-19
If you hit the f12 key or the key for choice of boot and try booting drom sdb. You could put it to be the first HD read in bios as well. This may work.

---

### Post by RapidDissent on 2010-08-19
Loaded sdc by mistake first go-around, GRUB loaded.

Double checked the drive (odd name in the BIOS), found the error. Booted on sda, and it immediately went to win7, which isn't even loading; just a blinking cursor. Very odd, because I tested that Win7 loaded properly just after disconnecting / reconnecting the drives.

EDIT- loaded normally into grub, selected Win7, and it loads fine as well. No idea what's going on with sda.

According to the bios under 'Hard Drives' in the boot priority section (AMIBIOS for ASUS P6T Rev. 1303), the "1st Drive" is the system drive, sdb, followed by sdc in "2nd Drive", and finally sda in the third.

Boot priority has sdb after cd.

These BIOS settings haven't changed throughout the ordeal, save for one adjustment made ~10 min ago in the 'Hard drives' after I found my mistaking sda for sdc, so "2nd Drive: and "3rd Drive" were reversed before.

EDIT 2 - Started into linux again from GRUB, file missing (meh). Also, reorganized the SATA cables on the mobo so that the system drive is on SATA1, the 1TB (sdc) is on SATA2, and the 1.5TB (sda) is on SATA3. GRUB still loads, linux loaded this time... odd.

---

### Post by oldfred on 2010-08-20
Grub first looks at the set root, which by itself would cause issues if you renumbered drives. But the next command is a search by UUID, so it still finds the correct drive.

On my system whichever drive I boot is hd0, then each drive remaining from sda, sdb, sdc is hd1 & hd2 in order. I found this by trying to chainload from one MBR to another.

---

