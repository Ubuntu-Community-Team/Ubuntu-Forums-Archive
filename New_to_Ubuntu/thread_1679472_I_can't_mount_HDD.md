---
title: "I can't mount HDD"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by Linux-is-super on 2011-02-01
Hi !

I have 2 HDD . I can't mount sda in Ubuntu. But in Windows XP it works. What can I do ? I try to format HDD and install ubuntu a new. It is still the same.

Here is blkid :

/dev/sda1: LABEL="Novi Podatci" UUID="5850F53F50F52502" TYPE="ntfs" 
/dev/sdb1: UUID="b71d3d48-d29a-4627-a358-19d3a4a96ddb" TYPE="ext4" 
/dev/sdb2: UUID="22c06f64-81d1-477b-a004-d072ecab1d28" TYPE="swap" 
/dev/sdb3: UUID="94245DDB245DC0C2" TYPE="ntfs" 
/dev/sdb5: LABEL="Podatci168G" UUID="44E4891CE489117A" TYPE="ntfs"

---

### Post by lavinog on 2011-02-01
How are you trying to mount it?

What message do you get when you try and mount it?

---

### Post by Linux-is-super on 2011-02-02
Hi @lavinog!
At Ubuntu startup it shows me message that cant mount device. And gives me choice to skip or continue waiting. The only way to load Ubuntu is to press S. And after load there is no HDD listed in computer. But in Windows everything is ok.

---

### Post by pl@yer on 2011-02-02
You should also please provide
```

# cat /etc/fstab

```

---

### Post by Linux-is-super on 2011-02-04
Thank you !
Here are cat /etc/fstab results :

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda3 during installation
UUID=91EA-C165  /windows        vfat    utf8,umask=007,gid=46 0       1
/dev/sda2       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by pl@yer on 2011-02-04
> **Linux-is-super said:**
> Hi !
/dev/sda1: LABEL="Novi Podatci" UUID="5850F53F50F52502" TYPE="ntfs" 

> **Linux-is-super said:**
> 
/dev/sda1 / **ext4** errors=remount-ro 0 1

You have it as ext4 in fstab and it is ntfs... 
I don't know if using ntfs as root filesystem, is a good idea?

---

### Post by presence1960 on 2011-02-04
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Linux-is-super on 2011-02-05
Thank you all ! 
Here is boot info script :


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    78,125,055    78,123,008  83 Linux
/dev/sdb2          78,125,056    82,030,591     3,905,536  82 Linux swap / Solaris
/dev/sdb3    *     82,030,592   160,155,647    78,125,056   7 HPFS/NTFS
/dev/sdb4         160,157,694   488,396,799   328,239,106   5 Extended
/dev/sdb5         160,157,757   488,392,064   328,234,308   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5850F53F50F52502                       ntfs       Novi Podatci                  
/dev/sda: PTTYPE="dos" 
/dev/sdb1        b71d3d48-d29a-4627-a358-19d3a4a96ddb   ext4                                     
/dev/sdb2        22c06f64-81d1-477b-a004-d072ecab1d28   swap                                     
/dev/sdb3        94245DDB245DC0C2                       ntfs                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        44E4891CE489117A                       ntfs       Podatci168G                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(1)partition(4)\WINDOWS.0="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set b71d3d48-d29a-4627-a358-19d3a4a96ddb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b71d3d48-d29a-4627-a358-19d3a4a96ddb
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
    search --no-floppy --fs-uuid --set b71d3d48-d29a-4627-a358-19d3a4a96ddb
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b71d3d48-d29a-4627-a358-19d3a4a96ddb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b71d3d48-d29a-4627-a358-19d3a4a96ddb
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b71d3d48-d29a-4627-a358-19d3a4a96ddb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b71d3d48-d29a-4627-a358-19d3a4a96ddb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b71d3d48-d29a-4627-a358-19d3a4a96ddb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 94245ddb245dc0c2
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda3 during installation
UUID=91EA-C165  /windows        vfat    utf8,umask=007,gid=46 0       1
/dev/sda2       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  30.2GB: boot/grub/core.img
  10.8GB: boot/grub/grub.cfg
  32.4GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/vmlinuz-2.6.35-22-generic
  32.4GB: initrd.img
    .3GB: vmlinuz

