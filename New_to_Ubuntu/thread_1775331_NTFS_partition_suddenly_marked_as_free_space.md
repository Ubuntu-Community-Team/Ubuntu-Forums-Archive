---
title: "NTFS partition suddenly marked as free space"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by redmorning on 2011-06-04
Hi folks,

I'm here with a windows (ntfs - no Linux related) question, one more time. I searched this issue but couldn't find a proper solution(if you know/find one and paste the link here, sorry for wasting your time). 

I hava a 10.04 Ubuntu box with a dual Windows 7. Actually i always have problems with my Ubuntu; it doesn't start because of disk checking so frequent(I'm suspecting from NTFS partitions). Before yesterday, i booted windows and then tried to boot in Ubuntu but it didn't start up! After many file checks, i decided to boot form a live usb and comment out ntfs (windows D) auto-mount line in /etc/fstab. Than it worked. (I can't post "fdisk -l" output now because i'm on windows now, but i can provide that). To see what's going on with that ntfs partition(which is full of documents, photos, music and films) i booted in windows and realized that (in my coumputer -> disk management) my D partition is marked as "free space" from now on. 

In gparted, this space is seems as "unallocated space". On windows, i tried "Easeus Partition Recovery (5.1)" tool. With this tool i can view all my files in this partition before it starts to scan this partition. So i know that all my files are still in there (just some of the folders name are unusual-like they are recovered-). I think that, this partition is just marked as "deleted". I didn't format or delete it, i didn't even touch that. Last thing that i did on this partition is to listen music from Ubuntu. 

With this Easeus tool, i can recover that partition but i don't have an external disk to use for this operation (not this option for a while). So i need to learn if i can manipulate this partitions flags. I already know testdisk and used it for a 350 GB disk recovery operation, it was very successful (as i said, i don't have an external hdd). 

If any information is needed, i can provide. 

Thanks in advance.

---

### Post by corncob on 2011-06-04
I got kind of lost in your post but if it has anything to do with things, you are only allowed to have 4 primary partitions on your drive.    Win 7 only needs 2 partitions, they tell me, a boot partition and the OS.  OEMs can add 2 more, recovery and storage, so your drive may have been filled up before you installed Ubuntu resulting in one of the partitions being pushed out (marked as unallocated space or other problems).  You should be able to see what partitions you have with gparted.

---

### Post by redmorning on 2011-06-04
Hi corncob,

Actually i was running my windows and linux happily for a long time (about10 months). I have a windows boot partition, windows OS partition, recovery partition and lastly an extended partition which contains my windows D partition and other linux partitions (such as /boot, /, swap). I can see my unallocated partition (windows D) on gparted under extended partition. So i don't have a primary partition limit issue(not after months i think [: ).

---

### Post by oldfred on 2011-06-04
Do not know an answer to your specific question, but it sounds like you are having hard drive issues. If you repeatedly have to run chkdsk in Windows and fsck in Linux I would be concerned that drive is failing and have a way to fully back up everything.

---

### Post by redmorning on 2011-06-04
Hi oldfred,

For a fully backup, i will need an extended hdd. Actually i didn't run chkdsk from windows yet and ubuntu won't be able to run fsck on this issued ntfs partition any more (after disabling auto-mount on /etc/fstab). Maybe i must give a shot before continuing. 
 The thing that bothers me is; when i run this easy use 'Easeus Partition Recovery' tool, i can see all my files right there on my partition. So it makes me think like i can revert this 'free space / unallocated' in some way. Am i right?

---

### Post by corncob on 2011-06-04
> **oldfred said:**
> Do not know an answer to your specific question, but it sounds like you are having hard drive issues. If you repeatedly have to run chkdsk in Windows and fsck in Linux I would be concerned that drive is failing and have a way to fully back up everything.

I was once told that to check if my hard drive was going bad to run
```
dmesg
```
and look for failures

---

### Post by redmorning on 2011-06-05
I'm now on my Ubuntu box. My dmesg output is in the attachment. I couldn't find any anomalies related my partition issue (or missed if there is any). I think it hasn't any information because those partitions are not mounted.

fdisk -l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdda4dda4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671       19324   141804606    7  HPFS/NTFS
/dev/sda4           19325       60802   333165506    5  Extended
/dev/sda5           41379       60467   153332392+  83  Linux
/dev/sda6           60468       60782     2518016   82  Linux swap / Solaris
/dev/sda7           60782       60802      158720   83  Linux

