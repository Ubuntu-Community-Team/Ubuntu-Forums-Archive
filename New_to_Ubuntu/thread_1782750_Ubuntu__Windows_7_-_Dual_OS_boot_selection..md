---
title: "Ubuntu / Windows 7 - Dual OS boot selection."
date: 2011-06-15
forum: New to Ubuntu
---

### Post by daniel-fairhaven on 2011-06-15
Newbie with Ubuntu 11.04 (from PCWorld.co.nz). Ubuntu is installed on D:\ (hdb), Windows 7 on C:\ (hda).

How can I change between OS during boot, all I get is Windows (D:\ no longer in Explorer), I cannot change using Boot Options (just offers HardDisk or CdDvdDrive).

Any Ideas or help please.

---

### Post by sanderd17 on 2011-06-15
How did you install it? With WUBI (inside Windows) or as a dual boot (next to windows)?

If you don't know, please follow this steps and post the result: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by nirab on 2011-06-15
here is a link that might help 

[http://www.ubuntugeek.com/step-by-step-guide-installing-ubuntu-11-04-natty-on-a-windows-7-dual-booting.html](http://www.ubuntugeek.com/step-by-step-guide-installing-ubuntu-11-04-natty-on-a-windows-7-dual-booting.html)

maybe you went wrong during one of the steps

---

### Post by daniel-fairhaven on 2011-06-15
My installation process as follows.
____________________

Burned ISO onto CDR.
Booted to CD Drive.
Pressed ESC during boot and loaded to DEMO.
Installed from DEMO;
     Language > Download Updates/Third Party; both not ticked
     Allocate Drive Space; something else
     New Partition > [D:\] > sub parts set to 'ext4' 2-4gb; no size issues
     My Country
     US Keyboard
     My Details
Rebooted after successful Install; removing CD.
____________________

After reboot went to Windows; no D:\ listed
Successive restarts go to Windows. Boot order doesn't include D:\



Hope that helps.

---

### Post by shibu_sawyer on 2011-06-15
i think something went wrong in partition,cos u have to allocate a swap space.. better you install ubuntu inside the windows.
format the partition D: using windows., insert the ubuntu cd into the  drive.select install inside windows and give a user name and password thats all ,cd ejects automatically,you reboot the s/m. A screen shows dual os(win/ubuntu),select ubuntu thats it.

---

### Post by mastablasta on 2011-06-15
> **shibu_sawyer said:**
> i think something went wrong in partition,cos u have to allocate a swap space.. better you install ubuntu inside the windows.
format the partition D: using windows., insert the ubuntu cd into the drive.select install inside windows and give a user name and password thats all ,cd ejects automatically,you reboot the s/m. A screen shows dual os(win/ubuntu),select ubuntu thats it.
 
 
actually you can do it without swap partition it's just risky.
 
And no this is not the problem.
 
@daniel-fairhaven please use the bootinfo script. the link to it was provided by sanderd17
 
it might be that you didn't install the boot manager on the right disk. but it's hard to say wihtout knowing exaclty what happens on boot and how partitions are flagged. script will tell this. follow the instructions provided on it's wesbite.
 
solution might be close but it's hard to say if we don't know the exact system configuration of boot.
 
your D:\ is not listed in windows because it has a file system that windows doesn't recognise unless you use special tools.

---

### Post by daniel-fairhaven on 2011-06-15
Ok, managed to get the CD Demo up and ran the script.

```
_________________________
_________________________

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.
 => Windows is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.

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
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

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

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   624,928,767   624,519,168   7 NTFS / exFAT / HPFS
/dev/sda3         624,928,768   625,140,399       211,632   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     3,905,535     3,903,488  83 Linux
/dev/sdb2           3,907,582   595,699,711   591,792,130   5 Extended
/dev/sdb5           3,907,584     7,811,071     3,903,488  83 Linux
/dev/sdb6           7,813,120    11,716,607     3,903,488  83 Linux
/dev/sdb7          11,718,656    19,529,727     7,811,072  83 Linux
/dev/sdb8          19,531,776    23,435,263     3,903,488  83 Linux
/dev/sdb9          23,437,312    27,340,799     3,903,488  83 Linux
/dev/sdb10         27,342,848    31,246,335     3,903,488  83 Linux
/dev/sdb11         31,248,384    39,059,455     7,811,072  83 Linux
/dev/sdb12         39,061,504    58,591,231    19,529,728  82 Linux swap / Solaris
/dev/sdb13         58,593,280   595,699,711   537,106,432  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,953,519,615 1,953,517,568   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               8,192    15,523,839    15,515,648   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B0C20CCCC20C98AC                       ntfs       SYSTEM
/dev/sda2        92A0DE91A0DE7AE5                       ntfs       Layer 01
/dev/sda3        846B-6E0E                              vfat       HP_TOOLS
/dev/sdb1        2055132b-e43d-43b2-a467-8988da9ff44a   ext4       
/dev/sdb10       07a260ab-0eca-430b-968f-758864aefa4d   ext4       
/dev/sdb11       76019983-3288-48d1-bf06-63635a96552b   ext4       
/dev/sdb12       2a856549-d59b-4839-ac42-132e3d60c4b8   swap       
/dev/sdb13       6ace193d-0332-4a3e-a21a-26caa3f4cd41   ext4       
/dev/sdb5        cec9e86c-0179-4466-8236-8337ec39e28d   ext4       
/dev/sdb6        7b5e5bf0-8df0-4ef7-aa16-7fa1e52737b5   ext4       
/dev/sdb7        ee7d6faa-6bcb-4e47-9278-2f976254e5aa   ext4       
/dev/sdb8        c6a967a0-7ec4-4637-aaf0-628a58aa1068   ext4       
/dev/sdb9        628254ad-c459-4ea2-81c0-a0abc7f90632   ext4       
/dev/sdc1        4C704FF7704FE5F4                       ntfs       Unknown Layer
/dev/sdd1        3866-3865                              vfat       PIP BOY

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/Unknown Layer     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sdb1/grub/grub.cfg: ==============================

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
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root ee7d6faa-6bcb-4e47-9278-2f976254e5aa
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 2055132b-e43d-43b2-a467-8988da9ff44a
set locale_dir=($root)/grub/locale
set lang=en_NZ
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 2055132b-e43d-43b2-a467-8988da9ff44a
	linux	/vmlinuz-2.6.38-8-generic root=UUID=6ace193d-0332-4a3e-a21a-26caa3f4cd41 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 2055132b-e43d-43b2-a467-8988da9ff44a
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/vmlinuz-2.6.38-8-generic root=UUID=6ace193d-0332-4a3e-a21a-26caa3f4cd41 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 2055132b-e43d-43b2-a467-8988da9ff44a
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 2055132b-e43d-43b2-a467-8988da9ff44a
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root B0C20CCCC20C98AC
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 92A0DE91A0DE7AE5
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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.152404785 = 0.163643392    grub/core.img                                  1
   0.153327942 = 0.164634624    grub/grub.cfg                                  1
   0.169166565 = 0.181641216    initrd.img-2.6.38-8-generic                    1
   0.133743286 = 0.143605760    vmlinuz-2.6.38-8-generic                       1

=============================== sdb13/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb13 during installation
UUID=6ace193d-0332-4a3e-a21a-26caa3f4cd41 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=2055132b-e43d-43b2-a467-8988da9ff44a /boot           ext4    defaults        0       2
# /home was on /dev/sdb5 during installation
UUID=cec9e86c-0179-4466-8236-8337ec39e28d /home           ext4    defaults        0       2
# /opt was on /dev/sdb10 during installation
UUID=07a260ab-0eca-430b-968f-758864aefa4d /opt            ext4    defaults        0       2
# /srv was on /dev/sdb9 during installation
UUID=628254ad-c459-4ea2-81c0-a0abc7f90632 /srv            ext4    defaults        0       2
# /tmp was on /dev/sdb6 during installation
UUID=7b5e5bf0-8df0-4ef7-aa16-7fa1e52737b5 /tmp            ext4    defaults        0       2
# /usr was on /dev/sdb7 during installation
UUID=ee7d6faa-6bcb-4e47-9278-2f976254e5aa /usr            ext4    defaults        0       2
# /usr/local was on /dev/sdb11 during installation
UUID=76019983-3288-48d1-bf06-63635a96552b /usr/local      ext4    defaults        0       2
# /var was on /dev/sdb8 during installation
UUID=c6a967a0-7ec4-4637-aaf0-628a58aa1068 /var            ext4    defaults        0       2
# swap was on /dev/sdb12 during installation
UUID=2a856549-d59b-4839-ac42-132e3d60c4b8 none            swap    sw              0       0
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 ca 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 3f 25  |........?.....?%|
00000020  b0 3a 03 00 1b 03 00 00  00 00 00 00 02 00 00 00  |.:..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 0e 6e 6b 84 4e  4f 20 4e 41 4d 45 20 20  |..).nk.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

_________________________
_________________________

```
Thats what I got.

<< Edit: 'sdc' & 'sdd' are my External HD and Cellphone >>

---

### Post by sanderd17 on 2011-06-15
First, post the output between CODE tags (click on the # in the editor) this will make the output more readable.

As far as I see, it should work if you install GRUB to /dev/sda.

Follow point 13 in this thread: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Your root directory (noted with /dev/sdXY in the tutorial) should be /dev/sdb1 and the device where you install it (noted with /dev/sdX in the tutorial) should be /dev/sda.

---

### Post by Mark Phelps on 2011-06-15
You need to know that if you make a mistake and accidentally install GRUB to the Win7 boot partition, that is likely to render Win7 unbootable.

Safest course is to do the following:
1) Disconnect the Win7 drive
2) Boot using an Ubuntu CD and reinstall GRUB
3) Reconnect the Win7 drive -- but continue to boot from the Ubuntu drive
4) Open a terminal in Ubuntu and enter "sudo update-grub".  This will regenerate the GRUB menu and add an entry for Win7.

