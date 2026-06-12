---
title: "Cant use hard disk space!"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by Ajay Ramaseshan on 2010-12-06
hey
ive run into a serous problem,
have a HP Pavillion dm4 Laptop
I thought of installing Ubuntu 10.10 along Windows 7 and 
thought of creating 3 partiions one for the Ubuntu one for the 
windows and one for my user data.
So windows created 100 Mb Syttem Primary Partion upon installation
So I created a 50 GB primary partiton for Windows programs,
and 477 Mb BOot Partition for Linux also primary partition
2.79 GB swap Partition for Swap also Primary Partition
48 GB Primary Partition for /root for Linux
and 15 GB /home Partition also Primary Partiton,
so now i have 350 GB unallocated space.
Now I went back to Windows 7 and tried to allocate this as my data files partition but Windows refuses . .saying that disk already contains the maximum no of partitions.
I am totally stuck now . cant use more than 70 % of my HDD///

DO I need to resinstall Ubuntu ?? and how ?? like which partitions of Ubuntu installations can be made logical .so that this error does not crop up ?? or is it not possible to partition the disk this way ? what s the maximum no of partitons possible ? .. please help   me.. its driving me crazy..!!:confused::confused:

---

### Post by Ajay Ramaseshan on 2010-12-06
For betteerclarity i m attachinga pic of my HDD space ;;: please open it in a new window.. as the thumbnail s too small here.,!

---

### Post by coffeecat on 2010-12-06
> **Ajay Ramaseshan said:**
> Now I went back to Windows 7 and tried to allocate this as my data files partition but Windows refuses . .saying that disk already contains the maximum no of partitions.

That sounds as though you have 4 primary partitions or that you have 3 primary and one extended partition and Windows doesn't know how to make logical partitions in the extended. The details are not clear from your Windows Disk Utility screenshot, so boot up with the Ubuntu live CD, go to the live desktop (not the installer), open a terminal and post the output of:

```
sudo fdisk -lu
```That way we can see what your partition layout is like and what you can do about it. Also, if you are trying to make a NTFS data partition, that would be better done in the live CD - Windows will be quite happy with a NTFS partition made with Gparted in the live CD.

---

### Post by Ajay Ramaseshan on 2010-12-06
> **coffeecat said:**
> That sounds as though you have 4 primary partitions or that you have 3 primary and one extended partition and Windows doesn't know how to make logical partitions in the extended. The details are not clear from your Windows Disk Utility screenshot, so boot up with the Ubuntu live CD, go to the live desktop (not the installer), open a terminal and post the output of:

```
sudo fdisk -lu
```That way we can see what your partition layout is like and what you can do about it. Also, if you are trying to make a NTFS data partition, that would be better done in the live CD - Windows will be quite happy with a NTFS partition made with Gparted in the live CD.

Hey I ran the fdisk -lu and got this output :

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f22e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   104859647    52326400    7  HPFS/NTFS
/dev/sda3       104859648   105836543      488448   83  Linux
/dev/sda4       105838590   241694719    67928065    5  Extended
/dev/sda5       105838592   111695871     2928640   82  Linux swap / Solaris
/dev/sda6       111697920   211695615    49998848   83  Linux
/dev/sda7       211697664   241694719    14998528   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204885504 bytes
255 heads, 62 sectors/track, 123562 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520063   976760000+   7  HPFS/NTFS

I am also attaching the output of Gparted for better clarity :
So now it is possible to use linux live Cd  s Gparted tool to allocate the HUGE unnallocated space as an NTFS partition..??

AJay

---

### Post by Ajay Ramaseshan on 2010-12-06
Btw i have got stuck in Linux also,..
I tried allocating the free space and got this error..

**It is not possible to create more than 4 primary partitions**
*If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first.*

I jus wanto create a partition that has NO os installation and can store my data.. what do I do from here..??

Ajay

---

