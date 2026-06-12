---
title: "ANOTHER Sound Problem with Ubuntu 10.10...Please Read"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by cynkronyze on 2011-04-26
Hi Everyone,

Hello from a absolute brand new user of the Linux desktop O.S. After a hair tearing incident with my Windows XP, i decided i am going in for a better OS. I did a quick check as to which Distribution will work best for the absolute noob (in todays lingo !!!) with this OS and the results tilted towards Ubuntu. After 2 attempts, the OS was installed although i have a few problems. 

Please help me out, My experience so far has been pretty great so far with this OS and I DO NOT WANT TO GO BACK TO WINDOWS.

Please help

Problem # 1
-----------

When i startup my computer, it brings me to a page to choose the OS, there are a couple of choices, i choose one, it brings me to a command prompt, saying failed to locate some file, waited for root device, cannot find root device..something like that, to which, i type in CD ROOT, it then goes the Root Directory, I have to wait for a good 5 minutes before i type in EXIT and then the OS loads just fine. I am sure that there is something wrong, and the OS should directly load into the Desktop.

Problem # 2
-----------

NO Sound !!!, as simple as that. I have the M-Audio 2496 Delta card, I have followed most of the forums regarding this problem and am aware that there are dedicated threads to this problem, I have followed the steps in that thread, but still no cigar.

this is one of the threads i followed : -