When you reboot, you should be seeing a GRUB menu.

---

### Post by oldfred on 2011-06-15
Have you tried booting from sdb? You can change BIOS or use one time boot key (f12 on my system).

When dual booting & BIOS lets you select boot drive, I prefer to keep the windows boot loader on the sda drive where windows is installed and the grub2 boot loader on sdb where Ubuntu is installed. That way each hard drive could boot on its own if you have troubles with the other.

---

### Post by daniel-fairhaven on 2011-06-15
Yeah, thanks Mark. I did what Sandred suggest a while ago (before your post) now I boot straight to ' grub> '.
 
I have no idea what to do know. Before this happened I booted from CD, ran terminal and followed the instructions to reinstall grub to my windows drive, sda, as suggested above.
 
I can pause startup showing options for bios, boot options etc... boot options being, HD, CD/DVD, and any usb devices i have (modem, fone etc).
 
*puppy dog eyes*
help

---

### Post by daniel-fairhaven on 2011-06-15
Bump.
 
... please.

---

### Post by oldfred on 2011-06-16
sanderd17 link to the instructions by drs305 should work to reinstall grub2's boot loader to sdb. You did include the extra line for mount /boot as you have a separate /boot and / (root) and the updated instructions for Natty's version of grub2?

sudo mount /dev/sdb13 /mnt
sudo mount /dev/sdb1 /mnt/boot

