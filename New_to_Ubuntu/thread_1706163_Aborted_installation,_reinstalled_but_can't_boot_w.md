---
title: "Aborted installation, reinstalled but can't boot windows"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by mvalviar on 2011-03-13
Hello,

I have a windows box with 2 partitions C:\ and D:\. Windows is in D:\. I tried installing ubuntu by reformatting C:\ and installing it there but the installation was interrupted by an outtage. I booted and the display says "please insert a bootable device or media." So I tried installing ubuntu again on the previously C:\ partition. The install completed but I when I but there is no boot option. I see and mount the D:\ partition in ubuntu The windows files are still there.

I tried sudo update-grub but it doesn't see the windows install. What do I do now?

Please help me.

Thanks.

---

### Post by YesWeCan on 2011-03-13
Hi there.
Would you mind posting the output of 'sudo fdisk -l' so we can see your partitions?

---

### Post by mvalviar on 2011-03-14
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41d241d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            6250        6374      999424   82  Linux swap / Solaris
/dev/sda2            6375       19456   105081134+   f  W95 Ext'd (LBA)
/dev/sda3   *           1        6250    50198528   83  Linux
/dev/sda5            6375       19456   105081133+   7  HPFS/NTFS

Partition table entries are not in disk order
```

What happened was: I installed windows and created 2 partitions. I mean to use C:\ for system files and D:\ for user files but I messed up and the windows got installed in D:\. So I decided to remove C:\  repartition in to ext4 and swap and installed ubuntu.

Can I still recover the windows install?

---

### Post by mvalviar on 2011-03-15
up

---

### Post by mvalviar on 2011-03-16
up

---

### Post by Dorsenstein on 2011-03-16
Could you post the contents of /etc/grub/menu.lst please?

---

### Post by mvalviar on 2011-03-20
Hello,

I've been away from the pc in question. 

I don't have that  file I have /etc/grub.d/. I don't have any idea what that is.

---

### Post by Hedgehog1 on 2011-03-20
mvalviar,

Right now it is hard to tell if the NTFS partition that had the Windows OS on it is can be saved.  I am pretty sure windows will not boot from a logical partition; sda5 is a logical rather than a primary partition.

We will need you to do this please:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

If it can be saved will will know from this.

***The Hedge***

:KS

---

### Post by mvalviar on 2011-03-20
```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1         100,399,104   102,397,951     1,998,848  82 Linux swap / Solaris
/dev/sda2         102,398,371   312,560,639   210,162,269   f W95 Ext d (LBA)
/dev/sda5         102,398,373   312,560,639   210,162,267   7 HPFS/NTFS
/dev/sda3    *          2,048   100,399,103   100,397,056  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2034 MB, 2034237440 bytes
63 heads, 62 sectors/track, 1017 cylinders, total 3973120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,972,401     3,972,340   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       a8470e9f-02c9-4abf-83b7-6512c1d6ef12   ext3                                     
/dev/sda1        65f18967-61b6-4f36-b979-1e53fbdaf0f0   swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        8d7e6dcd-8502-4839-80ee-d288c64dcd9e   ext4                                     
/dev/sda5        64F8E86AF8E83BC4                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        58EE-34C2                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
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
search --no-floppy --fs-uuid --set 8d7e6dcd-8502-4839-80ee-d288c64dcd9e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 8d7e6dcd-8502-4839-80ee-d288c64dcd9e
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 8d7e6dcd-8502-4839-80ee-d288c64dcd9e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=8d7e6dcd-8502-4839-80ee-d288c64dcd9e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 8d7e6dcd-8502-4839-80ee-d288c64dcd9e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=8d7e6dcd-8502-4839-80ee-d288c64dcd9e ro single 
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 8d7e6dcd-8502-4839-80ee-d288c64dcd9e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 8d7e6dcd-8502-4839-80ee-d288c64dcd9e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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
UUID=8d7e6dcd-8502-4839-80ee-d288c64dcd9e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=65f18967-61b6-4f36-b979-1e53fbdaf0f0 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


   8.7GB: boot/grub/core.img
  13.0GB: boot/grub/grub.cfg
  47.6GB: boot/initrd.img-2.6.35-22-generic
   8.7GB: boot/vmlinuz-2.6.35-22-generic
  47.6GB: initrd.img
   8.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ec ef 11 be ef bb 1f de  54 82 ed e1 dc 0a f8 ef  |........T.......|
