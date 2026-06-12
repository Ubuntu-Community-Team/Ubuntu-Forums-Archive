---
title: "Ubuntu 10.04 with Windows Boot Loader?"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by avgazn on 2010-08-01
I really hate grub. I don't know why but I just like Windows Boot Loader more. I have installed Ubuntu first then my windows distros. In the past versions I have used EasyBCD and it worked fine but now I can't seem to get it to work. Is there any way to use Windows Boot Loader to load into Ubuntu?

---

### Post by sikander3786 on 2010-08-01
> **avgazn said:**
> Is there any way to use Windows Boot Loader to load into Ubuntu?

Not possible. Stick with EasyBCD or GRUB or GRUB2 or LILO.

---

### Post by avgazn on 2010-08-01
> **sikander3786 said:**
> Not possible. Stick with EasyBCD or GRUB or GRUB2 or LILO.

Doesn't EasyBCD just change the configuration of windows Bootloader? How can I use EasyBCD to detect Ubuntu?

---

### Post by Mi11z on 2010-08-01
If it's the way grub looks that's your problem you might wanna try BURG here:

```
http://code.google.com/p/burg/wiki/Screenshots
```

It has a lot of really good looking themes as well as some funny ones, which if you have burg manager installed (makes the whole burg instillation A LOT easier!) anyway burg and it's manager work and look great as a boot/kernel loader goes, here's the manager:

```
http://www.sourceslist.eu/burg-2/burg-manager-configurare-e-installare-il-burg-non-e-mai-stato-cosi-semplice/
```

Make sure you use google translate for that last link, the developer is Italian you see. :)

hope this helped!
:popcorn:

---

### Post by sikander3786 on 2010-08-01
Here it is

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by sikander3786 on 2010-08-01
> **Mi11z said:**
> If it's the way grub looks that's your problem you might wanna try BURG here:


That is something really awesome. GRUB vs BURG.....

---

### Post by Jahid65 on 2010-08-01
To install burg run the following codes
```
sudo add-apt-repository ppa:bean123ch/burg
sudo apt-get update && sudo apt-get install burg burg-themes 
```**Install BURG to your Master Boot Record**   Install burg to your MBR using the command below. Substitute ‘hd0’ with an alternative drive if needed.
```
sudo burg-install "(hd0)"
```
You **MUST **update the burg
```
sudo update-burg
```

---

