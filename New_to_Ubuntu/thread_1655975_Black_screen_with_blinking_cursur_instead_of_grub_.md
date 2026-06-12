---
title: "Black screen with blinking cursur instead of grub (dualboot)"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by Tovam on 2010-12-30
Hello

I have a dualboot with Ubuntu 10.10 (64bit) and Windows 7 (32bit), which has worked fine for months.
Today, I installed a 64bit version of Windows 7 over my old Windows 7. The install went fine, and I could successfully boot in Windows 7 afterwards, but of course my grub was gone.

I live booted from an Ubuntu 10.04 cd that I had lying around, and did
```

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

```
I got an "Installation finished. No error reported." message, but when I rebooted, I got a black screen with a white blinking cursor after my bios splash screen, where I should have gotten my grub menu. The screen does not accept keyboard input.

I ran the Windows 7 dvd and did a boot repair, but it said it couldn't find any problems. Neither OS wanted to boot though.

So, I guess the problem is me messing up the grub installation, but does anyone know how to fix it?
Thanks

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7d087d08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       56667   455177646   83  Linux
/dev/sda2           56668       60801    33206355   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe888cfd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1958    15727603+  83  Linux
/dev/sdb2   *        1959       20234   146801970    7  HPFS/NTFS
/dev/sdb3           20235       38913   150039067+   5  Extended
/dev/sdb5           20235       20756     4192933+  82  Linux swap / Solaris
/dev/sdb6           20757       36302   124873213+  83  Linux
/dev/sdb7           36303       38913    20972826    7  HPFS/NTFS