### Post by Quackers on 2010-12-06
In Ubuntu please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Ajay Ramaseshan on 2010-12-06
Hey here is the output of RESULTS.TXT

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   104,859,647   104,652,800   7 HPFS/NTFS
/dev/sda3         104,859,648   105,836,543       976,896  83 Linux
/dev/sda4         105,838,590   241,694,719   135,856,130   5 Extended
/dev/sda5         105,838,592   111,695,871     5,857,280  82 Linux swap / Solaris
/dev/sda6         111,697,920   211,695,615    99,997,696  83 Linux
/dev/sda7         211,697,664   241,694,719    29,997,056  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204885504 bytes
255 heads, 62 sectors/track, 123562 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,063 1,953,520,001   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        341AF5931AF5527A                       ntfs       System Reserved               
/dev/sda2        8E8EFDBD8EFD9DC1                       ntfs                                     
/dev/sda3        7a4958ba-5e95-447f-a4df-ccdb09b8283e   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        eb138d61-f388-4be1-812e-1bdef5859d2d   swap                                     
/dev/sda6        a5d8980e-4c25-4f65-af4d-4a84a2464157   ext4                                     
/dev/sda7        2d3206a8-0ad6-44bc-96c4-0def3b2d46ee   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2A808CAA808C7E57                       ntfs       infinity                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda3/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set a5d8980e-4c25-4f65-af4d-4a84a2464157
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 7a4958ba-5e95-447f-a4df-ccdb09b8283e
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 7a4958ba-5e95-447f-a4df-ccdb09b8283e
	linux	/vmlinuz-2.6.35-23-generic-pae root=UUID=a5d8980e-4c25-4f65-af4d-4a84a2464157 ro   quiet splash
	initrd	/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 7a4958ba-5e95-447f-a4df-ccdb09b8283e
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/vmlinuz-2.6.35-23-generic-pae root=UUID=a5d8980e-4c25-4f65-af4d-4a84a2464157 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 7a4958ba-5e95-447f-a4df-ccdb09b8283e
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 7a4958ba-5e95-447f-a4df-ccdb09b8283e
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 341af5931af5527a
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