#If grub 1.99 with Natty uses boot not root-directory
sudo grub-install --boot-directory=/mnt/ /dev/sdb

---

### Post by daniel-fairhaven on 2011-06-16
No I didn't. Just...
 
"sudo mount /dev/sdXY /mnt"
"sudo grub-install --root-directory=/mnt /dev/sdX"
"sudo umount /mnt"
 
I stuck at grub prompt, can't get it to load to Windows/Ubuntu or cmd.
Is there a way to remove grub from where I installed it and put it in /boot using grubprompt?

---

### Post by oldfred on 2011-06-16
There are different parts of grub. The program is mostly in /boot. But the boot loader is in the MBR and then it uses part of the space right after the MBR for additional code.

You should just be able to rerun the install commands to update the grub2 boot loader in the MBR. It just needs to know where the rest of grub is (in /boot) and which partition is / (root). 

Most desktops have /boot in the / partition as it simplifies things. But servers, RAID, LVM & some very old systems need a separate /boot. I assume this is a server with virtually every system folder in a separate partition. Most severs only break out a few partitions as the one's that may need more space or control depending on  use - file, database, mail, web etc.

---

### Post by daniel-fairhaven on 2011-06-16
Computer is not a server, HP Notebook running Win7 Home Edition.
 
Instructions I followed told me to partition and allocate file space for /boot, /usr, /var, swapspace... etc and allocate the rest to root ( / ). All this is on a seperate HD from my windows one.
 
Please keep in mind I am a n00b with this and also stuck in grubprompt.

---

### Post by wildmanne39 on 2011-06-16
> **daniel-fairhaven said:**
> Computer is not a server, HP Notebook running Win7 Home Edition.
 
Instructions I followed told me to partition and allocate file space for /boot, /usr, /var, swapspace... etc and allocate the rest to root ( / ). All this is on a seperate HD from my windows one.
 