### Post by wilee-nilee on 2010-08-01
This is what some have gotten to work easybcd2.
[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

To be honest since the bootloader is only in the MBR of the hardrive, going this route is actually harder, grub2 works fine when used with a little understanding.

---

### Post by avgazn on 2010-08-01
> **Jahid65 said:**
> To install burg run the following codes
```
sudo add-apt-repository ppa:bean123ch/burg
sudo apt-get update && sudo apt-get install burg burg-themes 
```**Install BURG to your Master Boot Record**   Install burg to your MBR using the command below. Substitute ‘hd0’ with an alternative drive if needed.
```
sudo burg-install "(hd0)"
```
You **MUST **update the burg
```
sudo update-burg
```

I've decided this is pretty cool and I want to do this but I have tried to restore my grub and it didn't work. I loaded up my live CD, opened up terminal, put in the commands, and it said grub could not be found. I went to get my data off the drive to back it up but I couldn't because I didn't have the permissions to open the folder. How can I fix the grub or get the folder so I can just reinstall Ubuntu?

---

### Post by wilee-nilee on 2010-08-01
> **avgazn said:**
> I've decided this is pretty cool and I want to do this but I have tried to restore my grub and it didn't work. I loaded up my live CD, opened up terminal, put in the commands, and it said grub could not be found. I went to get my data off the drive to back it up but I couldn't because I didn't have the permissions to open the folder. How can I fix the grub or get the folder so I can just reinstall Ubuntu?

Post the bootscript in my signature in code tags as described.

---

### Post by avgazn on 2010-08-01
> **wilee-nilee said:**
> Post the bootscript in my signature in code tags as described.

Here it is.

```

            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdf5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   409,593,239   409,593,177   7 HPFS/NTFS
/dev/sda2         409,593,240   614,389,859   204,796,620   7 HPFS/NTFS
/dev/sda3         614,389,860   819,186,479   204,796,620   7 HPFS/NTFS
/dev/sda4         819,187,710   976,768,064   157,580,355   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5         819,187,712   923,224,063   104,036,352  83 Linux
/dev/sda6         923,226,112   925,566,975     2,340,864  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1              16,065   625,137,344   625,121,280   f W95 Ext d (LBA)
Extended  partition  linking to another extended partition
/dev/sdf5              16,128   625,137,344   625,121,217   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        73BBD2C24345E9ED                       ntfs       Windows XP                    
/dev/sda2        6AB518A756038BEB                       ntfs       Windows 7                     
/dev/sda3        626C557B29E2A5A1                       ntfs       Windows Vista                 
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3db86eac-8b29-4601-8901-cc05297a0752   ext4                                     
/dev/sda6        d8c331b5-beda-4997-9761-06967702fcdb   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1: PTTYPE="dos" 
/dev/sdf5        01E8-01F1                              vfat       HP PERSONAL                   
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/Windows Vista     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 3db86eac-8b29-4601-8901-cc05297a0752
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
search --no-floppy --fs-uuid --set 3db86eac-8b29-4601-8901-cc05297a0752
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3db86eac-8b29-4601-8901-cc05297a0752
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=3db86eac-8b29-4601-8901-cc05297a0752 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3db86eac-8b29-4601-8901-cc05297a0752
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=3db86eac-8b29-4601-8901-cc05297a0752 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3db86eac-8b29-4601-8901-cc05297a0752
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3db86eac-8b29-4601-8901-cc05297a0752 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3db86eac-8b29-4601-8901-cc05297a0752
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3db86eac-8b29-4601-8901-cc05297a0752 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3db86eac-8b29-4601-8901-cc05297a0752
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 3db86eac-8b29-4601-8901-cc05297a0752
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=3db86eac-8b29-4601-8901-cc05297a0752 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=d8c331b5-beda-4997-9761-06967702fcdb none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 421.7GB: boot/grub/core.img
 462.5GB: boot/grub/grub.cfg
 421.7GB: boot/initrd.img-2.6.32-21-generic
 421.7GB: boot/initrd.img-2.6.32-23-generic
 421.7GB: boot/vmlinuz-2.6.32-21-generic
 421.8GB: boot/vmlinuz-2.6.32-23-generic
 421.7GB: initrd.img
 421.7GB: initrd.img.old
 421.8GB: vmlinuz
 421.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdf5

00000000  eb 58 90 50 41 52 41 47  4f 4e 23 00 02 20 20 00  |.X.PARAGON#..  .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 97 42 25 e0 53 02 00  00 00 00 00 02 00 00 00  |..B%.S..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 f1 01 e8 01 48  50 20 50 65 72 73 6f 6e  |..)....HP Person|
00000050  61 6c 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |alFAT32   ......|
00000060  7b fb 8e d8 8e c0 fc bf  20 00 33 c0 b9 15 00 af  |{....... .3.....|
00000070  75 05 af 75 04 e2 f8 47  47 81 7d fe 00 c0 72 0a  |u..u...GG.}...r.|
00000080  e2 ed 81 3e 02 01 00 c0  73 0f be 88 7d e8 3f 00  |...>....s...}.?.|
00000090  33 c0 cd 16 3d 00 3b 75  f7 be a7 7c bf a7 7e b9  |3...=.;u...|..~.|
000000a0  71 00 f3 a5 e9 00 02 bb  00 7c b9 01 00 be e1 7e  |q........|.....~|
000000b0  e8 1c 00 33 c0 cd 16 b8  01 02 33 d2 50 cd 13 58  |...3......3.P..X|
000000c0  cd 13 72 e3 81 3e fe 7d  55 aa 75 db e9 31 fd 50  |..r..>.}U.u..1.P|
000000d0  53 51 ac 3c 00 75 04 59  5b 58 c3 b4 0e cd 10 eb  |SQ.<.u.Y[X......|
000000e0  f1 0a 0d 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
000000f0  73 6b 20 6f 72 20 64 69  73 6b 20 65 72 72 6f 72  |sk or disk error|
00000100  0a 0d 49 6e 73 65 72 74  20 44 4f 53 20 64 69 73  |..Insert DOS dis|
00000110  6b 65 74 74 65 20 61 6e  64 20 70 72 65 73 73 20  |kette and press |
00000120  61 6e 79 20 6b 65 79 20  2e 2e 2e 0a 0d 00 00 00  |any key ........|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  00 00 00 00 00 00 00 00  0a 0d 50 6f 73 73 69 62  |..........Possib|
00000190  6c 65 20 62 6f 6f 74 20  56 49 52 55 53 20 64 65  |le boot VIRUS de|
000001a0  74 65 63 74 65 64 21 0a  0d 50 72 65 73 73 20 3c  |tected!..Press <|
000001b0  46 31 3e 20 74 6f 20 63  6f 6e 74 69 6e 75 65 00  |F1> to continue.|
000001c0  0d 0a 50 57 2f 44 42 20  62 79 20 4b 49 52 20 56  |..PW/DB by KIR V|
000001d0  2e 20 28 43 29 20 50 61  72 61 67 6f 6e 20 31 39  |. (C) Paragon 19|
000001e0  39 37 2d 31 39 39 39 00  00 00 00 00 00 00 00 00  |97-1999.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by wilee-nilee on 2010-08-01
Follow this link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

In your case it would be in the terminal, in a live cd.
```
sudo mount /dev/sda5 /mnt
```
Then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot to Ubuntu and run. 
```
sudo update-grub
```

---

