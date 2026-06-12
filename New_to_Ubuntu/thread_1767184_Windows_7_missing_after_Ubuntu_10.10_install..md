---
title: "Windows 7 missing after Ubuntu 10.10 install."
date: 2011-05-25
forum: New to Ubuntu
---

### Post by iarchetype on 2011-05-25
Hi,

I recently installed 10.10 on my computer and now there is no bootloader. Hence, I can't get to windows 7.

After some research i found there is some problem with Grub2, so i did this,

```
sudo apt-get install os-prober
sudo update-grub2
 
```

The first said that os-prober is already the newer version.
The second displayed something like this,

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

I restarted and nothing happend, i guess because update-grub newer found windows 7.

If it's any use, i have sda1 as ubuntu and sda7 as windows.

I can get windows 7 by fixing IT'S bootrec but that won't get me grub either. I don't know what to do now. :confused:

Waiting for help.

---

### Post by seawolf167 on 2011-05-25
You can manually add the Windows 7 loader to the GRUB menu provided you didn't overwrite it when installing GRUB (in which case you'll use the Windows recovery disk to reinstall the Windows loader, then reinstall grub).

Edit /etc/grub.d/40_custom

```
sudo gedit /etc/grub.d/40_custom
```

Add the following line

```
menuentry ‘Windows 7&#8242; {
set root=’(hd0,msdos7)’
chainloader +1
}
```

Save, exit, then run

```
sudo update-grub2
```

and check to see if the entry exists

---

### Post by iarchetype on 2011-05-25
No use. The entry still doesn't get listed. 

I think I just have to fix the Win7 loader and then go back to reinstall Grub like you said.

Thanks anyways

---

### Post by Quackers on 2011-05-25
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder).
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by iarchetype on 2011-05-25
Here is the results file, 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 4. But according to the info from fdisk, 
                       sdb5 starts at sector 83891434.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb7 starts 
                       at sector 258. But according to the info from fdisk, 
                       sdb7 starts at sector 314585088.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sdb8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb8 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdb9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb9 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdb10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb10 
                       starts at sector 2048.
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 4007 MB, 4007624704 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7827392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63     7,827,391     7,827,329   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
12 heads, 4 sectors/track, 20349441 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    43,055,103    43,053,056  83 Linux
/dev/sdb2          52,430,848    83,890,175    31,459,328   7 NTFS / exFAT / HPFS
/dev/sdb3          83,891,432   976,750,591   892,859,160   f W95 Extended (LBA)
/dev/sdb5          83,891,434   136,327,648    52,436,215   7 NTFS / exFAT / HPFS
/dev/sdb6         136,327,653   314,584,829   178,257,177   7 NTFS / exFAT / HPFS
/dev/sdb7         314,585,088   398,471,167    83,886,080   7 NTFS / exFAT / HPFS
/dev/sdb8         398,473,216   524,302,335   125,829,120   7 NTFS / exFAT / HPFS
/dev/sdb9         524,304,384   838,877,183   314,572,800   7 NTFS / exFAT / HPFS
/dev/sdb10        838,879,232   976,750,591   137,871,360   7 NTFS / exFAT / HPFS
/dev/sdb4          43,055,104    52,430,847     9,375,744  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        77FB-E4E6                              vfat       ÿU‹ì‹MVW‹}
/dev/sdb1        4c95f357-f644-4bd8-a6b6-ff4ca62647aa   ext4       
/dev/sdb10       481C1D3B1C1D258A                       ntfs       Audio
/dev/sdb2        2EC046EDC046BB3B                       ntfs       Videos
/dev/sdb4        baa0db92-9dcf-4b89-9552-087fda5a2d54   swap       
/dev/sdb5        8240C3B040C3A8ED                       ntfs       Books
/dev/sdb6        E8A0DF64A0DF37B0                       ntfs       Software
/dev/sdb7        DAE83A94E83A6F3F                       ntfs       Windows 7
/dev/sdb8        60A4BA71A4BA4974                       ntfs       Data
/dev/sdb9        78EC0E2AEC0DE36C                       ntfs       Games

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/77FB-E4E6         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set 4c95f357-f644-4bd8-a6b6-ff4ca62647aa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 4c95f357-f644-4bd8-a6b6-ff4ca62647aa
set locale_dir=($root)/boot/grub/locale
set lang=en
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
	search --no-floppy --fs-uuid --set 4c95f357-f644-4bd8-a6b6-ff4ca62647aa
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=4c95f357-f644-4bd8-a6b6-ff4ca62647aa ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 4c95f357-f644-4bd8-a6b6-ff4ca62647aa
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=4c95f357-f644-4bd8-a6b6-ff4ca62647aa ro single 
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
	search --no-floppy --fs-uuid --set 4c95f357-f644-4bd8-a6b6-ff4ca62647aa
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 4c95f357-f644-4bd8-a6b6-ff4ca62647aa
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