=================== sda3: Location of files loaded by Grub: ===================


  53.8GB: grub/core.img
  53.8GB: grub/grub.cfg
  53.7GB: initrd.img-2.6.35-23-generic-pae
  53.7GB: vmlinuz-2.6.35-23-generic-pae

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
UUID=a5d8980e-4c25-4f65-af4d-4a84a2464157 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=7a4958ba-5e95-447f-a4df-ccdb09b8283e /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=2d3206a8-0ad6-44bc-96c4-0def3b2d46ee /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=eb138d61-f388-4be1-812e-1bdef5859d2d none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  db 9a e3 8a 55 41 a2 a7  0e 8e 72 1c a2 a8 22 2a  |....UA....r..."*|
00000010  20 e3 82 02 31 f4 39 80  fd b8 3a 04 09 24 db b3  | ...1.9...:..$..|
00000020  18 20 71 02 55 42 89 14  69 c6 e6 79 fe 65 e4 ff  |. q.UB..i..y.e..|
00000030  ff 8a 4a 5f 7b fd 7f ff  fb 92 04 f6 80 02 f8 67  |..J_{..........g|
00000040  d2 d3 01 42 f2 5e ac fa  7a 3c 25 5e 4a e9 9f 4c  |...B.^..z<%^J..L|
00000050  e7 84 ab c9 6c 33 e9 e8  f0 95 79 ea 4b 4d 5d fd  |....l3....y.KM].|
00000060  34 df fe ae da db ff f3  a1 0e 8c 72 aa 28 88 c1  |4..........r.(..|
00000070  e1 64 51 55 87 46 b1 c4  ca ff a7 f4 db 11 43 97  |.dQU.F........C.|
00000080  39 9d c8 a5 54 1a 1d 38  74 73 90 68 74 15 0a 1d  |9...T..8ts.ht...|
00000090  10 71 50 80 8b 8b 58 7b  89 e6 06 82 81 49 34 ac  |.qP...X{.....I4.|
000000a0  c2 28 0a 80 c4 a3 14 94  10 50 c8 a2 57 3f f8 e6  |.(.......P..W?..|
000000b0  ff ff 9c 43 fa 83 7f da  bf ef 38 d4 54 71 ca 3f  |...C......8.Tq.?|
000000c0  af ff d5 7f ff fa 5d 8e  34 7a 4c 75 18 60 b8 f9  |......].4zLu.`..|
000000d0  67 28 40 7e 64 b9 23 09  33 f3 d2 9b ed 5b d1 18  |g(@~d.#.3....[..|
000000e0  f3 ca bb 8f 1a 7b a1 ce  31 11 58 f3 4f 14 8d 89  |.....{..1.X.O...|
000000f0  93 20 50 6e ce 2d 9c 3c  40 e1 d1 e0 69 87 93 18  |. Pn.-.<@...i...|
00000100  04 92 92 8e 9d 81 10 09  d1 ac 90 0e 45 88 2a e7  |............E.*.|
00000110  2f fd ef ff cf 32 bf eb  7f db ff 5b 2f 93 7e df  |/....2.....[/.~.|
00000120  ff 95 7f ff fe 7b 95 22  e2 a2 05 0c 39 48 a2 03  |.....{."....9H..|
00000130  95 08 38 5c 48 8f 7b 55  3d f6 d6 b2 54 ea 3d d2  |..8\H.{U=...T.=.|
00000140  ee 43 1c 72 07 59 d8 e3  44 85 c7 8a 10 0e c3 c1  |.C.r.Y..D.......|
00000150  68 8c 83 4c e8 71 e0 00  cb 8a 82 b6 e0 7a f0 6b  |h..L.q.......z.k|
00000160  03 84 2f b1 38 3a c2 d7  c9 32 64 8a 1b 2f 5d 99  |../.8:...2d../].|
00000170  7f fe b5 09 bd 33 ef b7  fe ef ff fe be 7d 7e ff  |.....3.......}~.|
00000180  ff ff ff ff fb ff ff 8f  8f ff f8 5d 5a 98 a4 12  |...........]Z...|
00000190  2b 17 64 a0 8c e2 8b 25  b0 e2 2a 6f ff f5 db ea  |+.d....%..*o....|
000001a0  39 d6 d7 29 b6 a6 1a fc  22 a1 22 4b 16 1a d4 38  |9..)...."."K...8|
000001b0  46 0f c6 1a 28 22 5b 96  62 a8 a9 32 18 0b 00 fe  |F...("[.b..2....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 59 00 00 fe  |...........`Y...|
000001d0  ff ff 05 fe ff ff 02 60  59 00 00 e0 f5 05 00 00  |.......`Y.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

AJay

---

### Post by julio_cortez on 2010-12-06
From the GParted screen it looks like you have 3 primary and an extended partition.

Aren't you able to create something like a logical partition named **/sda8** *inside /sda4* (which is extended so it can contain logical partitions) with gparted?
I guess you should **extend /sda4** before doing anything else, in order for it to use all the unallocated space left. Of course you won't be able to create any other partition outside of /sda4 at the moment.

If you could create an NTFS logical aprtition within /sda4, I guess Windows wouldn't have problems in reading it..

---

### Post by Quackers on 2010-12-06
The screenshot you posted earlier does not agree with the output of the boot script. Your screenshot says you have 6 primary partitions. The maximum on any one disc is 4. The boot script says you have 3 primary partitions and an extended one. Let me look at this more closely. I'll get back to you shortly.

---

### Post by Quackers on 2010-12-06
julio_cortez's suggestion will work handsomely :-)
Extend sda4 to the end of the disc. This will give you another 350GB in sda4 to create another partition (or more) for your uses.

---

### Post by ingeva on 2010-12-06
> **Ajay Ramaseshan said:**
> hey
ive run into a serous problem,
have a HP Pavillion dm4 Laptop
I thought of installing Ubuntu 10.10 along Windows 7 and 
thought of creating 3 partiions one for the Ubuntu one for the 
windows and one for my user data.Not a bad thought.
However, there's one thing you need to know:
And hard disk system can contain up to 4 partitions.
However, someone has invented a trick that will help you to know:
One of the partitions (or more, I never tried) can be made into
what they call an EXTENDED partition (contrary to a PRIMARY one).
The Extended partition can be divided into one or more LOGICAL
partitions. You can do "anything" with those.
So here's my suggestion:
Using Windows, make all the partitions you need for Windows.
Leave the rest of the disk space unused and unpartitioned.

When you install Ubuntu, you come to a stage that allows you to
create and modify partitions. Personally I use the server edition
because it installs faster, and when you install ubuntu-desktop
and others, you get the newest edition the first time so you need
only do that once.
But back to the partitions. This is what I use:
In the PRIMARY partitions:
Boot partition: 10GB.
Home partition: 4 GB.
LOGICAL partitions:
SWAP partition: 4 GB.
STORAGE area (most people use the /home partition for
this but my way gives more flexibility)

In addition, I have this luxury:
/BACKUP partition (on a separate disk)
/MY partition (where I keep a lot of goodies, like music, videos, picture)
/FREE partition (extra backup)

Note that the EXTENDED partition takes up one partition in the
partition table, but no actual disk space.

Always install Windows first, because Microsoft doesn't
like other operating systems to they remove their boot
information. Anyone who want to sabotage MS has my
blessing. :)

---

### Post by Ajay Ramaseshan on 2010-12-06
> **julio_cortez said:**
> From the GParted screen it looks like you have 3 primary and an extended partition.

Aren't you able to create something like a logical partition named **/sda8** *inside /sda4* (which is extended so it can contain logical partitions) with gparted?
I guess you should **extend /sda4** before doing anything else, in order for it to use all the unallocated space left. Of course you won't be able to create any other partition outside of /sda4 at the moment.

If you could create an NTFS logical aprtition within /sda4, I guess Windows wouldn't have problems in reading it..

I thought of doing the same thing but how do I extend a partition in Gparted?? If I click on the unallocated space it just says "new" and doesnt create it under /sda4 !! am i missing something ??

AJay

---

### Post by coffeecat on 2010-12-06
> **Ajay Ramaseshan said:**
> how do I extend a partition in Gparted?? 

First right-click on sda5, your swap partition, and choose 'swapoff' otherwise you won't be able to do anything. Then click on sda4, your extended partition, and go to Partition > Resize/Move. Increase the size up to the physical end of the disc. Click on Apply. Now you will be able to create a new logical partition or partitions in the unused space.

---

### Post by Ajay Ramaseshan on 2010-12-06
Hey ppl\
Thank you SO much for helping me out.. I just did as instructed 
and Windows Reads the new logical Partition perfectly .. 
and I now have a partiton independent of Os . where I can store my dataa..

Thanks a lot.. :) :)
Ajay

---

### Post by julio_cortez on 2010-12-07
You're welcome. Unfortunately I got in too late to explain how to resize /sda4 in gparted but I saw coffeecat came in help ;)

By the way, seeing that everything went fine you should consider making this thread solved :)

---

### Post by wilee-nilee on 2010-12-07
Anybody notice that sda3 looks like boot partition? no flag but look at the script.

---

### Post by coffeecat on 2010-12-07
> **wilee-nilee said:**
> Anybody notice that sda3 looks like boot partition? no flag but look at the script.

I think you're right, but Linux doesn't need a boot flag. The OP says this in their first post:

> **Ajay Ramaseshan said:**
> and 477 Mb BOot Partition for Linux also primary partition

Which, being a primary partition, didn't help their original problem. Personally, I leave Windows and any recovery partition on their primaries and put everything else in logicals in one extended (for sda). I never bother with a boot partition either.

This four primary maximum in a mbr partition table is a never-ending source of confusion for inexperienced people. And some manufacturers' habit (*cough* HP *cough*) of producing Windows 7 machines with 4 primary partitions just makes it worse. The sooner the industry goes over to EFI with GPT partition tables the better.

OT-diatribe over. :wink:

---

### Post by julio_cortez on 2010-12-07
> **coffeecat said:**
> *cough* HP *cough*Well, to say it all (at least, regarding the case we're discussing here) it's Microsoft that is to "blame" for this. That 100MB primary partition that gets created automatically at the beginning of the disk when you install W7, meh.. Could be avoided in my opinion.

I know not everyone has the skills or the confidence to enter the manual partitioner while installing W7 and configure the disk so that partition doesn't get created, but it could (and, in my opinion, should) have been made optional as the recovery environment and bitlocker (when available) can easily be installed in the "main" W7 partition..

**I forgot (but it's VERY important):** Seeing that the 100MB partition is already there, in this case, i would NOT try to delete it as the recovery environment would be probably gone (*and yes, often it works and saved me from reinstalling a couple of times*) ;)

---

### Post by coffeecat on 2010-12-07
> **julio_cortez said:**
> I know not everyone has the skills or the confidence to enter the manual partitioner while installing W7 and configure the disk so that partition doesn't get created, but it could (and, in my opinion, should) have been made optional as the recovery environment and bitlocker (when available) can easily be installed in the "main" W7 partition..

Indeed. When I installed W7 to my main machine I created one NTFS partition for it with Gparted and installed it to that and that alone. And it seems happy enough. But you're right that many would not be confident enough to be able to do this. But the problem is OEM installs, not so much Microsoft. My dig at HP (I have no direct experience of HP) was because threads about their laptops come up with depressing regularity. Their standard setup seems to be: partition 1 = HP recovery; partition 2 = Window 7 boot; partition 3 = Windows 7 C; partition 4 = some sort of HP utility. And if you're a beginner and unused to partitioning you're snookered. Some other manufacturers content themselves with just three primary partitions.

Anyway, I think we're going OT. :wink:

---