[http://ubuntuforums.org/showthread.php?t=1540891&highlight=M-Audio+Delta+Audiophile+2496+setup]("http://ubuntuforums.org/showthread.php?t=1540891&highlight=M-Audio+Delta+Audiophile+2496+setup")

I just cant figure out what to do next. I will be really grateful if someone could help me figure out what to do.

I repeat, Please Help !!!

In Desperation

Cynkronyze

---

### Post by cynkronyze on 2011-04-26
This is what i get when i type in aplay -l : - 


**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
so I understand that my card is being recognized.
-------------------------------------------------------------------
I have disabled my onboard Sound from the BIOS

---

### Post by cynkronyze on 2011-04-26
Hi all,

When I type this in the command prompt terminal : -

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

I finally get the link 

[http://www.alsa-project.org/db/?f=5751cea9008f1e38aed7e1c4c1ba8d14506841d6]("http://www.alsa-project.org/db/?f=5751cea9008f1e38aed7e1c4c1ba8d14506841d6")

- Cynkronyze

---

### Post by Hedgehog1 on 2011-04-26
> **cynkronyze said:**
> 

Problem # 1
-----------

When i startup my computer, it brings me to a page to choose the OS, there are a couple of choices, i choose one, it brings me to a command prompt, saying failed to locate some file, waited for root device, cannot find root device..something like that, to which, i type in CD ROOT, it then goes the Root Directory, I have to wait for a good 5 minutes before i type in EXIT and then the OS loads just fine. I am sure that there is something wrong, and the OS should directly load into the Desktop.

In Desperation

Cynkronyze

Lets try and solve the booting issue first. Please boot into Ubuntu (if you are not already there when reading thi post) and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by cynkronyze on 2011-04-26
Hi Hedgehog,

Thanks for the reply..

OK so i did exactly what you told me to and this is what i get :- 


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

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

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   149,843,967   149,841,920  83 Linux
/dev/sda2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sda5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   107,619,783   107,619,721   7 HPFS/NTFS
/dev/sdb2         107,620,350   488,375,999   380,755,650   f W95 Ext d (LBA)
/dev/sdb5         204,796,683   308,158,829   103,362,147   7 HPFS/NTFS
/dev/sdb6         308,158,893   406,460,564    98,301,672   7 HPFS/NTFS
/dev/sdb7         406,460,628   488,375,999    81,915,372   7 HPFS/NTFS
/dev/sdb8         107,620,352   200,726,527    93,106,176  83 Linux
/dev/sdb9         200,728,576   204,795,903     4,067,328  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        75aaa572-909b-4aff-9bb3-cf25e193b117   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a6500be4-d1d7-4381-a277-76056af1a7c0   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F0F00443F0041290                       ntfs       Music                         
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        64DC4E97DC4E6400                       ntfs       Downloads                     
/dev/sdb6        5EB09836B098171D                       ntfs       Studio                        
/dev/sdb7        FE98A61C98A5D385                       ntfs       Pix                           
/dev/sdb8        40ebcbae-ee35-40b7-b723-030826aff2c8   ext4                                     
/dev/sdb9        4fc9dfe5-05ca-4866-88e9-9d7bfc39d019   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 75aaa572-909b-4aff-9bb3-cf25e193b117
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 75aaa572-909b-4aff-9bb3-cf25e193b117
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 75aaa572-909b-4aff-9bb3-cf25e193b117
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=75aaa572-909b-4aff-9bb3-cf25e193b117 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 75aaa572-909b-4aff-9bb3-cf25e193b117
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=75aaa572-909b-4aff-9bb3-cf25e193b117 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 75aaa572-909b-4aff-9bb3-cf25e193b117
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=75aaa572-909b-4aff-9bb3-cf25e193b117 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 75aaa572-909b-4aff-9bb3-cf25e193b117
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=75aaa572-909b-4aff-9bb3-cf25e193b117 ro single 
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
    search --no-floppy --fs-uuid --set 75aaa572-909b-4aff-9bb3-cf25e193b117
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 75aaa572-909b-4aff-9bb3-cf25e193b117
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=75aaa572-909b-4aff-9bb3-cf25e193b117 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  55.9GB: boot/grub/core.img
  30.3GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
    .8GB: boot/initrd.img-2.6.35-28-generic
  55.9GB: boot/vmlinuz-2.6.35-22-generic
  55.9GB: boot/vmlinuz-2.6.35-28-generic
    .8GB: initrd.img
    .8GB: initrd.img.old
  55.9GB: vmlinuz
  55.9GB: vmlinuz.old

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=40ebcbae-ee35-40b7-b723-030826aff2c8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=4fc9dfe5-05ca-4866-88e9-9d7bfc39d019 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader  on sdb2

00000000  b0 89 07 29 8c 93 b0 86  a7 32 41 09 c6 69 d7 29  |...).....2A..i.)|
00000010  a2 23 03 15 2b 44 64 b3  2c 26 78 52 98 47 a1 e7  |.#..+Dd.,&xR.G..|
00000020  4c 38 e7 b2 92 c7 a4 72  57 77 84 75 69 9c 19 0c  |L8.....rWw.ui...|
00000030  96 75 db c3 ce 5b 73 4b  af 7d 0f 3f 0c b4 db 0e  |.u...[sK.}.?....|
00000040  56 9c e5 88 85 81 56 c9  d8 f5 0c c5 e7 82 9d 24  |V.....V........$|
00000050  1a b4 e0 bc 70 64 5a 71  15 7c ed 98 66 d5 a1 a1  |....pdZq.|..f...|
00000060  cb ff 09 ff b1 cf 02 9d  fc 7f 36 fa 23 11 a1 3a  |..........6.#..:|
00000070  78 33 19 cc 02 d8 a4 79  6c e3 67 f9 69 d7 a9 a7  |x3.....yl.g.i...|
00000080  22 06 26 4d 73 a7 0c e3  98 3e 9a de 0c 8c 9f 60  |".&Ms....>.....`|
00000090  f0 8b 93 65 ca 17 e9 c9  5c 8c b9 4f a2 6c 63 05  |...e....\..O.lc.|
000000a0  cf be fb d0 54 cc db c3  87 ce 08 f2 28 d1 c2 6f  |....T.......(..o|
000000b0  b1 d1 a7 71 b1 40 a1 4d  cd 3e 8b 0a ee 12 d6 9b  |...q.@.M.>......|
000000c0  11 c1 92 5a 83 04 60 7c  7f fe d3 f6 b4 b0 32 0d  |...Z..`|......2.|
000000d0  49 0e e8 84 65 55 11 17  8c 76 96 98 83 00 51 5c  |I...eU...v....Q\|
000000e0  51 6e 71 e7 b0 ae 51 70  9c e2 55 73 ba a3 8b 99  |Qnq...Qp..Us....|
000000f0  51 0d ce 7d 5f 1b 78 64  93 73 eb 96 78 e7 49 b2  |Q..}_.xd.s..x.I.|
00000100  b8 74 75 8e 3c 67 fb 6a  9f b8 77 31 42 4d 43 a3  |.tu.<g.j..w1BMC.|
00000110  1f b7 3b 8a 5f 80 c4 eb  9c 1b fd f3 04 5c dd a7  |..;._........\..|
00000120  8c 24 ea 41 8d 86 77 f1  3e b2 18 21 aa fa fc 86  |.$.A..w.>..!....|
00000130  58 e9 f5 67 fd d3 13 3a  7d 24 e1 93 06 84 2b bc  |X..g...:}$....+.|
00000140  b4 ed 21 af 72 3c 74 34  6c f1 32 1e e3 c3 3a c7  |..!.r<t4l.2...:.|
00000150  9b 31 5e f0 a3 d9 3f c1  d9 28 7e e3 c6 5f 72 8f  |.1^...?..(~.._r.|
00000160  ce 8b ae 19 0a ff 3a 49  d3 93 4c b0 42 14 bf d7  |......:I..L.B...|
00000170  30 ca 67 69 32 8d 87 48  84 7b 68 89 eb 4d 01 f0  |0.gi2..H.{h..M..|
00000180  2f 83 ff 2a 1d 01 7d 03  7e 24 fb 46 a5 f4 bd fc  |/..*..}.~$.F....|
00000190  89 b7 b8 2c c4 62 72 39  76 90 e8 ad 88 6c 88 b6  |...,.br9v....l..|
000001a0  d2 32 15 d4 98 eb ed 23  72 74 d6 68 31 2f 81 88  |.2.....#rt.h1/..|
000001b0  56 7b 9b c3 27 d9 68 f1  f6 2c f3 79 f7 da 00 01  |V{..'.h..,.y....|
000001c0  c1 ff 07 fe ff ff 0d cb  ca 05 63 2e 29 06 00 fe  |..........c.)...|
000001d0  ff ff 05 fe ff ff 70 f9  f3 0b 27 f7 db 05 00 00  |......p...'.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

