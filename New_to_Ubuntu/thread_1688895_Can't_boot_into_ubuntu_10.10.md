---
title: "Can't boot into ubuntu 10.10"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by flee0308 on 2011-02-16
Recently, I decided to do an actual dual boot with windows vista instead of wubi. My hard drive (500gb) originally looked like this:

11gb -> D: Drive (backup)
Rest -> C: Drive

I decided to partition it like this.

50Gb Windows C: Drive  NTFS ( I just shrunk it )(Primary)
50Gb Linux  / /ext4 (Primary)
8Gb Linux Swap 
5Gb Linux /tmp /ext4
5Gb Linux /var /ext4
341Gb Linux /home /ext4
30Gb shared /windows FAT32
11Gb -> D: Drive (Didn't touch it) (Primary)


I chose to install Ubuntu into the 50Gb ext4 partition.

After restarting the computer, I am unable to enter Ubuntu. There's no boot menu. Instead, I go into Windows straight. My computer has been partitioned, as my windows drive has been shrunk and there's an extra J: Drive (the shared drive).

How can I find the boot menu and boot into ubuntu?

---

### Post by Rubi1200 on 2011-02-16
Hi,
we need to get a better overview of the current setup.

Please do the following;

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Oathanvil on 2011-02-16
did you install 10.10 from the desktop? If you did it will auto create a DUAL boot option you will see at boot-up. If it's not there something went wrong with the installation.

Not sure how to get that boot menue back for you.

If you created a partition on your primary drive and then created a / partition then a /home and a swap space for your ram and then installed ubuntu from disc in DOS then it should also create you a dual boot menue but this one should show you more around 4 or 5 more options to boot from not just the MS, OS and UBUNTU.

---

### Post by flee0308 on 2011-02-16
> **Rubi1200 said:**
> Hi,
we need to get a better overview of the current setup.

Please do the following;

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 125929152 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   100,000,062   100,000,000   7 HPFS/NTFS
/dev/sda2         953,698,725   976,768,064    23,069,340   7 HPFS/NTFS
/dev/sda3         100,001,792   199,999,487    99,997,696  83 Linux
/dev/sda4         200,001,534   953,698,303   753,696,770   5 Extended
/dev/sda5         200,001,536   216,000,511    15,998,976  82 Linux swap / Solaris
/dev/sda6         216,002,560   226,000,895     9,998,336  83 Linux
/dev/sda7         226,002,944   236,001,279     9,998,336  83 Linux
/dev/sda8         893,698,048   953,698,303    60,000,256   b W95 FAT32
/dev/sda9         236,003,328   893,693,951   657,690,624  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        269A23399A230541                       ntfs       COMPAQ                        
/dev/sda2        2C88743C8874071C                       ntfs       FACTORY_IMAGE                 
/dev/sda3        e0177bfc-3297-4152-a13d-034bea0c372a   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        d2c39148-98ee-4103-aac9-3abd69367154   swap                                     
/dev/sda6        bb0d0d04-68ac-4d76-9b20-1d6e71e6e36e   ext4                                     
/dev/sda7        71adb42b-03c9-4673-8054-b25e6a1286a1   ext4                                     
/dev/sda8        53F2-76B1                              vfat                                     
/dev/sda9        e3958bd4-13a6-49f0-b76a-3d046466e915   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set e0177bfc-3297-4152-a13d-034bea0c372a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set e0177bfc-3297-4152-a13d-034bea0c372a
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e0177bfc-3297-4152-a13d-034bea0c372a
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=e0177bfc-3297-4152-a13d-034bea0c372a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e0177bfc-3297-4152-a13d-034bea0c372a
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=e0177bfc-3297-4152-a13d-034bea0c372a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e0177bfc-3297-4152-a13d-034bea0c372a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e0177bfc-3297-4152-a13d-034bea0c372a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 269a23399a230541
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 2c88743c8874071c
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=e0177bfc-3297-4152-a13d-034bea0c372a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=e3958bd4-13a6-49f0-b76a-3d046466e915 /home           ext4    defaults        0       2
# /tmp was on /dev/sda6 during installation
UUID=bb0d0d04-68ac-4d76-9b20-1d6e71e6e36e /tmp            ext4    defaults        0       2
# /var was on /dev/sda7 during installation
UUID=71adb42b-03c9-4673-8054-b25e6a1286a1 /var            ext4    defaults        0       2
# /windows was on /dev/sda8 during installation
UUID=53F2-76B1  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=d2c39148-98ee-4103-aac9-3abd69367154 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  64.4GB: boot/grub/core.img
  90.0GB: boot/grub/grub.cfg
  51.6GB: boot/initrd.img-2.6.35-25-generic-pae
  64.4GB: boot/vmlinuz-2.6.35-25-generic-pae
  51.6GB: initrd.img
  64.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  f9 0c 20 2d bf 4f 54 c5  20 63 96 0a cb 4b c7 d3  |.. -.OT. c...K..|
00000010  22 43 87 e5 e5 16 c1 1b  b9 5d 5c 71 83 87 cc 15  |"C.......]\q....|
00000020  94 98 00 65 87 0f 2c bf  55 c6 52 a2 05 88 7f 4e  |...e..,.U.R....N|
00000030  b5 c5 53 14 ad 20 d3 c2  f2 51 47 6e 2d 4c da 66  |..S.. ...QGn-L.f|
00000040  26 bc e9 6d 3a 9a 47 fd  d2 7e 32 b3 b9 f0 2f 85  |&..m:.G..~2.../.|
00000050  54 c0 9c cf d3 8d 84 10  cf 0f 49 b8 ac 42 48 72  |T.........I..BHr|
00000060  46 e0 12 da 9c 62 63 81  c0 8a f1 b3 dd 83 9d 0e  |F....bc.........|
00000070  e3 55 66 0b 2b 7d b9 8f  1b fa d0 b2 48 1c 0c 04  |.Uf.+}......H...|
00000080  aa d1 9c 3e 1c a7 a8 63  1a e9 29 a0 1d c5 60 4a  |...>...c..)...`J|
00000090  1f 78 22 55 cc 53 31 eb  a3 91 6e 21 b3 4c 95 36  |.x"U.S1...n!.L.6|
000000a0  d6 58 9b 68 eb b0 64 71  fa 37 1a e0 06 6f 95 b6  |.X.h..dq.7...o..|
000000b0  b3 f5 f0 60 6a c1 1c 4d  37 bc 4c 60 81 7b 03 c3  |...`j..M7.L`.{..|
000000c0  fe a6 1d 75 68 bd 21 f1  5b fb 4d 7a 28 e7 27 01  |...uh.!.[.Mz(.'.|
000000d0  b3 07 79 1b 72 73 02 15  fa 25 d8 a1 e0 e0 8a bc  |..y.rs...%......|
000000e0  44 56 e5 98 fa bb 83 83  a2 92 9e 56 9a ba d8 cb  |DV.........V....|
000000f0  18 4d a6 2a c9 1f 99 28  b3 26 73 e0 31 59 6d a5  |.M.*...(.&s.1Ym.|
00000100  ae 00 ba 1a b0 3b 5b 5b  45 f8 8f db 1f 16 c6 69  |.....;[[E......i|
00000110  05 e3 02 03 40 9c 65 8b  78 f5 4a 43 62 9e 9c 14  |....@.e.x.JCb...|
00000120  aa 5c 9c d0 e9 10 07 c1  b0 9e c7 af 48 58 9a 13  |.\..........HX..|
00000130  29 e3 e5 6a 03 d0 14 20  3b 7f 8d 66 1e 12 ab 2a  |)..j... ;..f...*|
00000140  01 3e ad a0 c6 93 b2 c9  13 9e bd 10 0c 0d 38 43  |.>............8C|
00000150  e1 6f f4 11 9d 79 8e 73  67 20 44 ba e8 a0 da 3f  |.o...y.sg D....?|
00000160  fd 90 ae 3e f8 f5 b6 ca  cd 09 83 79 76 79 b4 22  |...>.......yvy."|
00000170  ec 73 ff 3e 85 ad 51 3d  b1 8b 38 ac 64 e9 af fd  |.s.>..Q=..8.d...|
00000180  85 1a 2f 33 28 99 b7 58  b8 24 f0 7c d2 0d b0 a5  |../3(..X.$.|....|
00000190  4c f5 2a 2e d1 d3 17 d2  98 d1 bf f7 82 a9 d0 c6  |L.*.............|
000001a0  c4 d8 0e 8a 51 87 fc 20  86 9e 90 09 d3 84 26 5a  |....Q.. ......&Z|
000001b0  dc ef 38 6c 2b fe 6e 48  30 8a b1 8a 2f d0 00 fe  |..8l+.nH0.../...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 20 f4 00 00 fe  |........... ....|
000001d0  ff ff 05 fe ff ff 02 20  f4 00 00 98 98 00 00 00  |....... ........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdg 

```

> **Oathanvil said:**
> did you install 10.10 from the desktop? If you did it will auto create a DUAL boot option you will see at boot-up. If it's not there something went wrong with the installation.

Not sure how to get that boot menue back for you.

If you created a partition on your primary drive and then created a / partition then a /home and a swap space for your ram and then installed ubuntu from disc in DOS then it should also create you a dual boot menue but this one should show you more around 4 or 5 more options to boot from not just the MS, OS and UBUNTU.

I installed from the disc, without booting windows.

---

### Post by Rubi1200 on 2011-02-16
Somehow GRUB was installed to the partition instead of the MBR of the drive.

To correct this, do the following from the LiveCD:
[FONT=monospace]
[/FONT]```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
run ```
sudo update-grub
``` back in Ubuntu to pick up the Windows install.

---

