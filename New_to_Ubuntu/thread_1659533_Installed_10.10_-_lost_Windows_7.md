---
title: "Installed 10.10 - lost Windows 7"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Hyehouse on 2011-01-04
Hi.  Have just installed 10.10 from a Linux Format live disk on my Samsung Netbook.  Installation appears OK, and 10.10 is working perfectly.

I can no longer boot into Windows 7 as Grub does not show Windows.

As a beginner, I would very much appreciate help.

---

### Post by Megaptera on 2011-01-04
When I couldn't see Vista in my dual boot I did this

"If, after installing grub, Windows does not appear in the boot menu, boot into Ubuntu and execute command

sudo update-grub2

Which you do in the Terminal.

Hope this helps as a first thing to try.

---

### Post by Sidewinder1 on 2011-01-04
Open a terminal and type in exactly:
```
sudo update-grub
```
I believe that is the correct syntax; if not, I'm certain someone more knowledgeable will chime in.

HTH,
Side

---

### Post by Hyehouse on 2011-01-05
> **Megaptera said:**
> When I couldn't see Vista in my dual boot I did this

"If, after installing grub, Windows does not appear in the boot menu, boot into Ubuntu and execute command

sudo update-grub2

Which you do in the Terminal.

Hope this helps as a first thing to try.
Thanks for reply.  Sadly no luck - Grub does not mention windows.

---

### Post by Hyehouse on 2011-01-05
> **Sidewinder1 said:**
> Open a terminal and type in exactly:
```
sudo update-grub
```
I believe that is the correct syntax; if not, I'm certain someone more knowledgeable will chime in.

HTH,
Side
Thanks for reply.  Sadly no luck - Grub does not mention windows.

---

