---
title: "Dual boot 11.04"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by Starbase 9525 on 2011-08-21
I installed 11.04 on my windows xp box and ran the setup to boot alongside windows. I can now boot into 11.04 just fine but windows won't boot. XP shows up at the bottom of the bootable list but when chosen only gets to a blank screen with a flashing cursor in the upper left corner. 11.04 sees the windows partition just fine and I can access files there but windows never boots. Is there anything I can do to fix this?

---

### Post by vidtek on 2011-08-21
Starbase-

You can run grub update to see if that will allow access.

from a terminal :  sudo update-grub

This will look at the systems installed and hopefully you will be able to boot to XP.

If this doesn't work try: sudo grub-install /dev/sdX  (To identify your boot disc run this command: sudo blkid)

replace sdX with whatever boot disc you're using.  Note this is a disc, not a partition, it will replace the MBR.  This should fix it.

If this doesn't work, you will then need to boot your XP cd disc, repair the MBR so only Windows will boot, then re-install grub to gain access to Ubuntu installation by using a chroot environment - if you need help with this post again.  This is a bit of a pain, so hopefully you won't need to do it.

Best of luck, Tony.

---

### Post by Starbase 9525 on 2011-08-21
Ran these two commands and this is what I got:

forrest@forrest-T6522:/home$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP on /dev/sdb1
done
forrest@forrest-T6522:/home$ blkid
/dev/sda1: LABEL="NT3500BASIX" UUID="17F6-3766" TYPE="vfat" 
/dev/sdb1: UUID="E86063006062D53A" TYPE="ntfs" 
/dev/sdb5: UUID="0ee63447-1d0a-4367-b6e3-fbd045f465d9" TYPE="ext4" 
/dev/sdc1: SEC_TYPE="msdos" UUID="0000-2CE1" TYPE="vfat"

Does this give enough info to do what you suggested?

Thanks for your help.

---

### Post by YesWeCan on 2011-08-22
Hi there. There may be subtle problems. Would you download this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post rhe RESULTS.txt file here. Use code tags to make it easier to read: highlight and press #

---

### Post by vidtek on 2011-08-23
> **Starbase 9525 said:**
> Ran these two commands and this is what I got:

forrest@forrest-T6522:/home$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP on /dev/sdb1
done
forrest@forrest-T6522:/home$ blkid
/dev/sda1: LABEL="NT3500BASIX" UUID="17F6-3766" TYPE="vfat" 
/dev/sdb1: UUID="E86063006062D53A" TYPE="ntfs" 
/dev/sdb5: UUID="0ee63447-1d0a-4367-b6e3-fbd045f465d9" TYPE="ext4" 
/dev/sdc1: SEC_TYPE="msdos" UUID="0000-2CE1" TYPE="vfat"

Does this give enough info to do what you suggested?

Thanks for your help.

Star..
It would appear you have 3 physical discs
Linux is on sdb5
you don't appear to have a swap disc
You have an NTFS partition sharing your linux drive I would hazard a guess and say that is your XP partition.
sda1 is probably an older legacy drive and I would think that sdc1 is a thumb or usb drive?

Anyway, the drive in which we are interested is definitely sdb.

You didn't say if you are now able to boot into windows in your reply.

Yes there is enough info to do the next step if necessary.

Tony

---