```
Where /dev/sdb1 is my Ubuntu root, and /dev/sdb2 my Windows install.

Oh, I am using grub2, not grub legacy, my bios is set to boot my second hard drive (/dev/sdb), and I have no devices plugged in.

---

### Post by Rubi1200 on 2010-12-30
Hi,
from the LiveCD download and run the boot info script linked at the bottom of my post.

Get the results back here please.

Thanks.

---

### Post by Mindswap1 on 2010-12-30
This is prob not the best suggestion, but this always happens to me when I have something plugged into the usb port like an ipod or psp. Maybe its the same problem for you. All you have to do is take out the device plugged in.

---

### Post by Tovam on 2010-12-30
Thanks for the replies.

@ Mindswap1: Apart from my keyboard and mouse, I have no devices plugged in.

@ Rubi1200: I added the results as an attachment to this post. The thing that caught my eye is that I have grub installed on both /dev/sda and /dev/sdb, and it wouldn't surprise me if that's the cause of my problem.
I'm not sure how to fix it though, do you have any suggestions?

---

### Post by Rubi1200 on 2010-12-30
Thanks for the results.

Couple of issues to deal with here:

1. GRUB is installed in the MBR of both drives, but from what I understood you are booting sdb.

On a related note, there is an error with the GRUB install on sdb1:
> Grub 2 is installed in the boot sector of sdb1

2. your fstab file is also seemingly out of sync. I assume you installed to sdb after whatever you did on sda?

The fix:
purge and reinstall GRUB using the chroot method outlined in this fantastic guide by drs305:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You must use the chroot method and make sure to mount sdb1 as the Ubuntu install and install GRUB to the MBR of sdb.

Don't forget to run sudo update-grub in Ubuntu after rebooting (and hopefully getting back in again).

Let me know how it goes.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 1710527 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1                  63   910,355,354   910,355,292  83 Linux
/dev/sda2         910,355,355   976,768,064    66,412,710  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    31,455,269    31,455,207  83 Linux
/dev/sdb2    *     31,455,270   325,059,209   293,603,940   7 HPFS/NTFS
/dev/sdb3         325,059,210   625,137,344   300,078,135   5 Extended
/dev/sdb5         325,059,273   333,445,139     8,385,867  82 Linux swap / Solaris
/dev/sdb6         333,445,203   583,191,629   249,746,427  83 Linux
/dev/sdb7         583,191,693   625,137,344    41,945,652   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        df829a1e-cd13-4bc9-a2b4-1da1a64ab71e   ext3       storage                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5ae22ea0-b262-4610-bf17-bd030c6db3f4   ext4                                     
/dev/sdb2        3AD5077A160A949F                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        c09b32fb-a8c8-4fd5-b046-4dbf5b6b218d   swap                                     
/dev/sdb6        ac1cf7ca-4936-4f37-8764-1965846a13a9   ext3                                     
/dev/sdb7        79D4E6FB7F07D4F0                       ntfs       shared                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /mnt                     ext4       (rw)


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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 5ae22ea0-b262-4610-bf17-bd030c6db3f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 5ae22ea0-b262-4610-bf17-bd030c6db3f4
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5ae22ea0-b262-4610-bf17-bd030c6db3f4
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=5ae22ea0-b262-4610-bf17-bd030c6db3f4 ro ipv6.disable=1  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5ae22ea0-b262-4610-bf17-bd030c6db3f4
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=5ae22ea0-b262-4610-bf17-bd030c6db3f4 ro single ipv6.disable=1
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5ae22ea0-b262-4610-bf17-bd030c6db3f4
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=5ae22ea0-b262-4610-bf17-bd030c6db3f4 ro ipv6.disable=1  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 5ae22ea0-b262-4610-bf17-bd030c6db3f4
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=5ae22ea0-b262-4610-bf17-bd030c6db3f4 ro single ipv6.disable=1
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 3ad5077a160a949f
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
proc            /proc           proc    defaults        0       0

# / was on /dev/sda1 during installation
UUID=5ae22ea0-b262-4610-bf17-bd030c6db3f4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ac1cf7ca-4936-4f37-8764-1965846a13a9 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=c09b32fb-a8c8-4fd5-b046-4dbf5b6b218d none            swap    sw              0       0

# cd-drive
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# shared folder for Linux, Windows and virtual machines
/dev/sdb7 /media/shared ntfs-3g defaults 0 0
# storage folder on second hard drive
/dev/sda1 /media/storage ext3 defaults 0 0

=================== sdb1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
  10.9GB: boot/grub/grub.cfg
  11.4GB: boot/initrd.img-2.6.32-24-generic-pae
   1.7GB: boot/initrd.img-2.6.35-22-generic-pae
  10.6GB: boot/vmlinuz-2.6.32-24-generic-pae
  15.2GB: boot/vmlinuz-2.6.35-22-generic-pae
   1.7GB: initrd.img
  11.4GB: initrd.img.old
  15.2GB: vmlinuz
  10.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  a9 91 d5 46 9a 9b 75 45  6f 5a 8a ee e1 5c e6 14  |...F..uEoZ...\..|
00000010  48 d3 f5 00 da 8f 2d ab  3c d3 97 49 41 8c f2 87  |H.....-.<..IA...|
00000020  21 fd 82 20 b5 8d c8 6d  99 4f 01 01 36 6d 2c cd  |!.. ...m.O..6m,.|
00000030  0f be 72 c4 fa 3a 9d 23  5c fe 86 a7 00 7a 8c ce  |..r..:.#\....z..|
00000040  cc 24 11 7c 48 c2 af 88  7c 04 4a 7c 0c 3a e3 38  |.$.|H...|.J|.:.8|
00000050  fc 3d 67 bc 8f 49 6c 3f  21 f6 ca 4b df 43 66 61  |.=g..Il?!..K.Cfa|
00000060  06 5b 6c fa 87 fe ab d0  a9 33 7a 54 92 e7 16 b8  |.[l......3zT....|
00000070  86 28 66 3c a6 26 33 90  ac 66 f4 e5 61 d3 9c de  |.(f<.&3..f..a...|
00000080  e7 be e6 59 cd d5 2c d3  ee b9 44 d1 f3 c9 6b 3a  |...Y..,...D...k:|
00000090  2d 65 01 fc 8b 6c 45 6e  8e a9 22 96 c1 54 f5 32  |-e...lEn.."..T.2|
000000a0  f0 c6 be 12 d6 cc c6 79  e6 ea 27 cc f4 e4 19 83  |.......y..'.....|
000000b0  34 2d 64 be 44 54 18 86  d4 9a 5e f7 9a 00 64 7f  |4-d.DT....^...d.|
000000c0  0e 56 0b d5 77 98 9e 3a  d1 f2 89 3f 0b 3e 3d 1a  |.V..w..:...?.>=.|
000000d0  1a 53 8f 3f 46 fc 48 9e  8f 2d 08 fc 07 90 fe bf  |.S.?F.H..-......|
000000e0  7c 3b 6a ec 91 4f b3 54  9e 33 84 8c 9d 6e 54 e4  ||;j..O.T.3...nT.|
000000f0  43 4d 22 89 00 07 c3 b6  4c 66 6d 9f 6a 29 54 9f  |CM".....Lfm.j)T.|
00000100  fc 09 ae 52 e7 54 ca 45  36 28 7a 21 5d b2 f2 bd  |...R.T.E6(z!]...|
00000110  29 2b 75 05 06 76 42 ff  e8 1f 9a 39 c9 1b a5 39  |)+u..vB....9...9|
00000120  2f f4 96 52 a3 82 d7 a8  f4 99 e5 22 02 9a 9b 40  |/..R......."...@|
00000130  2e 0d 75 cd 2e 1c a7 14  ef 04 91 a5 37 a4 c0 49  |..u.........7..I|
00000140  a8 18 db 2e 2b 1e 8a eb  ba 97 3d ca 27 f4 84 01  |....+.....=.'...|
00000150  41 79 fb 39 d6 d6 3f ac  1e d4 c1 d0 e3 b3 75 79  |Ay.9..?.......uy|
00000160  38 b4 aa 23 d0 67 20 c1  e4 e8 a4 7d 4b c2 d7 75  |8..#.g ....}K..u|
00000170  43 57 80 ed cd 93 4d 4f  7f 6e 3b 61 09 ec 93 06  |CW....MO.n;a....|
00000180  ff 98 5c 25 2f 45 77 fe  c7 17 20 c3 ff bd e4 4f  |..\%/Ew... ....O|
00000190  8e de 99 3e bc 54 7a 76  1a 39 3d eb 05 b7 12 c5  |...>.Tzv.9=.....|
000001a0  1e 64 43 ff 3f 17 f6 6b  dd 8b cc 82 ea e3 4f 1e  |.dC.?..k......O.|
000001b0  19 b3 59 77 7a 11 5b 0e  1f 19 b0 fa 3f cb 00 58  |..Ywz.[.....?..X|
000001c0  f2 b7 8e 0d 42 b1 e7 c9  07 f1 f0 95 be 08 c8 a2  |....B...........|
000001d0  6c 45 7d bb 86 4b 08 bc  a9 0c 49 f9 61 02 56 4c  |lE}..K....I.a.VL|
000001e0  b1 5e e5 40 d8 82 67 2e  c7 9f ee fe fc 3d 31 3d  |.^.@..g......=1=|
000001f0  cf d9 90 3f 44 1d 2f 77  5a e8 03 ce d7 54 76 f5  |...?D./wZ....Tv.|
00000200


```

---

### Post by Tovam on 2010-12-30
Purging and reinstalling grub the way that guide says fixed it, thank you very much for your help.

---

### Post by Rubi1200 on 2010-12-30
No problem, you are more than welcome :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