### Post by nothingspecial on 2011-01-05
Are you sure you didn`t install ubuntu over the entire disk?

type ```
sudo fdisk -l
```

Then post what it says.

---

### Post by milkrut on 2011-01-05
hi guys, I have the same problem ><

I entered "sudo fdisk -l" into terminal and this is what I got.

Doesn't seem to have a windows 7 boot but the windows 7 drive (sda5) is not formatted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          28      224878+  de  Dell Utility
/dev/sda2              29        1987    15728640    7  HPFS/NTFS
/dev/sda3   *        1987        2595     4882432   83  Linux
/dev/sda4            2595       38914   291732481    f  W95 Ext'd (LBA)
/dev/sda5           28052       38914    87249920    7  HPFS/NTFS
/dev/sda6            2595        2959     2928640   82  Linux swap / Solaris
/dev/sda7            2959       24843   175779840   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00110003

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182402  1465137560    7  HPFS/NTFS


What can I do to boot windows 7? Thanks a lot!

---

### Post by kansasnoob on 2011-01-05
We really need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternate instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by milkrut on 2011-01-05
hiya!

Attached is the report. Thanks again!

---

### Post by kansasnoob on 2011-01-05
I'm posting that full output in code tags for others to see:

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       449,819       449,757  de Dell Utility
/dev/sda2             450,560    31,907,839    31,457,280   7 HPFS/NTFS
/dev/sda3    *     31,907,840    41,672,703     9,764,864  83 Linux
/dev/sda4          41,674,750   625,139,711   583,464,962   f W95 Ext d (LBA)
/dev/sda5         450,639,872   625,139,711   174,499,840   7 HPFS/NTFS
/dev/sda6          41,674,752    47,532,031     5,857,280  82 Linux swap / Solaris
/dev/sda7          47,534,080   399,093,759   351,559,680  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 2,930,277,167 2,930,275,120   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D9-0417                              vfat       DellUtility                   
/dev/sda2        42A6EBD0A6EBC311                       ntfs       RECOVERY                      
/dev/sda3        a71b0353-378a-43ba-b2fd-4af538613636   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        FAD0D3B6D0D3777B                       ntfs                                     
/dev/sda6        3b775c8b-5689-420e-a705-a6e1582995c0   swap                                     
/dev/sda7        5f0d3ccd-c5c2-4e87-b499-3a44d5710e90   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8894CDFB94CDEBAE                       ntfs       Elements                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)
/dev/sdb1        /media/Elements          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set a71b0353-378a-43ba-b2fd-4af538613636
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set a71b0353-378a-43ba-b2fd-4af538613636
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set a71b0353-378a-43ba-b2fd-4af538613636
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=a71b0353-378a-43ba-b2fd-4af538613636 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set a71b0353-378a-43ba-b2fd-4af538613636
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=a71b0353-378a-43ba-b2fd-4af538613636 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set a71b0353-378a-43ba-b2fd-4af538613636
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a71b0353-378a-43ba-b2fd-4af538613636 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set a71b0353-378a-43ba-b2fd-4af538613636
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a71b0353-378a-43ba-b2fd-4af538613636 ro single 
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set a71b0353-378a-43ba-b2fd-4af538613636
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set a71b0353-378a-43ba-b2fd-4af538613636
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
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=5f0d3ccd-c5c2-4e87-b499-3a44d5710e90 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=3b775c8b-5689-420e-a705-a6e1582995c0 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  19.6GB: boot/grub/grub.cfg
  17.9GB: boot/initrd.img-2.6.35-22-generic
  17.9GB: boot/initrd.img-2.6.35-24-generic
  17.6GB: boot/vmlinuz-2.6.35-22-generic
  17.8GB: boot/vmlinuz-2.6.35-24-generic
  17.9GB: initrd.img
  17.9GB: initrd.img.old
  17.8GB: vmlinuz
  17.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  15 00 0c 00 06 00 2f 00  15 00 0a 00 1d 00 25 00  |....../.......%.|
00000010  13 00 4c 06 01 00 c5 08  03 00 28 00 01 00 0b 00  |..L.......(.....|
00000020  52 06 01 00 a5 08 02 00  01 00 0f 00 5c 06 05 00  |R...........\...|
00000030  8f 08 e2 08 fb 08 a0 08  f5 08 02 00 01 00 0a 00  |................|
00000040  62 06 01 00 05 08 02 00  1e 00 0a 00 68 06 01 00  |b...........h...|
00000050  31 08 02 00 15 00 0a 00  7c 06 01 00 33 08 00 00  |1.......|...3...|
00000060  04 00 77 06 00 00 05 00  77 06 00 00 19 00 77 06  |..w.....w.....w.|
00000070  02 00 15 00 0a 00 04 00  02 00 0e 00 27 00 0b 00  |............'...|
00000080  85 06 04 00 24 08 28 08  30 08 37 08 02 00 15 00  |....$.(.0.7.....|
00000090  0a 00 91 06 07 00 a4 08  a8 08 b0 08 b7 08 b1 08  |................|
000000a0  b3 08 ee 08 02 00 01 00  0a 00 97 06 01 00 0f 08  |................|
000000b0  02 00 02 00 0a 00 9d 06  01 00 03 08 02 00 15 00  |................|
000000c0  0a 00 a4 06 01 00 01 ff  03 00 02 00 26 00 0a 00  |............&...|
000000d0  aa 06 01 00 cd 08 02 00  01 00 13 00 00 00 00 00  |................|
000000e0  00 00 02 00 c1 06 01 00  45 08 00 00 16 00 bb 06  |........E.......|
000000f0  06 00 1c 00 15 00 30 00  1d 00 25 00 13 00 05 00  |......0...%.....|
00000100  15 00 0a 00 1d 00 25 00  13 00 c7 06 01 00 c5 08  |......%.........|
00000110  02 00 02 00 0b 00 cd 06  01 00 05 08 02 00 1e 00  |................|
00000120  0b 00 d7 06 05 00 62 08  7b 08 20 08 6a 08 72 08  |......b.{. .j.r.|
00000130  02 00 15 00 0b 00 de 06  02 00 e2 08 f5 08 02 00  |................|
00000140  01 00 0b 00 e7 06 01 00  00 ff 05 00 02 00 31 00  |..............1.|
00000150  1d 00 25 00 13 00 ee 06  01 00 01 ff 03 00 02 00  |..%.............|
00000160  26 00 0b 00 00 00 00 00  00 00 02 00 f8 06 01 00  |&...............|
00000170  05 08 02 00 1e 00 0c 00  02 07 05 00 62 08 7b 08  |............b.{.|
00000180  20 08 6a 08 72 08 02 00  15 00 0c 00 0a 07 03 00  | .j.r...........|
00000190  fb 08 e2 08 f5 08 02 00  01 00 0c 00 1b 07 01 00  |................|
000001a0  c5 08 00 00 1f 00 16 07  05 00 02 00 0a 00 1d 00  |................|
000001b0  25 00 13 00 04 00 02 00  25 00 14 00 13 00 00 fe  |%.......%.......|
000001c0  ff ff 07 fe ff ff 02 50  60 18 00 a8 66 0a 00 fe  |.......P`...f...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 60 59 00 00 00  |...........`Y...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I'm a bit worried and baffled :confused:

It's odd to see a Windows OS on a logical partition but it appears that's what you have:

> sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  [B][COLOR="Red"]According to the info in the boot sector, sda5 starts 
                       at sector 2048.[/COLOR][/B]
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe


And the highlighted message is also worrisome.

Did you move the beginning (left side) of the Windows partition?

I'm honestly unsure how to deal with that. I always prefer resizing Windows7 or Vista only with their own partitioning tool and then using Gparted to set up my Ubuntu partitions prior to installing.

Hopefully someone else will have a solution.

---

### Post by kansasnoob on 2011-01-05
One thing you could try is using Gparted to set a boot flag on sda5, then running:

```
sudo update-grub
```

I have doubts that'll work but it can't hurt to try.

You wouldn't need a boot flag on the Ubuntu partition.

Note: Gparted can be installed using USC or Synaptic. It'll then show up in System > Administration.

---

### Post by Shannonb1 on 2011-01-05
I had the same problem, I had to remove all usb harddrives and make the boot order look at linux drive first, which wasnt my c, then i used the grub command and it was back
 
i also used the win 7 recovery disc to rebuild i think it was the bootmgr, not sure if that was part of the solution.

---

### Post by Dracona on 2011-01-05
I'm sure i will get ripped for this comment, it is meant as a joke so don't be too upset with me.

Sounds like your off to a good start, best thing ever happened to me was installing Ubuntu, and deleting windows. well actually a little better feeling was when i took my windows OEM dis out for target practice with my 9mm.

listen to the guys on here, they can get you going again, provided you didn't install ubuntu over windows.

---

### Post by milkrut on 2011-01-05
What I tried to do was to use the Windows CD to fix bootmgr
the problem is that windows could not identify any Windows OS to fix ><

Any ideas?

---

### Post by Sef on 2011-01-05
> Boot sector info: According to the info in the boot sector, sda5 starts 
at sector 2048.

Windows should be on the first primary partition.


> Device Boot Start End Blocks Id System
/dev/sda1 1 28 224878+ de Dell Utility
/dev/sda2 29 1987 15728640 7 HPFS/NTFS
/dev/sda3 * 1987 2595 4882432 83 Linux
/dev/sda4 2595 38914 291732481 f W95 Ext'd (LBA)
/dev/sda5 28052 38914 87249920 7 HPFS/NTFS
/dev/sda6 2595 2959 2928640 82 Linux swap / Solaris
/dev/sda7 2959 24843 175779840 83 Linux

For some reason Windows seems to be on two paritions: sda2 - a primary partition and sda5 - a logical partition. The question is if sda2 is a true Windows installation, and if so, how can GRUB be set to boot into it instead of sda5.

---

### Post by Hyehouse on 2011-01-06
> **nothingspecial said:**
> Are you sure you didn`t install ubuntu over the entire disk?

