---
title: "Not able to boot into Windows"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by 1ktmeadows on 2011-08-14
Im new to Ubuntu to i have been playing around with ubuntu 11.04 for a week and I like it alot but when I try to boot into Windows 7 my computer will start to display to windows symbol and then it goes back to selection of ubuntu or windows. I tried it different times but my computer wont boot into windows. When I installed ubuntu, I set it to where it can dual boot.

---

### Post by n@ughty on 2011-08-14
Try login into ubuntu and type

sudo update-grub

and reboot

---

### Post by 1ktmeadows on 2011-08-14
I typed what you gave me  and then I shutdown. Then I tried to boot windows and it did the same thing again. It will start to make the windows symbols and then it goes back to where I select between ubuntu or windows. These are the selections that I get:
Ubuntu, with Linux 2.6.38-10-generic
Ubuntu, with Linux 2.6.38-10-generic (recovery)
Previous Linux version
Memory test (memtest86+)
Memory test (memtest86+) serial console 115200
Windows 7 (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)
Windows Recovery Environment (loader) (on/dev/sda3)
I selected both Windows 7 (loader) (on/dev/sda1) and Windows 7 (loader) (on/dev/sda2) and it still wont boot into windows.
Thanks for responding back

---

### Post by raja.genupula on 2011-08-14
are you sure is your windows in good working condition ?

---

### Post by 1ktmeadows on 2011-08-14
I think so because before I installed ubuntu 11.04, windows was working perfectly. What can I do to fix this?

---

### Post by Mark Phelps on 2011-08-15
HOW did you install 11.04 -- did you allow the Ubuntu installer to shrink your Win7 OS to make room for Ubuntu? OR did you shrink it yourself to make room?

If you did the latter, did you use the Win7 Disk Management utility? Or did you use the Gnome Partition Editor (GParted)?

Also, try BOTH of the Windows 7 Loader entries.  GRUB sometimes gets them confused and what is listed as a recovery entry is in fact, the real entry.

---

### Post by 1ktmeadows on 2011-08-15
When installing ubuntu 11.04, I installed it alongside windows 7. I thought I installed it correctly, what can I check to see what I did wrong?
Thanks for helping

---

### Post by Mark Phelps on 2011-08-15
> **1ktmeadows said:**
> When installing ubuntu 11.04, I installed it alongside windows 7. I thought I installed it correctly, what can I check to see what I did wrong?
Thanks for helping

We need to know HOW you installed Ubuntu -- which is why I asked the questions -- because the answers depend on the details.

OK, so open a terminal in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one). Post the results back here.  That will list out the partitions on your hard drive and will give us a clue regarding how Ubuntu is installed.

As to what you did "wrong", we can't tell until we at least see the results of that command.

---

### Post by 1ktmeadows on 2011-08-15
This is what I got:
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000   27  Unknown
/dev/sda2         3074048   360577743   178751848    7  HPFS/NTFS
/dev/sda3       604020736   625141759    10560512   17  Hidden HPFS/NTFS
/dev/sda4       360579070   604020735   121720833    5  Extended
/dev/sda5       360579072   598263807   118842368   83  Linux
/dev/sda6       598265856   604020735     2877440   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders, total 1984000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             249     1983743      991747+   6  FAT16

---

### Post by Mark Phelps on 2011-08-15
OK, so it looks like you installed Ubuntu into its own partitions.

So, HOW did you create the Ubuntu partitions? Did you shrink the Win7 partition using Win7 Disk Management and THEN create the Linux partitions manually?

Or, did you simply allow the Ubuntu installer to resize Win7 and create the partitions?

Because ... if you did the second, you are likely to have corrupted Win7 and rendered it unbootable.  This sometimes happens when you let the Ubuntu installer resize win7 partitions.

OK, so when you next try to boot, as SOON as you select Win7, start pressing the F8 key -- and keep doing that, even if the PC starts beeping.  If that works, it will boot you into SAFE mode, and from there you may be able to select Repair your Computer.

---

