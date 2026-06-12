---
title: "Re-installing Grub2"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by laugh1 on 2010-12-27
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)
 
I tried using that guide and put all the files in my C:/ but nothing changed during bootup. The tutorial on-site isn't very specific so I wouldn't know where to start there.
 
I'm pretty sure right now I have W7 and Ubuntu on here...but it won't boot it Ubuntu.

---

### Post by wojox on 2010-12-27
I've always had an easy time with [Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by coffeecat on 2010-12-27
You don't actually say what your problem is, but assuming it's what the headline of that link says - that you have installed Windows and lost grub - then I suggest you don't use that link. It is unnecessarily complicated. Instead, have a look at the official documentation here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

But before you follow those instructions, boot up the Ubuntu live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file here in code tags for clarity. That will tell us what is on your system.

---

### Post by laugh1 on 2010-12-27
Hi guys, I followed this tutorial:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

and at the end ran this command:

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/77a7f389-70ca-4ce0-bd24-fbc8c5b663aa /dev/sda1 --recheck

and got this error:

/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.


Now what?

---

### Post by laugh1 on 2010-12-27
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /menu.lst /boot.ini /Windows/System32/winload.exe 
                       /grldr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   428,804,095   428,802,048  83 Linux
/dev/sda2    *    428,804,096   429,008,895       204,800   7 HPFS/NTFS
/dev/sda3         429,008,896   600,565,759   171,556,864   7 HPFS/NTFS
/dev/sda4         600,567,806   625,141,759    24,573,954   5 Extended
/dev/sda5         600,567,808   625,141,759    24,573,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        77a7f389-70ca-4ce0-bd24-fbc8c5b663aa   ext4                                     
/dev/sda2        901AB1991AB17D32                       ntfs       System Reserved               
/dev/sda3        3E88B6A988B65ED9                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3d90640f-8729-4dc9-b8db-0c6904dbbdf3   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/77a7f389-70ca-4ce0-bd24-fbc8c5b663aa ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set 77a7f389-70ca-4ce0-bd24-fbc8c5b663aa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 77a7f389-70ca-4ce0-bd24-fbc8c5b663aa
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
    search --no-floppy --fs-uuid --set 77a7f389-70ca-4ce0-bd24-fbc8c5b663aa
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=77a7f389-70ca-4ce0-bd24-fbc8c5b663aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77a7f389-70ca-4ce0-bd24-fbc8c5b663aa
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=77a7f389-70ca-4ce0-bd24-fbc8c5b663aa ro single 
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
    search --no-floppy --fs-uuid --set 77a7f389-70ca-4ce0-bd24-fbc8c5b663aa
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 77a7f389-70ca-4ce0-bd24-fbc8c5b663aa
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3d90640f-8729-4dc9-b8db-0c6904dbbdf3 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 150.4GB: boot/grub/core.img
  38.8GB: boot/grub/grub.cfg
   3.1GB: boot/initrd.img-2.6.35-22-generic
    .2GB: boot/vmlinuz-2.6.35-22-generic
   3.1GB: initrd.img
    .2GB: vmlinuz

================================ sda3/menu.lst: ================================

timeout 0 
default 0 
title grub2 
find --set-root /boot/grub/core.img 
kernel /boot/grub/core.img 
boot
================================ sda3/boot.ini: ================================

