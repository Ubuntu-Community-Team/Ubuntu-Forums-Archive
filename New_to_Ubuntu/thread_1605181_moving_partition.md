---
title: "moving partition"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by joe2005 on 2010-10-25
I have a dual boot system with windows on sda1 and ubuntu on sda2  with grub on sda2.recently for test purpose installed maverick on sda7 with root on its own partition.Now I am in need of space and want to use the space sda7 for other purpose.Meanwhile maverick is fully installed with all up dates and other pakages.I want to retain the same and remove earlier installed os.How to do it ? I have attached gparted screenshot.thanks

---

### Post by Gone fishing on 2010-10-25
I was going to recommend the cloning tools on parted magic but gparted allows you to copy and paste partitions. Obviously if you move sda7 to sda2 you will need to fix grub.

But why? You could delete sda2 keep maverick where it is and use the free space there.

---

### Post by joe2005 on 2010-10-25
Agreed.If I delete sda2 how do I get back grub as think grub will be lost when sda2 deleted.PLease guide.Thanks for a very quick response.

---

### Post by Rubi1200 on 2010-10-25
The easiest way to reinstall GRUB can be found here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Use the first method and don't forget to run```
 sudo update-grub 
```after booting back into Ubuntu.

---

### Post by joe2005 on 2010-10-25
Thanks will try this tonight and report back.thanks once again

---

### Post by Gone fishing on 2010-10-25
If you keep Maverick where it is, the GRUB boot loader will be on the MBR you delete sda2 it will boot just fine on sda7. You can then just update grub to remove the redundent entries.

---

### Post by joe2005 on 2010-10-26
Thanks kept maverick on the existing partition deleted sda2 created ntldr missing error.Managed to restore windows loader.used live cd restored grub too thanks
The grub menu contains an entry  xp loader on sda 5 in addition to windows loader on sda1.want to remove the entry etc/default/grub returns permission denied.help please

---

### Post by Gone fishing on 2010-10-26
I think you just need to run sudo update-grub and it will automatically sort out your grub entries removing any non existent entries.

---

### Post by joe2005 on 2010-10-27
Tried as suggested.the entry is refusing to move.I think I made some error while restoring windows.attached the details if it is any help. thanks

---

### Post by Stephen Morgan on 2010-10-28
Grub must think XP is still bootable, if you want rid of it you could wipe the partition or if you just want the entry of the grub menu comment out the relevant lines in /etc/default/grub.cfg

```
sudo gedit /etc/defaults/grub.cfg
```

---

### Post by Quackers on 2010-10-28
It's not the best idea to edit grub.cfg directly as it will be overwritten.
Please go to the site below and download the boot script to your desktop, then run the script in a terminal by using the command given on that site. This will produce a Results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. (For CODE tags click on New Reply then on the # symbol in the toolbar).

This script will tell us where everything is on your system.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by joe2005 on 2010-10-28
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 2 in the file /NST/nst_linux.mbr looks at sector 
                       253494400 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /bootmgr /Boot/BCD /NTLDR /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 253494400 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda4         156,007,339   312,580,095   156,572,757   f W95 Ext d (LBA)
/dev/sda5         163,830,933   240,541,244    76,710,312   7 HPFS/NTFS
/dev/sda6    *    240,541,696   312,580,095    72,038,400  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    81,899,369    81,897,322   7 HPFS/NTFS
/dev/sdb2    *    163,814,805   573,408,044   409,593,240   7 HPFS/NTFS
/dev/sdb3         573,408,045   976,768,064   403,360,020   7 HPFS/NTFS
/dev/sdb4          81,899,370   163,814,804    81,915,435   f W95 Ext d (LBA)
/dev/sdb5          81,899,433   163,814,804    81,915,372   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A65C862A5C85F579                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        01CB4F62D2E42EF0                       ntfs       E VOLUME                      
/dev/sda6        37b7eb86-116f-43fe-8429-1e208b4721df   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        36BC7179BC713489                       ntfs                                     
/dev/sdb2        A23C44C13C449269                       ntfs       M VOLUME                      
/dev/sdb3        5C6457546457304E                       ntfs       N VOLUME                      
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        01CB242A7D97FC50                       ntfs       L VOLUME                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media/E VOLUME          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /media/N VOLUME          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/L VOLUME          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/WINLITE           iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb2        /media/M VOLUME          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/BOOT.INI: ================================

[Boot Loader]

timeout=30

Default=multi(0)disk(0)rdisk(0)partition(1)\Windows

[Operating Systems]

multi(0)disk(0)rdisk(0)partition(1)\Windows="Windows XP" /fastdetect
================================ sda5/BOOT.INI: ================================

[Boot Loader]

timeout=30

Default=multi(0)disk(0)rdisk(0)partition(1)\Windows



[Operating Systems]

multi(0)disk(0)rdisk(0)partition(1)\Windows="1ST TRY THIS seleccione esto primero" /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\Windows="2ND TRY THIS essayez ceci en deuzieme" /fastdetect

multi(0)disk(0)rdisk(0)partition(2)\Windows="3RD TRY THIS wahlen Sie diesen Third" /fastdetect

multi(0)disk(0)rdisk(1)partition(2)\Windows="4TH TRY THIS selezioni questo fourth" /fastdetect

multi(0)disk(0)rdisk(0)partition(3)\Windows="5TH TRY THIS selecione este fifth" /fastdetect

multi(0)disk(0)rdisk(1)partition(3)\Windows="6TH TRY THIS seleccione este sexto" /fastdetect

multi(0)disk(0)rdisk(0)partition(4)\Windows="7TH TRY THIS essayez ceci en septieme" /fastdetect

multi(0)disk(0)rdisk(1)partition(4)\Windows="8TH TRY THIS wahlen Sie dieses achte" /fastdetect

C:\="9TH TRY THIS selezioni questo nono"

D:\="10TH TRY THIS selecione este decimo"
=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 37b7eb86-116f-43fe-8429-1e208b4721df
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 37b7eb86-116f-43fe-8429-1e208b4721df
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 37b7eb86-116f-43fe-8429-1e208b4721df
insmod png
if background_image /usr/share/images/grub/image.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 37b7eb86-116f-43fe-8429-1e208b4721df
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=37b7eb86-116f-43fe-8429-1e208b4721df ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 37b7eb86-116f-43fe-8429-1e208b4721df
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=37b7eb86-116f-43fe-8429-1e208b4721df ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 37b7eb86-116f-43fe-8429-1e208b4721df
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 37b7eb86-116f-43fe-8429-1e208b4721df
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a65c862a5c85f579
	chainloader +1
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sda5)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 01cb4f62d2e42ef0
	drivemap -s (hd0) ${root}
	chainloader +1
}
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=37b7eb86-116f-43fe-8429-1e208b4721df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fa1f2500-9078-400d-b9fd-528c1b37de0c none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 129.7GB: boot/grub/core.img
 139.1GB: boot/grub/grub.cfg
 133.2GB: boot/initrd.img-2.6.35-22-generic-pae
 131.6GB: boot/vmlinuz-2.6.35-22-generic-pae
 149.0GB: grub/core.img
 133.2GB: initrd.img
 131.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  d1 26 e2 0e c6 76 68 b4  85 f7 8d 9e 41 85 87 51  |.&...vh.....A..Q|
00000010  e8 53 94 3d c6 84 76 2c  ae 25 d8 b8 cc f0 9e 79  |.S.=..v,.%.....y|
00000020  02 36 1a 03 2c 91 12 93  ef 6f 04 52 01 62 6a 63  |.6..,....o.R.bjc|
00000030  1a 3a 73 99 17 0b 88 bb  f9 29 c2 24 3c c9 c1 1f  |.:s......).$<...|
00000040  89 41 99 a5 4e 4e b4 19  b6 0c 5b 46 00 c3 71 83  |.A..NN....[F..q.|
00000050  97 f1 a8 45 99 be d6 b7  0f 0c 5a de 83 34 c3 3b  |...E......Z..4.;|
00000060  90 02 0f 12 72 59 10 30  56 2d 02 9e c1 ef 8d 03  |....rY.0V-......|
00000070  88 81 00 1b e5 e0 c0 78  bf d4 ba ca 25 82 81 52  |.......x....%..R|
00000080  a5 5f 82 22 b1 f8 1d fe  a3 3d fc b6 2a 4f da 88  |._.".....=..*O..|
00000090  f8 3c 04 07 be 12 80 f8  30 fc 03 42 1f d8 03 d3  |.<......0..B....|
000000a0  c9 a2 8e 41 a7 af 5e af  d7 25 78 14 e6 36 16 8f  |...A..^..%x..6..|
000000b0  0b 87 58 3b bf ab 90 62  99 78 a7 bc e1 51 95 cf  |..X;...b.x...Q..|
000000c0  d3 51 a6 86 3c 64 5a 05  37 9f 89 7c ee fb 2c 68  |.Q..<dZ.7..|..,h|
000000d0  3f 20 fa 96 3c 9b 86 ff  e6 94 fe e7 73 a4 55 a0  |? ..<.......s.U.|
000000e0  52 cb 56 17 c7 53 e9 9b  62 df 96 27 26 03 bb 9b  |R.V..S..b..'&...|
000000f0  98 97 a3 0f e5 99 b7 54  b7 58 e1 f0 3b 7c d5 b1  |.......T.X..;|..|
00000100  32 a5 53 56 e6 98 23 9b  6f 4d 4d 1d c5 75 78 79  |2.SV..#.oMM..uxy|
00000110  57 94 e5 c1 db 34 f5 53  f1 ed 6e 7d 7f c8 50 7e  |W....4.S..n}..P~|
00000120  81 9d b8 cd 51 34 fa 67  2f a3 d1 e4 1e f1 54 11  |....Q4.g/.....T.|
00000130  93 25 76 f7 97 b0 97 37  54 5a 3e 89 ff fb 80 4c  |.%v....7TZ>....L|
00000140  dd 1e 7c ba 8e a8 fb eb  e0 dd c4 77 db a8 6d b6  |..|........w..m.|
00000150  f2 0a 95 8e b7 b7 90 63  ab 60 8d dd 3f f5 35 a9  |.......c.`..?.5.|
00000160  25 4f 1c 9b fd 9d cc b2  cb 17 ea d0 d0 ff fb d0  |%O..............|
00000170  33 79 0f fd 4e f7 5c 25  f8 0c d1 da 82 d3 e0 87  |3y..N.\%........|
00000180  e8 8b 6f 3b 7b 59 bc c0  9d b9 fe eb 3d 77 8b c7  |..o;{Y......=w..|
00000190  e3 e8 0a 22 f5 6a 3e 25  f7 d9 db c2 4f dd b6 dc  |...".j>%....O...|
000001a0  50 0a 1e 74 0c 08 aa 20  b0 f8 29 af aa 95 5c f7  |P..t... ..)...\.|
000001b0  ae 58 a7 bc 17 97 17 78  77 f5 56 de 28 1e 00 fe  |.X.....xw.V.(...|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 ec ed e1 04 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by joe2005 on 2010-10-30
As desired posted the results of the boot script.request guidance to remove the entry.thanks

---

### Post by drs305 on 2010-10-30
I'll provide some guidance on at least the Ubuntu side.

At some point, Grub2 was installed to the sda6 partition. We can clean that up and get Grub2 installed on the MBR and looking to sda6.

To clear up the sda6 partition boot record (PBR), we can install testdisk and have it clear the PBR. To do this:

[If you are on the LiveCD, open Software Sources or Synaptic and enable the Universe repository via Settings, Repositories, then "Reload" and:]

```
sudo apt-get install testdisk
sudo testdisk /dev/sda6

```
Check in the first testdisk screen that you are in /dev/sda6.
Proceed.
Continue.
Select 'Intel'
Select 'MBR Code', then Y, Y
Quit, Quit

That will clean up the PBR. 

Now to make sure grub looks in the correct place:
If you are booted into your normal install on sda6 without using the LiveCD, run the following. Use *sda* and NOT *sda**6***
```
sudo grub-install /dev/sda
```
That should allow grub to boot normally to your sda6 install.

If you are on the LiveCD:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by drs305 on 2010-10-30
> **drs305 said:**
> I'll provide some guidance on at least the Ubuntu side.

At some point, Grub2 was installed to the sda6 partition. We can clean that up and get Grub2 installed on the MBR and looking to sda6.

To clear up the sda6 partition boot record (PBR), we can install testdisk and have it clear the PBR. To do this:

[If you are on the LiveCD, open Software Sources or Synaptic and enable the Universe repository via Settings, Repositories, then "Reload" and:]

```
sudo apt-get install testdisk
sudo testdisk /dev/sda6

```
Check in the first testdisk screen that you are in /dev/sda6.
Proceed.
Continue.
Select 'Intel'
Select 'MBR Code', then Y, Y
Quit, Quit

That will clean up the PBR. 

Now to make sure grub looks in the correct place:
If you are booted into your normal install on sda6 without using the LiveCD, run the following. Use *sda* and NOT *sda**6***
```
sudo grub-install /dev/sda
```
That should allow grub to boot normally to your sda6 install.

If you are on the LiveCD:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

This should allow booting to Ubuntu if sda is the drive BIOS looks at first.

Booting Windows may still take a bit of work. Run "sudo update-grub" after rebooting to see if Grub includes Windows in the menu.

---

### Post by joe2005 on 2010-10-30
Thanks.Did as told.Able to remove the unnecessary entry.Thanks once again

---

### Post by Rubi1200 on 2010-10-30
Does this mean you can now boot both Ubuntu and Windows?

If yes, please mark this thread Solved using the Thread Tools near the top of the page.

If no, let us know what you still need help with.

---