### Post by campb.andrew on 2011-08-23
I have this same issue. I installed 11.04 alongside Win 7. But now when i select Win 7 during the boot screen, it only goes as far as the starting windows screen before a BSOD flashes for a second and my pc restarts. :( I think i rewrote my MBR by mistake....and just wish Ubuntu showed the disk labels like Windows did during installs. 

Anyway, how can we fix our problem?

This is what my setup now looks like. Im really puzzled:

ironhide@ironhide-HP-ProBook-4530s:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-11-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-11-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
Found Windows 7 (loader) on /dev/sda3
done

ironhide@ironhide-HP-ProBook-4530s:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x17784653

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2048      616447      307200   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          616448   546701311   273042432   42  SFS
/dev/sda4       546701312   566545061     9921875   83  Linux

---

### Post by oldfred on 2011-08-23
@starbase 9525
Did you change drive order around after installs. Windows usually is sda. If it changed to sdb, the boot.ini may be wrong or other internal settings in boot sector. Boot script will help.

@campb.andrew
Please start your own thread, your issues are a lot different and you also have SFS or dynamic partitions from Windows. I have seen users not even be able to repair their dynamic partitions with windows tools, best to convert back to basic but not easy. Best to have really good backups.  Also post boot script.

---

### Post by Starbase 9525 on 2011-08-23
> **YesWeCan said:**
> Hi there. There may be subtle problems. Would you download this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post rhe RESULTS.txt file here. Use code tags to make it easier to read: highlight and press #

Here is the file. It is quite large and I don't know how to do code tags. Sorry.

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   976,768,064   976,768,002   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   163,703,242   163,703,180   7 NTFS / exFAT / HPFS
/dev/sdb2         163,704,830   320,172,031   156,467,202   5 Extended
/dev/sdb5         163,704,832   316,506,111   152,801,280  83 Linux
/dev/sdb6         316,508,160   320,172,031     3,663,872  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders, total 1974271 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     1,974,270     1,974,208   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        17F6-3766                              vfat       NT3500BASIX
/dev/sdb1        E86063006062D53A                       ntfs       
/dev/sdb5        0ee63447-1d0a-4367-b6e3-fbd045f465d9   ext4       
/dev/sdc1        0000-2CE1                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/0000-2CE1         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 0ee63447-1d0a-4367-b6e3-fbd045f465d9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 0ee63447-1d0a-4367-b6e3-fbd045f465d9
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos5)'
	search --no-floppy --fs-uuid --set=root 0ee63447-1d0a-4367-b6e3-fbd045f465d9
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=0ee63447-1d0a-4367-b6e3-fbd045f465d9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos5)'
	search --no-floppy --fs-uuid --set=root 0ee63447-1d0a-4367-b6e3-fbd045f465d9
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=0ee63447-1d0a-4367-b6e3-fbd045f465d9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos5)'
	search --no-floppy --fs-uuid --set=root 0ee63447-1d0a-4367-b6e3-fbd045f465d9
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=0ee63447-1d0a-4367-b6e3-fbd045f465d9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos5)'
	search --no-floppy --fs-uuid --set=root 0ee63447-1d0a-4367-b6e3-fbd045f465d9
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=0ee63447-1d0a-4367-b6e3-fbd045f465d9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos5)'
	search --no-floppy --fs-uuid --set=root 0ee63447-1d0a-4367-b6e3-fbd045f465d9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos5)'
	search --no-floppy --fs-uuid --set=root 0ee63447-1d0a-4367-b6e3-fbd045f465d9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root E86063006062D53A
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

=============================== sdb5/etc/fstab: ================================

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
UUID=0ee63447-1d0a-4367-b6e3-fbd045f465d9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=85938d97-791a-4da6-8c29-361cc62be6af none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 118.194580078 = 126.910464000  boot/grub/core.img                             1
 140.275241852 = 150.619394048  boot/grub/grub.cfg                             1
  79.944709778 = 85.839978496   boot/initrd.img-2.6.38-11-generic              2
  79.474609375 = 85.335212032   boot/initrd.img-2.6.38-8-generic               2
  79.693668365 = 85.570424832   boot/vmlinuz-2.6.38-11-generic                 1
 118.192852020 = 126.908608512  boot/vmlinuz-2.6.38-8-generic                  1
  79.944709778 = 85.839978496   initrd.img                                     2
  79.474609375 = 85.335212032   initrd.img.old                                 2
  79.693668365 = 85.570424832   vmlinuz                                        1
 118.192852020 = 126.908608512  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  cf 6a 51 76 f9 4d a1 fe  43 0b cf 2a f6 6e 81 e9  |.jQv.M..C..*.n..|