### Post by Triblaze on 2011-08-15
I had the same problem and my windows has not been working as a result, so I'll keep an eye on this.

If it has become unbootable, as you said, is there a way to fix it?

---

### Post by oldfred on 2011-08-15
Your windows boot flag is on sda1, which then is the standard windows active partition which has all the boot files. 

But the fdisk did not show it as NTFS?? which it just about has to be.

Run this to see if it tells more about the install.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by 1ktmeadows on 2011-08-15
I haven't tried pushing F8 yet but I did go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and here is what I got.
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048   360,577,743   357,503,696   7 NTFS / exFAT / HPFS
/dev/sda3         604,020,736   625,141,759    21,121,024  17 Hidden NTFS / HPFS
/dev/sda4         360,579,070   604,020,735   243,441,666   5 Extended
/dev/sda5         360,579,072   598,263,807   237,684,736  83 Linux
/dev/sda6         598,265,856   604,020,735     5,754,880  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders, total 1984000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                 249     1,983,743     1,983,495   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6A5A5F7A5A5F424D                       ntfs       System
/dev/sda2        3864851F6484E14C                       ntfs       TI105828W0G
/dev/sda3        581EAA991EAA6FA4                       ntfs       HDDRECOVERY
/dev/sda5        db7667f5-2b98-4a70-9ebc-96d1ecb69eb2   ext4       
/dev/sda6        937fc183-86fc-4928-9c55-b5958679520f   swap       
/dev/sdb1        3035-3066                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/3035-3066         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root db7667f5-2b98-4a70-9ebc-96d1ecb69eb2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root db7667f5-2b98-4a70-9ebc-96d1ecb69eb2
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root db7667f5-2b98-4a70-9ebc-96d1ecb69eb2
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=db7667f5-2b98-4a70-9ebc-96d1ecb69eb2 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root db7667f5-2b98-4a70-9ebc-96d1ecb69eb2
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=db7667f5-2b98-4a70-9ebc-96d1ecb69eb2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root db7667f5-2b98-4a70-9ebc-96d1ecb69eb2
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=db7667f5-2b98-4a70-9ebc-96d1ecb69eb2 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root db7667f5-2b98-4a70-9ebc-96d1ecb69eb2
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=db7667f5-2b98-4a70-9ebc-96d1ecb69eb2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root db7667f5-2b98-4a70-9ebc-96d1ecb69eb2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root db7667f5-2b98-4a70-9ebc-96d1ecb69eb2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6A5A5F7A5A5F424D
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 3864851F6484E14C
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 581EAA991EAA6FA4
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
# / was on /dev/sda5 during installation
UUID=db7667f5-2b98-4a70-9ebc-96d1ecb69eb2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=937fc183-86fc-4928-9c55-b5958679520f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 278.071533203 = 298.577035264  boot/grub/core.img                             1
 260.334445953 = 279.531982848  boot/grub/grub.cfg                             1
 179.242187500 = 192.459833344  boot/initrd.img-2.6.38-10-generic              2
 178.699115753 = 191.876714496  boot/initrd.img-2.6.38-8-generic               2
 178.238590240 = 191.382228992  boot/vmlinuz-2.6.38-10-generic                 1
 278.069805145 = 298.575179776  boot/vmlinuz-2.6.38-8-generic                  1
 179.242187500 = 192.459833344  initrd.img                                     2
 178.699115753 = 191.876714496  initrd.img.old                                 2
 178.238590240 = 191.382228992  vmlinuz                                        1
 278.069805145 = 298.575179776  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  0f 20 e7 d7 b5 76 23 86  f4 77 1c 7e 7c 5c 8f c5  |. ...v#..w.~|\..|
