---
title: "lost  XP on dual boot"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by worlestone on 2011-04-17
I have recently moved from running ubuntu via wubi with Windows XP to installing lubuntu in it's own partition.

All went well, but I have noticed that XP does not now appear in Grub. Not sure what I should post here to ask for help, but some starters would be appreciated.

Thanks in advance

Adrian

---

### Post by ububeginner on 2011-04-17
Try opening a terminal and enter the command:

sudo update-grub

---

### Post by Rubi1200 on 2011-04-17
If the advice posted by ububeginner doesn't resolve the issue, then please do the following from within your Ubuntu install:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
 sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by oldfred on 2011-04-17
If you installed Lubuntu, you probably have to install the os-prober to get the update-grub to work. So try this, then the udate as suggested by ububeginner, and it that does not work follow Rubi1200's instructions on the boot script.

```
sudo apt-get install os-prober
sudo update-grub
```

---

### Post by Leppie on 2011-04-17
could you post the outputs of the following commands:
```
blkid
sudo fdisk -l
```

---

### Post by worlestone on 2011-04-17
Thank you all for the swift and helpful replies, I'm now back and dual booting fine with:

sudo apt-get install os-prober
sudo update-grub

Thanks you

---

### Post by oldfred on 2011-04-17
Glad you got it working.:)

@Leppie
The boot script includes both of those commands and much more for analysis of a booting issue.

---

### Post by Leppie on 2011-04-17
oldfred, i know it does 
you may not remember me, but i remember you ;)

---

### Post by Rubi1200 on 2011-04-18
> **worlestone said:**
> Thank you all for the swift and helpful replies, I'm now back and dual booting fine with:

sudo apt-get install os-prober
sudo update-grub

Thanks you
Excellent, glad you got it sorted out :-)

---

### Post by bobhurt on 2011-04-18
I also lost my windows boot option from the ubuntu boot menu.

I have this result from
sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xead8ead8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2          118661      182401   511999582+   7  HPFS/NTFS
/dev/sda3           12749       76489   511999582+   7  HPFS/NTFS
/dev/sda4           76490      118660   338738527    5  Extended
/dev/sda5           76490       79104    21004956   82  Linux swap / Solaris
/dev/sda6           79105       91852   102398278+  83  Linux
/dev/sda7           91853      118660   215335228+   b  W95 FAT32

Result from bootinfo

         Boot Info Script 0.55    dated February 15th, 2010                    