00000010  c6 f3 87 cf f2 96 b9 71  dc bc d6 45 ea d3 8d 27  |.......q...E...'|
00000020  d1 c3 67 64 5d b3 d8 ad  55 4c ff 41 92 55 72 43  |..gd]...UL.A.UrC|
00000030  db 4a fd 48 cc 80 e4 92  ce 29 64 25 70 71 5a e4  |.J.H.....)d%pqZ.|
00000040  ea c5 57 d4 81 a5 f9 1b  9c 00 9c 65 35 e1 a7 38  |..W........e5..8|
00000050  d9 2e b9 43 87 0e fe f0  77 05 bc 1f fc e0 07 0f  |...C....w.......|
00000060  e4 95 d3 47 a4 b8 fb fb  df ff fe 4f 7f fa 93 9b  |...G.......O....|
00000070  95 ba 10 45 59 7d 30 90  e9 2a 6f b6 5f 7d d2 49  |...EY}0..*o._}.I|
00000080  27 65 d2 a4 48 d1 e4 bf  f5 d6 5b a7 4c 99 52 74  |'e..H.....[.L.Rt|
00000090  fd d3 0d e0 2a 67 d8 57  78 b5 15 74 0f d8 e8 aa  |....*g.Wx..t....|
000000a0  ab ae b2 e6 bc 92 da ff  fd df ff b5 3c 3b de f5  |............<;..|
000000b0  d7 5f 9f cb 4f 84 a2 36  87 5a 21 09 af db 6e 49  |._..O..6.Z!...nI|
000000c0  91 d8 2a af c7 1e 7b 4c  e5 50 55 61 9b 36 6d 54  |..*...{L.PUa.6mT|
000000d0  f6 dc 3e b2 88 ab 67 ec  c2 24 3b 7d 18 ae d9 95  |..>...g..$;}....|
000000e0  02 ae 5f bf de fa 09 c3  6f b0 c1 ab 85 4e 76 da  |.._.....o....Nv.|
000000f0  d5 ae ef bd f7 9e 16 e2  07 ce 14 e5 a4 fc d0 12  |................|
00000100  13 b7 32 89 76 e5 5c a7  50 e6 5a 15 7d be 86 0d  |..2.v.\.P.Z.}...|
00000110  c1 c0 95 4e ae e1 92 ee  c7 d6 f9 41 d7 30 01 d8  |...N.......A.0..|
00000120  a6 7a d8 66 9b 6d b2 8d  c1 ae 6d ab 00 ac fc e9  |.z.f.m....m.....|
00000130  d1 bc 3f ff f9 cf f7 dc  73 cf 90 21 43 4a 1d 3e  |..?.....s..!CJ.>|
00000140  57 28 f5 54 0e 5d b4 28  9c 70 c2 09 0b 17 2e 0c  |W(.T.].(.p......|
00000150  64 db 16 80 45 c9 74 a9  45 39 75 06 1c fe a0 56  |d...E.t.E9u....V|
00000160  ac e8 fa a7 bb f8 d8 6d  ff 32 27 f8 b5 f1 e7 fe  |.......m.2'.....|
00000170  33 93 27 4f 3e e7 9c 73  94 4b e9 a5 bd f6 da 4b  |3.'O>..s.K.....K|
00000180  c1 b5 e8 8c 1f b3 67 cf  7e fb ed b7 6d 82 08 05  |......g.~...m...|
00000190  e0 d6 93 fe da 1e b7 d2  ab 07 ab 56 ad b2 a1 8e  |...........V....|
000001a0  6d db b6 b5 73 bd ee 12  11 1d 80 2e 92 59 1c 0d  |m...s........Y..|
000001b0  d7 98 ca 7d f5 af 02 b0  9b 78 d2 7f d5 e6 00 fe  |...}.....x......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 1b 09 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 90  1b 09 00 f0 37 00 00 00  |............7...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg sdh 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by Starbase 9525 on 2011-08-23
> **vidtek said:**
> Star..
It would appear you have 3 physical discs
Linux is on sdb5
you don't appear to have a swap disc
You have an NTFS partition sharing your linux drive I would hazard a guess and say that is your XP partition.
sda1 is probably an older legacy drive and I would think that sdc1 is a thumb or usb drive?

Anyway, the drive in which we are interested is definitely sdb.

You didn't say if you are now able to boot into windows in your reply.

Yes there is enough info to do the next step if necessary.

Tony

Windows still does not boot. I have a 150GB IDE drive that is/was my Windows drive. I installed 11.04 on that splitting it roughly in half. Just after doing that, and before checking that Windows would boot, I installed a 500GB SATA drive from another computer that went belly up. It just has files on it, no OS. I also have a thumb drive with some backup files sitting in a USB slot. Tried changing the order of the boot drives but that didn't work. So, basically I only have two physical drives.

---

### Post by Starbase 9525 on 2011-08-23
> **oldfred said:**
> @starbase 9525
Did you change drive order around after installs. Windows usually is sda. If it changed to sdb, the boot.ini may be wrong or other internal settings in boot sector. Boot script will help.

@campb.andrew
Please start your own thread, your issues are a lot different and you also have SFS or dynamic partitions from Windows. I have seen users not even be able to repair their dynamic partitions with windows tools, best to convert back to basic but not easy. Best to have really good backups.  Also post boot script.

Did not change boot order after I installed 11.04. When the boot list comes up Ubuntu is at the top and Windows XP is at the bottom. I did go and change the boot order just to see what would happen and it didn't work so I set it back.

---

### Post by oldfred on 2011-08-23
I meant drive order not boot order. But you have no boot.ini in your XP partition.

Script normally shows these three for XP:
WinXP
/boot.ini /ntldr /NTDETECT.COM

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)

You may not need all these commands.
XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
[COLOR=Red]BOOTCFG  /rebuild  # rebuilds boot.ini[/COLOR]
chkdsk c: /r

If you create boot.ini with Ubuntu, since it is just a text file:
If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to cchoose windows format.

Did you intend to encrypt swap?

---

### Post by vidtek on 2011-10-20
Starbase-

Did you get this sorted?

If so mark it as solved please.

Best regards, Tony.

---