```

i can't view that unallocated partition (it was /dev/sda8 before) anymore. 

vim /etc/fstab
```
  7 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  8 proc            /proc           proc    nodev,noexec,nosuid 0       0
  9 /dev/sda5       /               ext2    defaults,user_xattr  0       1
 10 /dev/sda7       /boot           ext2    defaults     0       2
 11 #/dev/sda3       /windows-C      ntfs    defaults     0       0 
 12 #/dev/sda8       /windows-D      ntfs    defaults     0       0  
 13 # swap was on /dev/sda6 during installation
 14 UUID=9fbf8e24-a37e-4b14-ad25-fbe8ef1b2944 none            swap    sw              0       0

```

In this case, i cannot use fsck for my lost partition ('unallocated' / 'free space'). The last system modification that i remember was kernel update (2.6.32-30 -> 2.6.32-32). But after this update, i boot in Ubuntu successively one time. 
So i want to ask if i would any chance to mark this lost partition from ubuntu (which cannot be seen from fdsik) or do i have to do it in windows? 

Thanks.

---

### Post by redmorning on 2011-06-05
BTW, after this kernel update, in spite of non-mounted ntfs partitions, ubuntu cannot boot in its first attempt and after a hard reboot, it checks partitions. It doesn't find any error anyway. Just a little boring point.

---

### Post by westie457 on 2011-06-05
> After many file checks, i decided to boot form a live usb and comment out ntfs (windows D) auto-mount line in /etc/fstab.

Hello, from what I have read in your first post it looks like your partition got lost when you commented out the line in the quote.

Have you tried to reverse that operation?

Edit: Did a small amount of research and found this 

[http://ubuntuforums.org/showthread.php?t=1590694]("http://ubuntuforums.org/showthread.php?t=1590694")

Hope this works for you.

---

### Post by redmorning on 2011-06-05
Hi westie,

I commented out that line to secure Ubuntu booting. They're not lost. I know why they're not accessible from Ubuntu now. If i reverse it, i won't see anything (if you look at my fdisk output, you will see). Because in gparted, it seems 'unallocated space'. So for Ubuntu, there is not an existing partition to mount! I can see my files just from Windows (with that recovery toll mentioned in the first post).

Thanks.

---

### Post by corncob on 2011-06-05
I noticed only one "failure" in your dmesg output:
```
Suggest a bigger bdl_pos_adjo failures"
```.
"Basically it's a warning message that CPU usage got higher due to
somehow wrongly behaving hardware."

---

### Post by yetiman64 on 2011-06-05
> fdisk -l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdda4dda4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671       19324   141804606    7  HPFS/NTFS
/dev/sda4           19325       60802   333165506    5  Extended
/dev/sda5           41379       60467   153332392+  83  Linux
/dev/sda6           60468       60782     2518016   82  Linux swap / Solaris
/dev/sda7           60782       60802      158720   83  Linux 
```i can't view that unallocated partition (it was /dev/sda8 before) anymore. 
If fdisk can't see what was /dev/sda8 then the partition table entry for sda8 may be damaged, you may be able to recover it and rewrite the partition table using testdisk.