00000010  01 4d 67 ac 7f fe 07 c5  9e c4 27 fa 8e 4c 0a 9f  |.Mg.......'..L..|
00000020  c6 c8 57 27 47 d4 43 f7  16 4c b8 9f 39 e3 3e 0c  |..W'G.C..L..9.>.|
00000030  7e 66 e7 97 28 53 95 4c  db 39 22 c4 a0 29 19 b1  |~f..(S.L.9"..)..|
00000040  02 bc 7e 3a 74 70 56 6d  f9 77 07 23 7b 38 bb 83  |..~:tpVm.w.#{8..|
00000050  d0 29 1f 68 ff 73 ed 0b  2c f9 c5 70 43 74 f6 10  |.).h.s..,..pCt..|
00000060  22 25 4e 29 0a 45 55 4d  aa b6 60 4e d1 65 8e 2d  |"%N).EUM..`N.e.-|
00000070  47 65 ab 11 1f 1b ca bb  d7 2e be 7c 2e 70 51 48  |Ge.........|.pQH|
00000080  e7 67 65 2c db 76 e3 af  bb 9d 4c ee 47 c1 54 75  |.ge,.v....L.G.Tu|
00000090  d9 8f 0d 10 44 d9 45 62  9f af 9e b2 7e ce 1d f5  |....D.Eb....~...|
000000a0  12 1e 84 10 cc e4 77 64  7f 4b dd 32 2e 93 b9 7f  |......wd.K.2....|
000000b0  33 e3 c9 bd 0a 60 97 41  83 47 cf 92 ea ff be 1f  |3....`.A.G......|
000000c0  16 2d 51 7d 00 69 21 e8  9c 46 a0 61 7b 79 7f 89  |.-Q}.i!..F.a{y..|
000000d0  68 b8 91 46 da ad d1 a9  e6 56 70 88 fc 35 1a 91  |h..F.....Vp..5..|
000000e0  10 99 3a 23 a9 3a 37 f0  68 f4 e5 91 52 79 c7 1c  |..:#.:7.h...Ry..|
000000f0  5a 33 c3 34 de 70 59 42  fb 04 9c 91 55 2d ad 37  |Z3.4.pYB....U-.7|
00000100  60 e9 e3 e8 7d 92 aa ff  75 8b ea e7 bb b2 78 34  |`...}...u.....x4|
00000110  bf 32 06 1d 17 a7 31 d2  93 4c 55 42 2a df 01 24  |.2....1..LUB*..$|
00000120  fc 38 46 9d a2 3d 77 e8  56 59 f6 e6 2f 94 69 ce  |.8F..=w.VY../.i.|
00000130  54 7e 6f 81 37 b5 ce e4  60 a4 81 25 24 be fc 9b  |T~o.7...`..%$...|
00000140  62 73 50 af fd 0a 1c fa  12 f0 1c 17 ef 30 5c bb  |bsP..........0\.|
00000150  1c a9 c6 21 7e 54 63 ef  32 df 0b 12 8b 54 0d 55  |...!~Tc.2....T.U|
00000160  a6 cf 6d 0b 79 f9 31 7f  48 6b 0c a8 39 ef 68 cf  |..m.y.1.Hk..9.h.|
00000170  6f b4 79 8c 1a 6a 37 64  ce 15 dc b1 87 08 86 60  |o.y..j7d.......`|
00000180  52 c8 44 0e e2 b6 cc 53  b5 b2 a6 57 72 e5 ab 87  |R.D....S...Wr...|
00000190  cb 4e a7 91 b5 7f d9 19  95 a8 41 bb 10 59 9c 5f  |.N........A..Y._|
000001a0  35 98 65 34 eb b4 bc 51  0c a1 3c c0 3d 56 b0 d7  |5.e4...Q..<.=V..|
000001b0  b1 c6 3f 17 67 a8 e0 f3  0e f1 cb 53 b1 c7 00 fe  |..?.g......S....|
000001c0  ff ff 07 fe ff ff 02 00  00 00 5b d2 86 0c 00 00  |..........[.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by mvalviar on 2011-03-21
up

---