Please keep in mind I am a n00b with this and also stuck in grubprompt.
Hi, have you actually tried to get into the boot setup when you turn your computer on because your boot script shows the grub is on your sdb drive, it could just be a matter of selecting your sdb at start up the key well be like escape or f8 something like that, just look at what the screen says is your boot menu. If you have alread tried that I missed that I am sorry it is late and I just found your post I have not read every comment from all users.

---

### Post by sanderd17 on 2011-06-16
> **daniel-fairhaven said:**
> Computer is not a server, HP Notebook running Win7 Home Edition.
 
Instructions I followed told me to partition and allocate file space for /boot, /usr, /var, swapspace... etc and allocate the rest to root ( / ). All this is on a seperate HD from my windows one.
 
Please keep in mind I am a n00b with this and also stuck in grubprompt.

Those instructions sound like instructions for setting up a server. Normally you only need a root partition, or if you want to separate your personal data from your OS, you can also create a /home partition.

Would you mind reinstalling with less partitions? I didn't expect that you had a separate /boot. This changes the partitions you have to use in the grub-install command.

---

### Post by oldfred on 2011-06-16
A couple of installs with screen shots. If not exactly same version screens may vary slightly but process is the same.

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

My standard suggestion as a starting point:
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by daniel-fairhaven on 2011-06-16
Thank you all for the recent help, it helps to know that the install I did was for a server... when this gets fixed I'll seperate as mentioned, /root, /swap, and /home.
 
However, I am stuck at the grubprompt screen and don't know how to continue to the gui, boot from cd or go to windows.
 
My bios boot order has; Internal Hard Drive, CD/DVD Drive, and any USB connected to the computer. Changing the order just sends me to grubprompt, nothing else.
 
Also this is a Notebook, I can't disconnect a drive to force the install off of the other, I seem to remember someone mentioning that.
 
Thanking you in advance. :)

---

### Post by sanderd17 on 2011-06-16
And why don't you do a normal desktop install?

A server installation on a notebook makes no sense at all. A fresh desktop installation will probably solve the problems, and if they aren't solved immediately, it will avoid further problems.

---

### Post by daniel-fairhaven on 2011-06-16
Gov, I didn't know the difference at the time, this is in the Absolute Beginner forum. I can't force boot to CD/DVD from bios, I need info regarding grubprompt and how to proceed from there to the gui then i can hopfully rerun the install from the disk and rearrange the partions correctly. Or grub instructions to uninstall the sudo commands I ran from post #14.

---

### Post by wildmanne39 on 2011-06-16
> **daniel-fairhaven said:**
> Gov, I didn't know the difference at the time, this is in the Absolute Beginner forum. I can't force boot to CD/DVD from bios, I need info regarding grubprompt and how to proceed from there to the gui then i can hopfully rerun the install from the disk and rearrange the partions correctly. Or grub instructions to uninstall the sudo commands I ran from post #14.
Hi, why can you not go into bios or the boot menu when you first turn on your system and choose to boot from cd rom? If you watch when you first turn on your system it will say what key to push to enter bios so you can change your boot order to boot cd first, and you will also see a boot menu and it will tell you what key to hit to enter boot menu then choose cd, the difference in the two is that the last one just boots cd first that one time and the first one changes it to boot cd first every time.

---

### Post by daniel-fairhaven on 2011-06-16
I don't know why I can't boot to the cd. I can go into bios, I can change the boot order but it still boots to grubprompt no matter the order.

---

### Post by westie457 on 2011-06-16
Hi referring to sanderd17 earlier post suggesting you look at point 13 of this link
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")
did you take a look at point 15?

This should help you through the grub prompt.