Testdisk is available in the repositories (there is also a Windows variant available), a link to a guide for it is [[COLOR=Blue]--here--[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

Read the guide fully and determine how to use it in your circumstances **before** attempting anything, testdisk is a powerful tool, use with care. Good luck.

---

### Post by redmorning on 2011-06-05
**@Corncob**
Thank you for pointing that warning. I think it is not a related point.

**@westie** 
I read that detailed thread, it has many useful tricks and informations. But as i see. it is much more grub/boot issue. I already have an experience one that one time:
[http://ubuntuforums.org/showthread.php?t=1606427&page=3]("http://ubuntuforums.org/showthread.php?t=1606427&page=3")

My situation is a bit different i think. I am posting the gparted view (as an attachment - 168.94GB unallocated partition under /dev/sda4) and boot_info_script.sh ([http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")) result: 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for /grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 1461376 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    26,626,047    26,624,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     26,626,048    26,830,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          26,830,848   310,440,059   283,609,212   7 NTFS / exFAT / HPFS
/dev/sda4         310,440,060   976,771,071   666,331,012   5 Extended
/dev/sda5         664,737,570   971,402,354   306,664,785  83 Linux
/dev/sda6         971,415,552   976,451,583     5,036,032  82 Linux swap / Solaris
/dev/sda7         976,453,632   976,771,071       317,440  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000 MB, 1000341504 bytes
16 heads, 32 sectors/track, 3816 cylinders, total 1953792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     1,953,791     1,953,760   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE
/dev/sda2        C4A24162A2415A56                       ntfs       SYSTEM RESERVED
/dev/sda3        BA6E48826E483981                       ntfs       ACER
/dev/sda5        9b78b480-8219-45c3-a524-10b805012d5e   ext2       
/dev/sda6        9fbf8e24-a37e-4b14-ad25-fbe8ef1b2944   swap       
/dev/sda7        5e4f1df6-cc68-4961-bbad-977b78b45254   ext2       
/dev/sdb1        7C59-F2C6                              vfat       LUDVIG

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set 9b78b480-8219-45c3-a524-10b805012d5e
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
search --no-floppy --fs-uuid --set 9b78b480-8219-45c3-a524-10b805012d5e
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 9b78b480-8219-45c3-a524-10b805012d5e
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=9b78b480-8219-45c3-a524-10b805012d5e ro acpi_osi=Linux  quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 9b78b480-8219-45c3-a524-10b805012d5e
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=9b78b480-8219-45c3-a524-10b805012d5e ro single acpi_osi=Linux
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set daa41c49a41c2b11
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c4a24162a2415a56
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext2    defaults,user_xattr	 0       1
/dev/sda7       /boot           ext2    defaults     0       2
#/dev/sda3       /windows-C      ntfs    defaults     0       0 
#/dev/sda8       /windows-D      ntfs    defaults     0       0  
# swap was on /dev/sda6 during installation
UUID=9fbf8e24-a37e-4b14-ad25-fbe8ef1b2944 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 340.893578529 = 366.031692800  boot/grub/core.img                             1
 454.393486977 = 487.901291520  boot/grub/grub.cfg                             1
 461.376595497 = 495.399347200  boot/initrd.img-2.6.32-29-generic              3
 457.546517372 = 491.286832128  boot/vmlinuz-2.6.32-29-generic                 2

============================= sda7/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set 9b78b480-8219-45c3-a524-10b805012d5e
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
search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
	linux	/vmlinuz-2.6.32-32-generic root=UUID=9b78b480-8219-45c3-a524-10b805012d5e ro acpi_osi=Linux  quiet splash
	initrd	/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
	echo	'Loading Linux 2.6.32-32-generic ...'
	linux	/vmlinuz-2.6.32-32-generic root=UUID=9b78b480-8219-45c3-a524-10b805012d5e ro single acpi_osi=Linux
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-32-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set daa41c49a41c2b11
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c4a24162a2415a56
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 465.749092102 = 500.094279680  grub/core.img                                  3
 465.743261337 = 500.088018944  grub/grub.cfg                                  1
 465.626255035 = 499.962384384  initrd.img-2.6.32-32-generic                  37
 465.616751671 = 499.952180224  vmlinuz-2.6.32-32-generic                     18

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label oem=OEM install (for manufacturers)
kernel /ubnkern
append initrd=/ubninit oem=oem-config/enable=true

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             vesamenu.c32                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 vesamenu.c32                       :  COM32R module (v3.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  cb 0f 11 00 53 3b 49 a4  25 90 ba 8c 7a 19 2f 0a  |....S;I.%...z./.|
00000010  16 37 15 34 8f c1 35 f9  06 bb 63 22 27 de 78 54  |.7.4..5...c"'.xT|
00000020  f4 9d d6 71 98 09 7e 29  86 3e 0e 30 58 92 35 30  |...q..~).>.0X.50|
00000030  16 c9 70 13 4a 85 7b 3c  cc b6 95 8a 8d ab 6b 6e  |..p.J.{<......kn|
00000040  6c cc a5 be f1 16 60 9f  ee 13 c4 cd 33 3d 22 41  |l.....`.....3="A|
00000050  73 78 8b 99 a8 d1 70 90  b0 ce 2d 86 d9 fe 2c 58  |sx....p...-...,X|
00000060  74 87 30 e2 25 f1 f0 dd  16 b9 86 fd 74 9c 49 b3  |t.0.%.......t.I.|
00000070  b1 38 a6 0c 97 8a 55 0a  f2 55 85 6e 2d 26 dc 7d  |.8....U..U.n-&.}|
00000080  e3 71 a6 c1 dc ce cc 4a  9d 40 2c 6e 8f 03 00 bc  |.q.....J.@,n....|
00000090  a7 d3 ed 6a e2 bd 50 5d  55 c9 b4 ca e9 3c 5e 51  |...j..P]U....<^Q|
000000a0  0a 92 74 df 05 ba 1f 64  a4 b6 8e d8 dc dd 2a 8a  |..t....d......*.|
000000b0  33 03 46 93 10 53 51 4c  cb 8e 4e 0b 8c aa aa aa  |3.F..SQL..N.....|
000000c0  aa aa aa aa aa aa aa aa  aa aa aa aa aa aa aa aa  |................|
000000d0  aa aa aa aa aa aa aa aa  aa aa aa aa aa aa 00 02  |................|
000000e0  66 04 02 25 38 f6 60 8c  d2 eb 04 07 02 37 0c 6f  |f..%8.`......7.o|
000000f0  1c c6 45 c0 c8 c6 e7 88  a9 83 ff fb e2 04 0e 0e  |..E.............|
00000100  e7 a9 68 d1 13 7a 7a 70  f6 8d 2a 22 6f 0c aa 1d  |..h..zzp..*"o...|
00000110  19 a3 4c 6d 65 e7 c3 bc  b4 69 09 bc 32 a2 34 bc  |..Lme....i..2.4.|
00000120  eb a4 38 82 03 99 00 47  8e 24 0e c8 95 26 81 98  |..8....G.$...&..|
00000130  72 f0 b0 43 ca 75 88 05  8f 88 06 1d 47 21 66 b4  |r..C.u......G!f.|
00000140  c5 95 05 61 47 53 02 08  12 19 2f 01 84 12 e5 a6  |...aGS..../.....|
00000150  8f 06 4b 76 b1 04 ab 90  c0 08 20 8e 93 42 68 15  |..Kv...... ..Bh.|
00000160  0f 95 ea bb a1 ac 22 ee  95 25 a8 d5 41 7f 0f 93  |......"..%..A...|
00000170  d4 06 00 9d 34 4b aa 48  f5 02 d1 80 73 82 fd 0e  |....4K.H....s...|
00000180  17 38 8f 12 4c 2b 2d 8c  33 b7 b8 d5 85 aa 23 59  |.8..L+-.3.....#Y|
00000190  2a d3 53 8c 31 bb f0 ea  9a 9f 4f 75 df b1 ae 62  |*.S.1.....Ou...b|
000001a0  b8 98 f8 6d 50 41 3a db  0d d5 37 1d cb 2d cd 11  |...mPA:...7..-..|
000001b0  b7 8f 88 b6 87 0a cc 77  6b 5b 50 ae 8e 45 00 fe  |.......wk[P..E..|
000001c0  ff ff 83 fe ff ff a6 26  1e 15 51 55 47 12 00 fe  |.......&..QUG...|
000001d0  ff ff 05 fe ff ff f7 7b  65 27 8d 0b 4d 00 00 00  |.......{e'..M...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

I am now on a live usb.

---

### Post by redmorning on 2011-06-05
> **yetiman64 said:**
> If fdisk can't see what was /dev/sda8 then the partition table entry for sda8 may be damaged, you may be able to recover it and rewrite the partition table using testdisk.

Testdisk is available in the repositories (there is also a Windows variant available), a link to a guide for it is [[COLOR=Blue]--here--[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

Read the guide fully and determine how to use it in your circumstances **before** attempting anything, testdisk is a powerful tool, use with care. Good luck.
Hi yetiman,

I saw your post just after i posted my last one. I think just like you, ther must be some problems on partition table for /dev/sda8. Maybe a flag is changed or its metadata is completely damaged. Like i already said two times, all the data is still standing there. I will examnine that testdisk link you posted. 

Thanks

---

### Post by yetiman64 on 2011-06-05
> **piratejackus said:**
> ....all the data is still standing there.

Yes that sounds right, I have had a partition table totally hosed, gparted saw my boot drive as totally unallocated, Windows couldn't see a thing, the only reason I could boot both systems was because I was using the GAG bootloader (which scans the drive for partitions, doesn't rely on the partition table apparently). 

All the information can be on the drive and the partitions but if the partition table is partly or fully damaged things start disappearing in gparted and the Windows disk management console.

I actually used testdisk to recover that particular mess :-)

---

### Post by oldfred on 2011-06-05
What does testdisk say about the partition Are you sure these are not files chkdsk did recover but isolated?

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by redmorning on 2011-06-05
> **yetiman64 said:**
> Yes that sounds right, I have had a partition table totally hosed, gparted saw my boot drive as totally unallocated, Windows couldn't see a thing, the only reason I could boot both systems was because I was using the GAG bootloader (which scans the drive for partitions, doesn't rely on the partition table apparently). 

All the information can be on the drive and the partitions but if the partition table is partly or fully damaged things start disappearing in gparted and the Windows disk management console.

I actually used testdisk to recover that particular mess :-)
Your bootloader seems very fine. I did not dive into those boot loader stuff as i am not so experienced (and also because of being have lost my all-some partitions or systems so many times). I don't know if you noticed but in my earlier posts i mentioned a data recovery tool which shows me all of my files before make a scan, just in one second! But it normally asks for an extended hdd (which i don't have) to make a recovery process. 
In this helpful forum atmosphere, i'm looking for a solution to retrieve this partition to life without a recovery process.
BTW, i'm still reading testdisk for a proper solution.

---

### Post by redmorning on 2011-06-05
> **oldfred said:**
> What does testdisk say about the partition Are you sure these are not files chkdsk did recover but isolated?

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Hi oldfred,

I run testdisk but i couldn't see my unallocated partition in the list (the view is in the attachment). Now it is still analyzing partitions.
*I will continue to feed this thread/or edit this post.*


***_EDIT:_***
Testdisk quick analyses is finished, result view is attached.
as you see in the image the partitions are;
-> Windows recovery partition - 13 GB
-> Windows boot partition - 104 MB
-> Windows OS partition - 145 GB
-> Ubuntu / partition - 157 GB
-> Swap partition - 2578 MB
-> Ubuntu /boot partition - 162 MB

My lost/unallocated partition is not in the list. I can not undelete my partition as **oldfred** pointed with the link [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS]("http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS") for the same reason.


***_EDIT 2:_***
After this issue raised up (maybe triggered because of last kernel update 2.6.32-30 -> 2.6.32-32) i can boot in ubuntu after two or more hard shutdowns (after i choose ubuntu from grub list, ubuntu can not be load and a black screen stays) and a fsck. So it takes about 15-20 min for every boot. This is really boring, very very boring.

---

### Post by srs5694 on 2011-06-05
I have two suggestions.

First, do a "deep" analysis with TestDisk. That might not be the right term, but basically, it offers a couple different levels of analysis, which take different amounts of time. Run the more lengthy one.

Second, if the Windows tool you've used to find the partition can be coaxed into revealing its start and end points (or even just its start point) in sectors, you can re-create the partition using fdisk.

---

### Post by redmorning on 2011-06-05
> **srs5694 said:**
> I have two suggestions.

First, do a "deep" analysis with TestDisk. That might not be the right term, but basically, it offers a couple different levels of analysis, which take different amounts of time. Run the more lengthy one.

Second, if the Windows tool you've used to find the partition can be coaxed into revealing its start and end points (or even just its start point) in sectors, you can re-create the partition using fdisk.
i did the deep analysis (which takes a long time like you said) too but my 'unallocated partition' didn't show in the list.

I didn't understand exactly your second suggestion, that recovery program is just showing me the files inside the partition. It doesn't give any information about the start and end points. 

Actually, to re-create the partition, i can assume the start and end points from other partitions (regarding to testdisk analysis) but in that way, a new partition will be created but i can't be sure if those files will show up in the partition or not!

---

### Post by oldfred on 2011-06-05
I do not know why testdisk would not find sda8 between 310440060 the beginning of your extended partition and 644737570 the beginning of you next partition in the extended??

parted has a rescue mode where you input a start & end it it tries to find a partition (I think that is how testdisk does it also).

First backup current partition table.
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

sudo parted /dev/sda unit s print

sudo parted
unit s
rescue
input start & end and see if it finds partition

---

### Post by redmorning on 2011-06-05
> **oldfred said:**
> I do not know why testdisk would not find sda8 between 310440060 the beginning of your extended partition and 644737570 the beginning of you next partition in the extended??

parted has a rescue mode where you input a start & end it it tries to find a partition (I think that is how testdisk does it also).

First backup current partition table.
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

sudo parted /dev/sda unit s print

sudo parted
unit s
rescue
input start & end and see if it finds partition

i tried parted, it searched but it didn't any result in this block:
```

GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) rescue                                                           
Start? 310440060
End? 644737570                                                            
(parted)  

```


---***EDIT***---
my mistake, i had to precise the end point smaller than 644737570, so:

```

(parted) unit s                                                           
(parted) rescue                                                           
Start? 310440060                                                          
End? 664737569
Information: A ntfs logical partition was found at 310440186s -> 664737561s.  Do you want to add it to the
partition table?
Yes/No/Cancel? Yes                                                        
(parted) quit                                                             
Information: You may need to update /etc/fstab.  

```

Happily:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdda4dda4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671       19324   141804606    7  HPFS/NTFS
/dev/sda4           19325       60802   333165506    5  Extended
/dev/sda5           41379       60467   153332392+  83  Linux
/dev/sda6           60468       60782     2518016   82  Linux swap / Solaris
/dev/sda7           60782       60802      158720   83  Linux
/dev/sda8           19325       41378   177148688    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 2003 MB, 2003795968 bytes
32 heads, 63 sectors/track, 1941 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00b93e60

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1941     1956496+   6  FAT16

```

**oldfred**, thank you very much for sharing your knowledge and experience one more time. After mounting sda8, voila! all my files are there again!
it is a simple (but a little hard to find) solution as it has to be within linux. I really like this forum!
(:

cheers!

---

### Post by oldfred on 2011-06-05
Glad it worked. :)

But if data is important it should be fully backed up on a regular basis.

---

### Post by redmorning on 2011-06-05
> **oldfred said:**
> Glad it worked. :)

But if data is important it should be fully backed up on a regular basis.
You're absolutely right, i must buy an external disk.


BTW, i'd like to ask you something (you can propose me to create a new thread of course);
everytime i boot in ubuntu after windows, ubuntu runs fsck and after that, it restarts automatically and hangs on with black screen (after grub menu selection) No action on hdd (regarding to its led). And sometimes after a hard shutdown in this situation, it runs fsck again (i'm suspecting for hard shutdown triggers fsck). 
In regular boots (not after windows), this happens too. I have this issue for a looong time and i always afraid to corrupt this fsck process. So it takes a long time to start ubuntu session. 
To discover the reasons, whish logs do i have to examine ? 
In case of cancelling startup fsck process, is there a big danger?  

I'm asking all of these questions because i think they are related to these windows ntfs partitions. 

Thanks in advance for all.

*You don't have to answer and if you don't then i will create a new thread on this issue*

---

### Post by oldfred on 2011-06-05
I have seen one or two threads on fsck running on every boot, but did not follow threads to see issue or solution. 

I would think any sort of hard shutdown would trigger fsck or chkdsk in NTFS as that can damage file system. Are you not able to shutdown normally?

Are you hibernating in one system or the other and then writing into the hibernation? That causes corruption since the hibernation does not know about changes and is looking for everything where it was.

---

### Post by redmorning on 2011-06-06
When i have just a black screen without any action on hdd,i have no choice other than a hard shutdown. 
I'm not hibernating any of my systems. I had bad experiences with ubuntu on hibernate issue. 
I will search more to find a way/reason/solution. 

Thanks for all.

ciao!

---

### Post by oldfred on 2011-06-06
You should at least try this first on any forced shutdown.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by redmorning on 2011-06-06
> **oldfred said:**
> You should at least try this first on any forced shutdown.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
I didn't know it and every time i force shutdown, i feel like i'm hurting the system (:

This method is awesome! And those shortcuts to remember (:
Thank you again for sharing another precious piece of knowledge!

---

### Post by fyo on 2012-04-26
Booted up my notebook today and... one of my partitions (one of two ext4 partitions with Ubuntu) was gone. Marked as unallocated. Gave me quite a scare.

> **oldfred said:**
> parted has a rescue mode where you input a start & end it it tries to find a partition (I think that is how testdisk does it also).

First backup current partition table.
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)

sudo parted /dev/sda unit s print

sudo parted
unit s
rescue
input start & end and see if it finds partition

THANK YOU!

Everything is now back to normal...

Although I have no idea what caused the screw up in the first place.

---