type ```
sudo fdisk -l
```

Then post what it says.
Thanks for reply output follows:-

alan@SamsungNC10:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce41a31c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2611    20971520   27  Unknown
/dev/sda2   *        2611        2624      102400    7  HPFS/NTFS
/dev/sda3            2706       20517   143064427+   7  HPFS/NTFS
/dev/sda4           20517       30402    79396865    f  W95 Ext'd (LBA)
/dev/sda5           26477       30402    31528874+   7  HPFS/NTFS
/dev/sda6           20517       26227    45862912   83  Linux
/dev/sda7           26227       26476     2003968   82  Linux swap / Solaris

Partition table entries are not in disk order
alan@SamsungNC10:~$

---

### Post by Megaptera on 2011-01-06
This thread was started by Hyehouse, could milkrut who appears to have wandered in with his/her own issue please ask Forum Staff to move his/her problem to a new thread elsewhere as it's getting confusing in here???

Thanks.

---

### Post by milkrut on 2011-01-07
sorry about that, I was just thinking it was the same problem hence I posted here as well ><

---

### Post by Megaptera on 2011-01-07
> **milkrut said:**
> sorry about that, I was just thinking it was the same problem hence I posted here as well ><

Thanks for understanding :D

---

### Post by JDM_SOHC on 2011-02-17
Was this problem ever figured out..?? I'm going to buy a Samsung Netbook this week and I don't wanna run into this same issue..

---

### Post by hansolo4949 on 2011-02-17
Uh oh....it's the dreaded "cannot boot into windows" issue. I would, if you can, immedately go into the windows 7 partition (via places) and get all of your critical files off of there pronto, before something bad happens, and you lose the data. Just my 2 cents.

---

### Post by pekon on 2011-02-17
Incase you hv messed up ur partition table / MBR . use "testdisk" utility to fix it
Following link would be useful
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