[boot loader] 
timeout=0 
default=c:\grldr.mbr 
[operating systems] 
C:\grldr.mbr="Grub4Dos"
=================== sda3: Location of files loaded by Grub: ===================


    ??GB: menu.lst
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  61 5d 6f 7c 92 db b4 7e  7e d6 a2 af 6e 8c 2c 7c  |a]o|...~~...n.,||
00000010  e7 ee bc 6f 63 bd 5a 8e  3b d4 39 6d 66 70 a2 37  |...oc.Z.;.9mfp.7|
00000020  9b 79 9f 3b 53 d5 c1 1c  ae ea 34 62 c6 e3 2f a2  |.y.;S.....4b../.|
00000030  ba 9f 49 b9 35 ee f1 81  ec e9 de 87 f7 7c fb d9  |..I.5........|..|
00000040  92 2e 37 dc 42 7f f8 6e  b9 46 72 3d f7 d9 61 bf  |..7.B..n.Fr=..a.|
00000050  d1 96 a8 2f 27 1d 18 7d  b2 ca ee 52 fd b7 96 a7  |.../'..}...R....|
00000060  e2 ec 47 27 1e 25 1c 5f  5a e5 e9 55 bf 88 b8 2f  |..G'.%._Z..U.../|
00000070  0f 3d cc a8 d8 53 11 b7  51 bf 89 93 27 5b 2b af  |.=...S..Q...'[+.|
00000080  e2 5e 1f 40 0e 68 e8 64  62 0d ac 98 af cb d7 8c  |.^.@.h.db.......|
00000090  56 25 db 6c 99 fa d6 ad  13 b2 52 7d d3 8a da d0  |V%.l......R}....|
000000a0  37 21 23 ad 75 66 df 14  b2 b5 75 66 56 46 62 4e  |7!#.uf....ufVFbN|
000000b0  82 2d bb b5 7f 14 ec ce  17 9b d8 e0 a2 2c 11 96  |.-...........,..|
000000c0  18 59 3d 2b 14 c9 ac e3  68 1f 29 c1 fe fd fb 57  |.Y=+....h.)....W|
000000d0  94 a0 35 ab 54 4a b6 72  fd 89 3a 9f 48 ae a9 b2  |..5.TJ.r..:.H...|
000000e0  b1 ff 82 a3 bf 79 cf 30  b0 2e 23 2b 55 9b f5 bb  |.....y.0..#+U...|
000000f0  5e 39 fb e0 96 33 ef ee  57 cf 7f 22 5b 34 ef 8b  |^9...3..W.."[4..|
00000100  82 30 41 ff c4 63 69 ca  af 01 7d a3 de 8f d8 e3  |.0A..ci...}.....|
00000110  39 79 cc ee 87 b3 2c 9f  65 29 f3 f7 38 7f fd a1  |9y....,.e)..8...|
00000120  e2 ea ae d4 b8 89 6f eb  aa fd 5c d3 b5 61 ea a3  |......o...\..a..|
00000130  0f e7 ee 69 e3 fc 28 ee  b5 c1 e7 27 77 fa 78 8b  |...i..(....'w.x.|
00000140  f9 93 3a 75 d7 b7 49 6c  56 f5 67 97 13 63 c4 b1  |..:u..IlV.g..c..|
00000150  be f3 a2 12 96 6d de 9d  11 bb e6 34 f7 e5 a2 d3  |.....m.....4....|
00000160  99 0e 63 b3 4f 5e cc 71  53 d6 1e 7e 20 fe a1 4c  |..c.O^.qS..~ ..L|
00000170  59 7f 81 6c 43 ca 9e 05  4d 3a 7b 36 52 ca 36 ee  |Y..lC...M:{6R.6.|
00000180  fe 38 ce f4 f1 8d 11 b1  d6 cb 5b 4c 41 ad 2f f5  |.8........[LA./.|
00000190  3f ba 42 6b ae 7a 79 78  b7 53 27 aa bb 3e ba 3c  |?.Bk.zyx.S'..>.<|
000001a0  65 4c cf 5a 7b 32 37 36  79 52 d3 1a 33 71 f9 b9  |eL.Z{276yR..3q..|
000001b0  8d f3 ce bc b3 32 ae c9  af ad 0c 8b 4f d4 00 fe  |.....2......O...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 76 01 00 00  |............v...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

That is my results.txt

---

### Post by drs305 on 2010-12-27
By including the partition number you tried installing G2 to a partition instead of the MBR. It can be done but generally isn't necessary and thus you got the warning messages. 

To boot your sda1 Ubuntu, you can run the command like this from the LiveCD. Do not put the partition number in the second command:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

After rebooting, you may need to run "sudo update-grub" to get Windows on the menu.

---

### Post by amjjawad on 2010-12-27
And don't forget to check the signature of drs305 ;)

---