00000010  a6 7d 3d 9d 7d 3d dd ec  72 8f 4a 23 86 c8 94 5e  |.}=.}=..r.J#...^|
00000020  3c 05 29 fe 49 c0 e6 e1  e3 7b 18 a3 4c 34 ec f3  |<.).I....{..L4..|
00000030  f3 7c f7 b5 ac 9f 90 fa  1a 6e 43 d3 38 e4 7e b9  |.|.......nC.8.~.|
00000040  b5 d9 6f 24 a4 60 81 50  e5 5b 3f ad 62 c7 12 58  |..o$.`.P.[?.b..X|
00000050  80 9b cd 9b 2c 05 6e 6f  7e fc f0 11 49 4b bd 98  |....,.no~...IK..|
00000060  23 86 fd 95 60 9d 80 3a  31 75 1d f0 73 1d 2d 49  |#...`..:1u..s.-I|
00000070  47 52 ee 5b 0b fe 4f b8  0d 0f 09 3a 3e 9f 75 fe  |GR.[..O....:>.u.|
00000080  ff 44 4a c0 2e 45 5a 4d  c7 ad f3 0a 77 c0 d5 35  |.DJ..EZM....w..5|
00000090  18 f9 c7 05 a8 77 9e eb  07 bc 4e cd e7 ba f8 18  |.....w....N.....|
000000a0  b2 2c 02 55 31 f2 fb bf  28 ac 9d f5 fe 93 d9 f5  |.,.U1...(.......|
000000b0  de c0 64 1a 18 a7 3c ac  c9 66 fd ba df 44 2e bd  |..d...<..f...D..|
000000c0  c9 54 e3 ef 55 73 fb 83  35 68 ef ef de f0 70 fd  |.T..Us..5h....p.|
000000d0  af 04 f0 4f f4 c2 73 65  63 e7 77 35 b8 59 31 31  |...O..sec.w5.Y11|
000000e0  e9 6e b2 f4 fb 32 99 ee  86 e3 bd b2 b2 82 fe 49  |.n...2.........I|
000000f0  f0 be 32 f8 b1 92 f5 1f  e9 e8 3d 2e 02 b1 77 ab  |..2.......=...w.|
00000100  66 d0 ae 02 48 fc 1d 64  70 71 71 eb 0d bb 9a fb  |f...H..dpqq.....|
00000110  fb 83 66 ed 9c fd 06 9c  3e 90 4b 66 94 1f ca ff  |..f.....>.Kf....|
00000120  70 25 1e fa 20 2e 4b 60  72 35 74 40 cd 6c cd 0e  |p%.. .K`r5t@.l..|
00000130  79 1f eb 56 4d 3f 1c 56  4a be 3d 99 f6 05 17 88  |y..VM?.VJ.=.....|
00000140  13 db 77 14 6d 86 20 44  86 2d 4f dc a8 15 47 0d  |..w.m. D.-O...G.|
00000150  67 28 97 22 ce 53 80 93  25 12 75 a3 0b 1b e5 b5  |g(.".S..%.u.....|
00000160  58 e5 52 78 8f 61 07 0f  79 1e da bc cf 4d 02 88  |X.Rx.a..y....M..|
00000170  8b ca b2 7f f1 09 09 31  77 fe d1 79 00 58 fd db  |.......1w..y.X..|
00000180  ec 82 d2 d0 d2 ce 4d 13  e4 6e 80 92 3b 7c 91 5a  |......M..n..;|.Z|
00000190  de 31 b7 46 c4 bf 6d e1  3c e0 91 b3 f0 3f 4f ef  |.1.F..m.<....?O.|
000001a0  b3 43 c6 d8 99 f5 25 3e  af e9 c2 66 5d 4a bb a2  |.C....%>...f]J..|
000001b0  92 7b 5e 36 18 50 5c f0  30 77 6b 5e 38 aa 00 fe  |.{^6.P\.0wk^8...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c8 2a 0e 00 fe  |............*...|
000001d0  ff ff 05 fe ff ff 02 c8  2a 0e 00 d8 57 00 00 00  |........*...W...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by 1ktmeadows on 2011-08-15
I was able to get to work by pushing F8 and doing a Repair. I want to say thank you to everyone for helping me. I really appreciate yall for helping me. 
Thank You, Thank You, alot

---