================================ sdb3/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  f8 ef be 00 4b d9 1f 00  b8 7f 67 65 85 eb 80 f9  |....K.....ge....|
00000010  42 0f 20 3d a0 f9 ed ae  04 fe bf 5f 1f e0 fa 82  |B. =......._....|
00000020  c5 d9 d6 ec c2 2c d7 01  e8 db ab 9f 0f d6 0f 90  |.....,..........|
00000030  7e 7f 77 de b6 3b c8 07  dc 31 fc 9f b3 7c 3f f2  |~.w..;...1...|?.|
00000040  04 c2 7f 60 ff f5 69 9b  63 8d 48 df 62 f8 16 ba  |...`..i.c.H.b...|
00000050  7f 31 b0 9f 73 80 96 0c  ff 0f a5 bb 87 3f 92 e3  |.1..s........?..|
00000060  ff c9 5f 5e 44 04 f6 ef  a9 af 5f 79 94 c3 6a dc  |.._^D....._y..j.|
00000070  d8 cf be fe c4 fe 03 af  27 3b fe d3 3f c6 f1 3f  |........';..?..?|
00000080  f2 0d 8e ff e1 f7 ef 3d  1b 15 bf 5f cf 03 c8 ff  |.......=..._....|
00000090  ff 84 73 81 91 97 a8 e1  7f cd df ff f5 4f ef f2  |..s..........O..|
000000a0  9c 5f e7 fd 39 ff 6f 7d  0d e1 ff 9f ae 81 41 cc  |._..9.o}......A.|
000000b0  63 4f f7 4f fc 1c 3a ff  74 5d 29 6f 46 5d f5 a7  |cO.O..:.t])oF]..|
000000c0  86 ff 63 fe fb e8 c7 77  dc b7 7e 81 09 f3 05 9d  |..c....w..~.....|
000000d0  73 fc 9f b3 b9 a2 ca cb  07 97 1c ca 1b b0 df fa  |s...............|
000000e0  0d 2d ef 00 1f 39 f2 7d  c7 7f 45 d6 6b 87 9c 8f  |.-...9.}..E.k...|
000000f0  fe 61 2c f2 cb 9d 8e fb  8a c6 fd d3 fb bb 61 fe  |.a,...........a.|
00000100  ff c4 fe 74 be a8 6e 28  1d 10 75 c1 73 e6 ff 2b  |...t..n(..u.s..+|
00000110  3f 7f c4 86 e3 7e a3 c0  ff 8d c8 e7 35 db e6 ab  |?....~......5...|
00000120  00 fb d9 c7 d5 68 f0 3e  d1 70 fc 57 e4 79 01 fc  |.....h.>.p.W.y..|
00000130  c7 1c bf 66 33 f2 05 ba  ef f0 b8 8e ff 1b c5 71  |...f3..........q|
00000140  a3 9f cb 71 5f eb 00 f5  9a 85 4f 7d c2 7c f2 7e  |...q_.....O}.|.~|
00000150  8f d0 9d 03 c7 b8 06 58  3b a5 ff 0c 7d 03 8e fd  |.......X;...}...|
00000160  4b 4f b6 c2 ff 3f e3 ff  a0 e3 ff 60 c5 7f 81 df  |KO...?.....`....|
00000170  1f 7c 16 dd a7 47 fc 5f  be 00 d1 a7 e9 fb 03 45  |.|...G._.......E|
00000180  7f bf e9 43 2d ff 3f e8  b8 3f 78 c9 e7 01 12 fb  |...C-.?..?x.....|
00000190  73 5f 5f 27 70 fe c3 de  d6 f9 0f fb 2c 62 1d 30  |s__'p.......,b.0|
000001a0  34 4c 2d 82 36 f0 7f 60  39 e7 fa e1 1c 80 3e e1  |4L-.6..`9.....>.|
000001b0  63 f4 1d a6 e3 5d 80 d6  ff 2a d7 00 fc 7b 00 fe  |c....]...*...{..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 44 75 90 13 00 00  |......?...Du....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by Linux-is-super on 2011-02-07
Any ideas !

---

### Post by pl@yer on 2011-02-07
In ubuntu try;
```

sudo -s
# [ -d /mnt/sda1 ]||mkdir /mnt/sda1
# mount -t ntfs /dev/sda1 /mnt/sda1
# ls -l /mnt/sda1

```

or 
change "ext4" to "ntfs" in /etc/fstab.

---