For more guidance take a look at this link
[http://www.supergrubdisk.org/super-grub2-disk/]("http://www.supergrubdisk.org/super-grub2-disk/")

Hope this helps

---

### Post by daniel-fairhaven on 2011-06-16
OK, I have access to the GUI and Terminal by following the #15 point on the Basics post.

Has this solved my issues with dual boot options? Will this mean I boot straight to the Ubuntu desktop instead of the Grub Prompt? or give me the options of Win 7 & Ubuntu?

Do I need to reinstall Ubuntu reallocating space for just /root, /home, and /swap?
Grub is on my windows hd should it be removed?

---

### Post by wildmanne39 on 2011-06-16
> **daniel-fairhaven said:**
> OK, I have access to the GUI and Terminal by following the #15 point on the Basics post.

Has this solved my issues with dual boot options? Will this mean I boot straight to the Ubuntu desktop instead of the Grub Prompt? or give me the options of Win 7 & Ubuntu?

Do I need to reinstall Ubuntu reallocating space for just /root, /home, and /swap?
Grub is on my windows hd should it be removed?
Hi, yes they said you should reinstall ubuntu, and yes you want to put grub on the second drive, I will give you a link for installing to second drive. Also create the partitions as you mentioned.
 [http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by daniel-fairhaven on 2011-06-17
Had to restart the computer, came up with grub again. Went through all the same stuff as before to get to the desktop again... however now it comes up with;
 
(initramfs)
Could not find the ISO /<name.iso>
blah blah, reload to windows and chkdsk (which i can't)
 
I had a look (ls) at the prompt but permissions prevent me going far.
 
Any ideas? All the installation info was the same as before when it worked... but now *shrug*

---

### Post by daniel-fairhaven on 2011-06-17
Bump...

---

### Post by westie457 on 2011-06-18
> sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

[SIZE="4"][SIZE="3"][/SIZE][/SIZE][SIZE="2"][/SIZE]Hello, it looks to me that you installed inside Windows and somehow it got screwed up.

Can you boot into Windows?

If so go into Control Panel > Programs and Features. Check in the list if Ubuntu is there un-install it.
Then put the CD in the Drive, close any window that opens.

Reboot into the CD not (pressing any keys) wait until you get the install options window.

Select install

Choose location
Select keyboard

At the partitioning screen select something else to choose where you want the install to go.

The partitioning screens will guide you through the steps and when all is ready will give a final warning about changes will be written to disk. 

Click on Install/Continue

That should have you up and running.


On the other hand. If nothing is listed under Programs and Features and is not listed in your Start Menu come back and we will try something different.

Good luck

---

### Post by sanderd17 on 2011-06-18
> **daniel-fairhaven said:**
> Bump...

Come on, your installation is completely screwed up (even before you asked it here). You have some Wubi installation and a disk that has 13 partitions.

Just reinstall the desktop edition (biggest partition for /home, 12 GB for root (/) and about 2 GB for swap), this should also discover your windows installation. If it doesn't discover your windows installation, then you can do what I suggested in the first page.

---

### Post by oldfred on 2011-06-18
We often spend days here helping users, but sometimes reinstall is just the better choice. Especially if you do not have data or configurations to recover or have good backups. Most can reinstall in about an hour depending on computer and Internet speeds.

I have partitioned in advance and not included updates. With install from USB flash drive on a 3 year old system it took 9 minutes for a basic install. But downloading updates & some reconfiguration, still ended up about an hour to a working system.

---

### Post by daniel-fairhaven on 2011-06-18
Yes, thank you for that. I know the install is messed up, that I've too many partitions. How ever I can't boot to CD (even by changing boot order), I can't boot to windows... It just goes to GrubPrompt. When I follow the help for Grub the process dumps me at Initramfs.

---

### Post by westie457 on 2011-06-18
Hello again, do you have a Windows 7 Install DVD? If yes stick that in the DVD-drive and re-boot. You should get a line of text on screen saying "Press any key to boot from CD/DVD"

The Windows DVD overrides any settings that you have in your BIOS.


In the next window select your Country and keyboard layout. Press Enter.

When the Install window appears select the option to repair your computer.

You might have to enter your Windows password as well

The next window will have several options - start-up repair, restore from an image, restore to an earlier point with System Restore, Memtest and 1 or 2 others.

Select Start-up repair, the system will then look for Windows installations. If it cannot find any that match the DVD it will stop and let you know. It should find only one ie Windows 7, click on continue and wait following any prompts that come up.

Look through the report that is displayed after. It might say at the end that the OS booted correctly. Try re-booting, if the repairs were successful then you will be in Windows. If unsuccessful you will be at the repair screen again. DO NOT PANIC.

Select the last option which is 2Open a Command-Prompt"

Enter these commands 1 at a time -ignoring the quote marks-pressing enter after each

            "bootrec /fixmbr"
            "bootrec /fixboot"
            "bootrec /rebuildbcd"

Type in exit or quit then Reboot.

You will now have a working system without any Grub prompt and you will be free to do a clean install of Ubuntu.

Have a good time wherever you are.


PS  Apologies for putting a long post about Windows on here, it was necessary to help a fellow Ubuntuer.
I know this works because I had to do it earlier when I stuffed up my spare box. You may laugh if you wish.

---