menuentry 'Windows 7' {
set root=' (hd0,msdos7)'
chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb4 during installation
UUID=baa0db92-9dcf-4b89-9552-087fda5a2d54 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.184558868 = 4.493135872    boot/grub/core.img                             1
  14.419296265 = 15.482601472   boot/grub/grub.cfg                             1
  14.415039062 = 15.478030336   boot/initrd.img-2.6.35-22-generic              2
   0.333099365 = 0.357662720    boot/vmlinuz-2.6.35-22-generic                 1
  14.415039062 = 15.478030336   initrd.img                                     2
   0.333099365 = 0.357662720    vmlinuz                                        1



```

---

### Post by oldfred on 2011-05-25
Actually your windows boot partition maybe sda1 as that is where the boot files are. Or is that only a repair console and you deleted the NTFS boot partition?  The boot partition is not normally a FAT partition, but the repairCD for windows use FAT.. Normally FAT partitions are not set up to have the boot sector to boot Vista or 7. Can you boot from sda with BIOS or one time boot key?

This may also be a problem. Window is very particular about its partition boot sector. It must match locations and have boot info in the partition. You may need to run windows repairs on it.

```
sdb7: ____________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    [COLOR=Red]Boot sector info:   According to the info in the boot sector, sdb7 starts 
                       at sector 258. But according to the info from fdisk, 
                       sdb7 starts at sector 314585088.[/COLOR]
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

```You still show wubi in your sda7 windows install, but it does not have the normal boot files of bootmgr and BCD.

Best case is to only have Vista or Win7 in primary partitions. Anything else leads to issues. If you cannot use the sda1 to boot then you have to create another NTFS primary partition to have the boot files to let you boot win7 in the logical partition.

While this primarily discusses Vista, win7 works exactly the same way. If you do not want to fully understand booting at least review the pictures.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Quackers on 2011-05-25
It seems that you installed Ubuntu to /dev/sdb1. How large is this partition?

I suspect that sdb1 was originally a Windows boot partition. This would have held the first 2 Windows boot files.
The fact that those boot files are now missing is the reason that update-grub is not finding your Windows 7 system.
If Windows 7 was in a primary partition you could move the boot flag and repair its boot sector. Unfortunately Windows is not in a primary partition. It is in sdb7, which is a logical partition and Windows cannot boot from a logical partition unless its boot files are stored in a primary partition.

By all means see what other members suggest, but my suggestion would be to format the sdb1 partition to NTFS (deleting Ubuntu) and then try to repair the Windows bootloader with a Windows 7 repair disc (or installation disc). I have to say that I am not 100% sure that it will work, with Win 7 in a logical partition, as I'm not sure the installation will be found.
Obviously you should back up any data in Ubuntu that you may need first.
It may also be an idea to backup any data in your Windows system too.

See oldfred's post above!

---

### Post by iarchetype on 2011-05-26
This is what happend, i tried to install ubuntu from wubi inside windows 7. I gave it the xp partition to install alongside. When I restarted i found out that my ubuntu image was corrupted. 

So after downloading the image again i decided to install using the normal way and wiped the xp partition(which might have the boot files as it was primary) to install ubuntu in its place.

Now the sda1(FAT32) might just be the repair console as oldfred said.

I can see now, how bad i screwed it all up. I would have to delete the ubuntu partition and do a fresh win7 install there....After my Exams are over.

Thanks to All of You :)

---

### Post by jtarin on 2011-05-26
Moral of the story: To many windows and no boots make for cold feet.

---

### Post by iarchetype on 2011-05-27
I erased ubuntu, replaced it with win7 on sdb1. then erased videos and installed ubuntu on sdb2 using wubi.
 
Only these were actually primary partitions on my disk so for now everything's working and i am happy. :popcorn:


Thanks again.  ;)

---