[http://ubuntuforums.org/showthread.php?t=1731894](http://ubuntuforums.org/showthread.php?t=1731894)
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
moved bootinfoscript to desktop
sudo bash ~/Desktop/boot_info_script*.sh

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2       1,906,272,900 2,930,272,064 1,023,999,165   7 HPFS/NTFS
/dev/sda3         204,796,620 1,228,795,784 1,023,999,165   7 HPFS/NTFS
/dev/sda4       1,228,795,846 1,906,272,899   677,477,054   5 Extended
/dev/sda5       1,228,795,848 1,270,805,759    42,009,912  82 Linux swap / Solaris
/dev/sda6       1,270,805,823 1,475,602,379   204,796,557  83 Linux
/dev/sda7       1,475,602,443 1,906,272,899   430,670,457   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3C5CE1225CE0D822                       ntfs       WinXP_Orig                    
/dev/sda2        6208A8F208A8C67F                       ntfs       WinXP_Main                    
/dev/sda3        465442F910712411                       ntfs       Windows7                      
/dev/sda4: PTTYPE="dos" 
/dev/sda5        43560e49-6acb-482d-8583-c5e3aa64cc42   swap       Ubuntu-Swap                   
/dev/sda6        7e164617-3aae-4158-b431-f7c8aa778628   ext2                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext2       (rw,errors=remount-ro)
/dev/sda1        /media/WinXP_Orig        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	echo	'Loading Linux 2.6.35-26-generic ...'
	linux	/boot/vmlinuz-2.6.35-26-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7e164617-3aae-4158-b431-f7c8aa778628 ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 7e164617-3aae-4158-b431-f7c8aa778628
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3c5ce1225ce0d822
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
# / was on /dev/sda6 during installation
UUID=7e164617-3aae-4158-b431-f7c8aa778628 /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=43560e49-6acb-482d-8583-c5e3aa64cc42 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 753.4GB: boot/grub/core.img
 753.5GB: boot/grub/grub.cfg
 753.2GB: boot/initrd.img-2.6.35-22-generic
 753.2GB: boot/initrd.img-2.6.35-23-generic
 753.2GB: boot/initrd.img-2.6.35-24-generic
 753.3GB: boot/initrd.img-2.6.35-25-generic
 753.3GB: boot/initrd.img-2.6.35-26-generic
 753.3GB: boot/initrd.img-2.6.35-27-generic
 753.3GB: boot/initrd.img-2.6.35-28-generic
 753.3GB: boot/vmlinuz-2.6.35-22-generic
 753.2GB: boot/vmlinuz-2.6.35-23-generic
 753.2GB: boot/vmlinuz-2.6.35-24-generic
 753.2GB: boot/vmlinuz-2.6.35-25-generic
 753.3GB: boot/vmlinuz-2.6.35-26-generic
 753.3GB: boot/vmlinuz-2.6.35-27-generic
 753.2GB: boot/vmlinuz-2.6.35-28-generic
 753.3GB: initrd.img
 753.3GB: initrd.img.old
 753.2GB: vmlinuz
 753.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda7

00000000  b9 62 c0 ad c0 36 50 43  04 5d 8f 08 bb a5 13 ef  |.b...6PC.]......|
00000010  26 8b 46 ce 2e 6e e9 1c  38 89 99 2a bd 99 fd 7c  |&.F..n..8..*...||
00000020  a0 99 ef 67 73 09 d6 e7  23 e2 e9 d9 a8 ec 0b 50  |...gs...#......P|
00000030  52 d3 7c c7 4c 85 56 41  a4 63 87 bc d4 8b 38 21  |R.|.L.VA.c....8!|
00000040  22 f2 f4 51 ac 26 f3 09  86 20 f4 12 e6 fd 9e b7  |"..Q.&... ......|
00000050  61 ee 81 4b 6d 63 45 ef  29 7c ce 43 06 d2 16 51  |a..KmcE.)|.C...Q|
00000060  68 d7 51 6c 75 41 2c 09  f2 e4 25 1f 96 06 25 38  |h.QluA,...%...%8|
00000070  a0 a4 e4 64 ce a2 ed bb  04 07 48 48 94 ba 09 03  |...d......HH....|
00000080  1f e0 fd 2c 8a 52 24 b0  a8 18 d2 fe 24 b4 bc c9  |...,.R$.....$...|
00000090  e1 51 0e d9 c4 8d c2 e2  5f 91 60 32 24 d2 87 9c  |.Q......_.`2$...|
000000a0  1d db 41 2e fb 27 f1 e5  0f d1 81 42 3b 58 08 4a  |..A..'.....B;X.J|
000000b0  6c 07 1c 29 90 52 76 7c  43 44 18 1b c0 f6 8b dc  |l..).Rv|CD......|
000000c0  60 0b 05 d5 da 53 46 59  fe 40 5e 2d 9e 00 a5 6b  |`....SFY.@^-...k|
000000d0  ad e7 22 3c 06 ba 02 16  56 60 7a 65 7b 75 a0 64  |.."<....V`ze{u.d|
000000e0  8e 1d b9 43 48 c1 b4 ae  07 6f 25 3d 44 da 08 b3  |...CH....o%=D...|
000000f0  54 11 19 4a 93 87 10 5c  eb d5 78 0b 43 a3 6b b9  |T..J...\..x.C.k.|
00000100  28 b5 5b 96 ca 9d 8d 09  92 91 1f 27 2e 24 a1 12  |(.[........'.$..|
00000110  c5 4c 6a 8a 9e d8 f0 8f  b6 da 37 6e 7a 2b 24 cc  |.Lj.......7nz+$.|
00000120  cd 44 0c 52 05 74 7b 1c  98 79 97 bd c7 e6 b2 06  |.D.R.t{..y......|
00000130  4f a2 d7 a4 ec 2d 9f c5  d3 cc 69 66 d7 82 f3 d9  |O....-....if....|
00000140  30 f1 d3 38 e4 53 73 0a  8d 2f a5 1b b2 75 8b 97  |0..8.Ss../...u..|
00000150  0c b3 c8 bd a4 fc 13 3b  a4 24 af 7e ac 5c 2a 89  |.......;.$.~.\*.|
00000160  0b 30 c2 2e 67 fb 34 19  fa fd bb 96 0c de 6c 61  |.0..g.4.......la|
00000170  e0 6b 0c ad 76 88 42 aa  6d fe 72 4a 2e 1a 9a 8d  |.k..v.B.m.rJ....|
00000180  52 f9 3a 1d 86 48 cc f5  c6 de bf e2 22 ba a7 f4  |R.:..H......"...|
00000190  f0 6f 26 85 c0 51 c2 77  14 ce 60 5c e7 05 dc 66  |.o&..Q.w..`\...f|
000001a0  31 de bf e5 ca 98 15 9a  cb 69 53 53 b1 fe c1 fe  |1........iSS....|
000001b0  7e 63 68 c9 7c 56 4d d5  06 41 1c b7 33 d7 a2 6c  |~ch.|VM..A..3..l|
000001c0  fc d3 1c c6 45 f6 fa 8d  2f af 65 58 e5 25 fd 1c  |....E.../.eX.%..|
000001d0  17 e4 96 d1 ed 24 54 7c  67 c8 71 5f c1 32 19 aa  |.....$T|g.q_.2..|
000001e0  a3 0f 17 00 ca e6 df c4  66 ef 82 40 f2 34 fc d0  |........f..@.4..|
000001f0  9e 45 71 44 2d 28 be da  ad b9 fc 50 c6 8f 8b 54  |.EqD-(.....P...T|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 





I have update-grub2 to no avail,  CANNOT get windows to show up in boot list.  Any clue?

---

### Post by oldfred on 2011-04-18
Your windows 7 is in the boot list. Windows combines all the boot files from all the installs into the active partition(boot flag). So Grub will only find one bootable windows install. If you have more than one install you have to update the BCD with BCDedit in windows.

Multibooters, Pictures here worth 1000+ words - Discusses Vista with XP but 7 is same
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by bobhurt on 2011-04-18
Thanks oldfred.    When I reboot, Windows 7 does not appear in the boot options.  It used to appear at the end.  I know bupkus about grub, such as where it gets the data it puts in the boot-up list of which system to boot.  If it gets the list from the same place as bootinfo, it clearly ignores the Windows 7 entry.  Look at this:

> ### BEGIN /etc/grub.d/30_os-prober ###
[COLOR="Red"]menuentry "Windows 7[/COLOR] (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3c5ce1225ce0d822
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the [COLOR="red"]'exec tail'[/COLOR] line above.
### END /etc/grub.d/40_custom ###

The win 7 boot item SHOULD display.

WHAT 'exec tail'?  I saw none, so maybe the process hosed it and it does not show the win 7 boot option for that reason.

In my system I installed win 7 after win xp, so the win 7 partition gives me the option to boot xp.  Win 7 got hosed somehow and I haven't bothered fixing it because when I do it will hose grub, and I'll have to set up some way beforehand to fix that.

Can you help me figure out how to get windows 7 to show up in the boot list?

I terribly miss Acrobat Pro in UBUNTU.  I haven't tried it under WINE.  If I had that and a Linux version of Outlook, I'd hose windows for good. Any comments on that?

---

### Post by oldfred on 2011-04-18
When the grub menu appears is there a little tiny arrow on the right side of the menu box? If so you have to scroll down for more entries.

You may want to house clean old kernels. You should keep current & one old one that works. 

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
HOWTO: Remove Older Kernels via GUI Tweak
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

