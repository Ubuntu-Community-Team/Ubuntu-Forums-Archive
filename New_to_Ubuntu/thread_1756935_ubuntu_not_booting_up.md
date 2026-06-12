---
title: "ubuntu not booting up"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by holywhistler on 2011-05-12
Hello,
 
I am a noob with Ubuntu and linux in general, I recently removed windows from my laptop and installed 11.04, I had some issues with unity so I decided to get 10.10. I got it installed but after the installation is not booting up, once I turn my laptop on it takes me to the GNU Grub thing with some memory sizes and that says "[ Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]"

Im stuck there and have no Idea of what to do. I can boot from my USB which I used to install it on the first place. I created the usb using the universal usb installer.
 
My HD is a 120gb partitioned in 2 one is a file repository and the other has Ubuntu(and nothing else) installed on it.
 
I have seen several posts with similar cases and have had no luck.
 
Any help is very appreciated.
 
Thanks!

---

### Post by Hedgehog1 on 2011-05-12
We need to get a look at what shape your install is in, and then see what we can do to help.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by holywhistler on 2011-05-13
Here is it, hope you can help

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 3229184 
    on boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sdb. Stage2 looks on partition #1 for /boot/grub/grub.conf.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             80    15,663,103    15,663,024   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    36,868,095    36,866,048  83 Linux
/dev/sdb2          36,869,236   234,436,544   197,567,309   f W95 Ext d (LBA)
/dev/sdb5          36,869,238   234,436,544   197,567,307   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0A00-332F                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a3aabcfa-05e3-41e8-91ed-03091f75c487   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        6C6C392E6C38F484                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb5        /media/6C6C392E6C38F484  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing"
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=a3aabcfa-05e3-41e8-91ed-03091f75c487 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
    echo    'Loading Linux 2.6.35-19-generic ...'
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=a3aabcfa-05e3-41e8-91ed-03091f75c487 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
    multiboot    /boot/memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
    multiboot    /boot/memtest86+_multiboot.bin console=ttyS0,115200n8
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=a3aabcfa-05e3-41e8-91ed-03091f75c487 /               ext4    errors=remount-ro 0       1

=================== sdb1: Location of files loaded by Grub: ===================


  10.9GB: boot/grub/core.img
  13.0GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.35-19-generic
  10.9GB: boot/vmlinuz-2.6.35-19-generic
   1.4GB: initrd.img
  10.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 50 00 00 00  |........?...P...|
00000020  b0 ff ee 00 09 77 00 00  00 00 00 00 02 00 00 00  |.....w..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 2f 33 00 0a 4e  4f 20 4e 41 4d 45 20 20  |..)/3..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 36  ee 00 00 66 ba 00 00 00  |..E}.f.6...f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  e7 a1 30 8d 73 01 00 00  00 5a 00 00 00 00 00 00  |..0.s....Z......|
00000010  80 00 00 00 01 00 04 80  50 00 00 00 60 00 00 00  |........P...`...|
00000020  00 00 00 00 14 00 00 00  02 00 3c 00 02 00 00 00  |..........<.....|
00000030  00 00 18 00 ff 01 1f 00  01 02 00 00 00 00 00 05  |................|
00000040  20 00 00 00 20 02 00 00  00 00 14 00 ff 01 1f 00  | ... ...........|
00000050  01 01 00 00 00 00 00 05  12 00 00 00 00 00 00 00  |................|
00000060  80 80 00 00 01 02 00 00  00 00 00 05 20 00 00 00  |............ ...|
00000070  20 02 00 00 01 01 00 00  00 00 00 05 12 00 00 00  | ...............|
00000080  ff 75 f8 e8 07 f5 db ff  53 ff 75 ec 89 45 e8 ff  |.u......S.u..E..|
00000090  75 f8 e8 f8 f4 db ff ff  75 f8 89 45 ec 8d 45 e0  |u.......u..E..E.|
000000a0  50 8d 45 d0 50 e8 a4 25  ff ff 8a 86 81 00 00 00  |P.E.P..%........|
000000b0  8b 5d 08 24 18 3c 08 0f  84 81 00 00 00 53 e8 09  |.].$.<.......S..|
000000c0  84 e7 ff 3b c3 75 77 f6  86 81 00 00 00 18 75 06  |...;.uw.......u.|
000000d0  83 4d fc 0a eb 19 83 4d  fc 08 57 53 e8 04 85 e7  |.M.....M..WS....|
000000e0  ff 50 e8 64 9a e7 ff 85  c0 74 04 83 4d fc 04 3b  |.P.d.....t..M..;|
000000f0  1d 18 8b 77 30 75 07 81  4d fc 00 02 00 00 ff 75  |...w0u..M......u|
00000100  fc 8b 45 dc 2b 45 d4 50  8b 45 d8 2b 45 d0 50 53  |..E.+E.P.E.+E.PS|
00000110  e8 c3 c1 e4 ff 6a ff 53  e8 89 30 da ff 53 e8 83  |.....j.S..0..S..|
00000120  2b fb ff 53 e8 dd 74 e1  ff 85 c0 74 07 57 53 e8  |+..S..t....t.WS.|
00000130  2e 17 e1 ff 66 83 a6 81  00 00 00 e7 eb 39 8b 45  |....f........9.E|
00000140  dc 2b 45 d4 6a 09 50 8b  45 d8 2b 45 d0 50 53 e8  |.+E.j.P.E.+E.PS.|
00000150  84 c1 e4 ff 53 e8 ac 74  e1 ff 85 c0 74 19 57 53  |....S..t....t.WS|
00000160  e8 fd 16 e1 ff eb 10 83  7d f4 00 74 0a 85 db 74  |........}..t...t|
00000170  06 8b 03 53 ff 50 08 5f  5e 5b c9 c2 08 00 55 8b  |...S.P._^[....U.|
00000180  ec 6a 00 ff 75 08 e8 52  f1 ff ff 85 c0 74 0c ff  |.j..u..R.....t..|
00000190  75 10 ff 75 0c 50 e8 47  f2 ff ff 5d c2 0c 00 55  |u..u.P.G...]...U|
000001a0  8b ec 56 57 8b 7d 08 8b  cf e8 a2 a1 d4 ff 85 c0  |..VW.}..........|
000001b0  74 1b 8b 15 74 2b 6a 30  8b cf 8b c7 c1 e9 00 01  |t...t+j0........|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 4b a3 c6 0b 00 00  |..........K.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Hedgehog1 on 2011-05-13
Finally - an easy one!

Please boot from the **_10.10_** LiveCD/LiveUSB, select 'TRY'.

The enter these two commands:

```
sudo mount /dev/sd**a2** /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

This will get grub looking at dev/sda2 rather than the /dev/sda1 it is incorrectly looking for (/dev/sda1 is not a Linux partition).

Your should be able to reboot an operate normally.

***The Hedge***

:KS

---

### Post by holywhistler on 2011-05-13
when running the first command I get ```
mount: can't find /dev/sda2/mnt in /etc/fstab or /etc/mtab
```when running the second I got some results, after that I rebooted and now I am not dropping to the gnu grub thing but I get stuck on a blinking thing that never moves up.

any advice?

---

### Post by garvinrick4 on 2011-05-13
Hedgehog1 the bootscript says sdb is the drive / is at. And grub-legacy is in mbr for some
reason. Best purge all grub grub-common grub-pc in sdb1 and reinstall grub-common grub-pc while in chroot and update-grub. 
He has flash as sda and HDD as sdb so might be a thing.

---

### Post by garvinrick4 on 2011-05-13
Hey holywhistler why is flash drive sda and your 120 gig internal sdb when you take
the flash drive out internal will be sda and problem will come up I believe. I will give
you commands in next post. Do you know something I do not about flash being first
in order of drives.

---

### Post by holywhistler on 2011-05-13
Well I am booting up from the flashdrive cause otherwise it wouldn't work, regarding it being first on the list I am not really sure.

---

### Post by garvinrick4 on 2011-05-13
This will put grub2 in mbr of sdb have to do it while in root of install at sdb1 copy and paste into a terminal. (Still do not know why 1 drive and is sdb instead of sda.)


```
sudo mount /dev/sdb1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
 
``````
apt-get purge grub grub-common grub-pc
``````
apt-get install grub-common grub-pc
``````
 grub-install /dev/sdb
``````
update-grub
``````
exit
```                                  ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
``````
sudo shutdown -r now
```

---

### Post by holywhistler on 2011-05-13
```
cp: `/etc/resolv.conf' and `/mnt/etc/resolv.conf' are the same file
```

Thats what I get with the first command you posted, should I continue?

---

### Post by garvinrick4 on 2011-05-13
> **holywhistler said:**
> Well I am booting up from the flashdrive cause otherwise it wouldn't work, regarding it being first on the list I am not really sure.
Well was sdb at install the bootscript says so run the code then boot from HDD after
and let me know. Code should work just worried about sdb instead of sda after you
pull flash drive out. Let me know.

---

### Post by garvinrick4 on 2011-05-13
> **holywhistler said:**
> ```
cp: `/etc/resolv.conf' and `/mnt/etc/resolv.conf' are the same file
```Thats what I get with the first command you posted, should I continue?
That is the internet connection. Is just copying the connection to /mnt so you will be online
to get packages. If you are not in root after the command no do not go to next command.
You are using the flash drive and it does have a internet connection correct. You are using the flash drive now.
Does it bring you to a root prompt in terminal?

---

### Post by garvinrick4 on 2011-05-13
Ok get your internet connection working in flash drive.
Unmount everything that mounted with this and start over with first command.
  	 	 	 	 	```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 
```

---

### Post by holywhistler on 2011-05-13
when I try
```

apt-get grub-install /dev/sdb
```

I get

```
E: Invalid operation grub-install
```

---

### Post by garvinrick4 on 2011-05-13
Gezz I am sorry it is.
```
grub-install /dev/sdb
```

---

### Post by holywhistler on 2011-05-13
with that I get

```
rm: cannot remove `/boot/grub/915resolution.mod': Permission denied
```

BTW sorry for being such a pain

---

### Post by garvinrick4 on 2011-05-13
thats ok you are not in root. Lets start over.  Make sure you have your internet running
with your flash drive. Now we will make sure nothing mounted and start over. Run this in terminal.
                          ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 
```Now go back to the commands I gave you and start over. Make sure you are in flash drive
and internet is working on flash drive. We will get it, keep going.

---

### Post by holywhistler on 2011-05-13
probably a rookie question, but how do I know if my internet is running on the flash drive?

---

### Post by garvinrick4 on 2011-05-13
> **holywhistler said:**
> probably a rookie question, but how do I know if my internet is running on the flash drive? Open firefox and see if you can get online.

---

### Post by holywhistler on 2011-05-13
Oh ok, well Im online In fact I am replying through my Ubuntu computer

---

### Post by garvinrick4 on 2011-05-13
good run post 17 to unmount anything that could be. And then go back and start the string of code over. Should be ok now.

---

### Post by holywhistler on 2011-05-13
with the code in post 17 i get this

```
umount: /mnt/dev/pts: not found

```

I get thats ok, cause means nothing is mounted, right?

---

### Post by garvinrick4 on 2011-05-13
> I get thats ok, cause means nothing is mounted, right?
There you go. Start the commands now. One at a time.

---

### Post by holywhistler on 2011-05-13
> **garvinrick4 said:**
> That is the internet connection. Is just copying the connection to /mnt so you will be online
to get packages. If you are not in root after the command no do not go to next command.
You are using the flash drive and it does have a internet connection correct. You are using the flash drive now.
Does it bring you to a root prompt in terminal?

I got that again with the first code, can you please explain?

---

### Post by garvinrick4 on 2011-05-13
> **holywhistler said:**
> I got that again with the first code, can you please explain?
I am copying /etc/resolv.conf to /mnt/etc/resolv.conf which is your internet connection over to the /dev/sdb1 we are mounting in /mnt
# So somewhere we are not on the same page.
Are you using a flash drive right now.
Are you by chance in your Ubuntu install of 10.10 and not your flash drive.

When you run the code it is telling me etc/resolv.conf and /mnt/etc/resolv.conf have the
same thing in them, nothing different. Why nothing different to copy? Or you are not even in a flash drive
but using your install but will only boot if you have the flash drive in? If that is the case
let me know?

---

### Post by holywhistler on 2011-05-13
I was a little confused with all the flash drive thing, I am currently using my install which I got to work by booting from my USB, I think i am running my install because it makes no difference if I remove the stick or not.

---

### Post by garvinrick4 on 2011-05-13
If in flash drive and using it not install run this and tell me what it says.

```
gedit /etc/resolv.conf
```

---

### Post by holywhistler on 2011-05-13
a "text file" opened with this on it

```
# Generated by NetworkManager
domain amnet.co.cr
search amnet.co.cr
nameserver 192.168.0.1
```

---

### Post by garvinrick4 on 2011-05-13
If you are in the install then run in terminal with internet working.
```
sudo apt-get purge grub grub-common grub-pc
```
```
sudo apt-get install grub-common grub-pc
```
```
sudo grub-install /dev/sdb
```
```
sudo update-grub
```
```
sudo reboot
```
Let me know:

---

### Post by holywhistler on 2011-05-13
When I ran the second command I got a blue screen asking where to install grub, I selected the drive in which my install is, I continued with the rest of the commands and guess what? ITS WORKING!!!!!!:D I rebooted a couple of times and even shut down to test and It worked all the times( except one time I got something with unable to enumerate usb device in port 1, with no flash drive plugged) but still it booted.

Thank you so very much for the patience!!

---

### Post by garvinrick4 on 2011-05-13
> **holywhistler said:**
> When I ran the second command I got a blue screen asking where to install grub, I selected the drive in which my install is, I continued with the rest of the commands and guess what? ITS WORKING!!!!!!:D I rebooted a couple of times and even shut down to test and It worked all the times( except one time I got something with unable to enumerate usb device in port 1, with no flash drive plugged) but still it booted.

Thank you so very much for the patience!! Very good I am glad you are up and running. Some confusion but it got done. Enjoy it.

---

### Post by garvinrick4 on 2011-05-13
If you get a chance run that script for me again I am interested and seeing it now.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

Like you did at start. Thanks.

---

### Post by holywhistler on 2011-05-13
Sure here it is

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 21384600 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    36,868,095    36,866,048  83 Linux
/dev/sda2          36,869,236   234,436,544   197,567,309   f W95 Ext d (LBA)
/dev/sda5          36,869,238   234,436,544   197,567,307   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        a3aabcfa-05e3-41e8-91ed-03091f75c487   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6C6C392E6C38F484                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media/6C6C392E6C38F484  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
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
    search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=a3aabcfa-05e3-41e8-91ed-03091f75c487 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=a3aabcfa-05e3-41e8-91ed-03091f75c487 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=a3aabcfa-05e3-41e8-91ed-03091f75c487 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
    echo    'Loading Linux 2.6.35-19-generic ...'
    linux    /boot/vmlinuz-2.6.35-19-generic root=UUID=a3aabcfa-05e3-41e8-91ed-03091f75c487 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a3aabcfa-05e3-41e8-91ed-03091f75c487
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
# / was on /dev/sdb1 during installation
UUID=a3aabcfa-05e3-41e8-91ed-03091f75c487 /               ext4    errors=remount-ro 0       1

=================== sda1: Location of files loaded by Grub: ===================


  10.9GB: boot/grub/core.img
  15.2GB: boot/grub/grub.cfg
   2.0GB: boot/initrd.img-2.6.35-19-generic
   3.0GB: boot/initrd.img-2.6.35-28-generic
  10.9GB: boot/vmlinuz-2.6.35-19-generic
  11.0GB: boot/vmlinuz-2.6.35-28-generic
   3.0GB: initrd.img
   2.0GB: initrd.img.old
  11.0GB: vmlinuz
  10.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  e7 a1 30 8d 73 01 00 00  00 5a 00 00 00 00 00 00  |..0.s....Z......|
00000010  80 00 00 00 01 00 04 80  50 00 00 00 60 00 00 00  |........P...`...|
00000020  00 00 00 00 14 00 00 00  02 00 3c 00 02 00 00 00  |..........<.....|
00000030  00 00 18 00 ff 01 1f 00  01 02 00 00 00 00 00 05  |................|
00000040  20 00 00 00 20 02 00 00  00 00 14 00 ff 01 1f 00  | ... ...........|
00000050  01 01 00 00 00 00 00 05  12 00 00 00 00 00 00 00  |................|
00000060  80 80 00 00 01 02 00 00  00 00 00 05 20 00 00 00  |............ ...|
00000070  20 02 00 00 01 01 00 00  00 00 00 05 12 00 00 00  | ...............|
00000080  ff 75 f8 e8 07 f5 db ff  53 ff 75 ec 89 45 e8 ff  |.u......S.u..E..|
00000090  75 f8 e8 f8 f4 db ff ff  75 f8 89 45 ec 8d 45 e0  |u.......u..E..E.|
000000a0  50 8d 45 d0 50 e8 a4 25  ff ff 8a 86 81 00 00 00  |P.E.P..%........|
000000b0  8b 5d 08 24 18 3c 08 0f  84 81 00 00 00 53 e8 09  |.].$.<.......S..|
000000c0  84 e7 ff 3b c3 75 77 f6  86 81 00 00 00 18 75 06  |...;.uw.......u.|
000000d0  83 4d fc 0a eb 19 83 4d  fc 08 57 53 e8 04 85 e7  |.M.....M..WS....|
000000e0  ff 50 e8 64 9a e7 ff 85  c0 74 04 83 4d fc 04 3b  |.P.d.....t..M..;|
000000f0  1d 18 8b 77 30 75 07 81  4d fc 00 02 00 00 ff 75  |...w0u..M......u|
00000100  fc 8b 45 dc 2b 45 d4 50  8b 45 d8 2b 45 d0 50 53  |..E.+E.P.E.+E.PS|
00000110  e8 c3 c1 e4 ff 6a ff 53  e8 89 30 da ff 53 e8 83  |.....j.S..0..S..|
00000120  2b fb ff 53 e8 dd 74 e1  ff 85 c0 74 07 57 53 e8  |+..S..t....t.WS.|
00000130  2e 17 e1 ff 66 83 a6 81  00 00 00 e7 eb 39 8b 45  |....f........9.E|
00000140  dc 2b 45 d4 6a 09 50 8b  45 d8 2b 45 d0 50 53 e8  |.+E.j.P.E.+E.PS.|
00000150  84 c1 e4 ff 53 e8 ac 74  e1 ff 85 c0 74 19 57 53  |....S..t....t.WS|
00000160  e8 fd 16 e1 ff eb 10 83  7d f4 00 74 0a 85 db 74  |........}..t...t|
00000170  06 8b 03 53 ff 50 08 5f  5e 5b c9 c2 08 00 55 8b  |...S.P._^[....U.|
00000180  ec 6a 00 ff 75 08 e8 52  f1 ff ff 85 c0 74 0c ff  |.j..u..R.....t..|
00000190  75 10 ff 75 0c 50 e8 47  f2 ff ff 5d c2 0c 00 55  |u..u.P.G...]...U|
000001a0  8b ec 56 57 8b 7d 08 8b  cf e8 a2 a1 d4 ff 85 c0  |..VW.}..........|
000001b0  74 1b 8b 15 74 2b 6a 30  8b cf 8b c7 c1 e9 00 01  |t...t+j0........|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 4b a3 c6 0b 00 00  |..........K.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

 
```

---

### Post by garvinrick4 on 2011-05-13
**Well it went back to sda instead of sdb from original boot script. So now you can
use sda to install grub2 to if ever have to again not sdb. Still shows that was installed
to drive sdb at install in fstab. If it works it works,  still has a flaw in sda1 now (grub installed in sda1 and then installed in sda so works, looks a bit sloppy.)
Can be fixed,  fstab can be fixed also if you ever want to. Working now so up to you. 
**Confusion at start of thread I was assuming you were booted into your
flash drive and we were trying to fix boot from there. Big difference in code from within your install which you were, lot simpler.
We figured it out in long run so no big deal. Contact me if need any help with this install in future. 

**Remember the code a gave you using sdb drive from first boot script is now sda in second boot script. That is good thing.
    fstab still says original install in sdb1 which does not exist now.  So if fstab not fixed might have to use UUID # to mount if ever have to mount in Live CD.
If you do not understand that right now you will later, me to it can be a bit confusing at times so don't worry and keep using Ubuntu. See your UUID # below:
=============================== sda1/etc/fstab: ===============================  #
 /etc/fstab: static file system information. 
# # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. 
See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    nodev,noexec,nosuid 0       0 
# / was on /dev/sdb1 during installation 
UUID=a3aabcfa-05e3-41e8-91ed-03091f75c487 /               ext4    errors=remount-ro 0       1

---

### Post by omegadestroy on 2012-02-11
hi all. i had dual boot windows 7 and ubuntu 11.04 and for some reason, grub won't boot ubuntu anymore on the list. it only shows windows 7. tried boot-repair but didn't work. 

below is the log from boot-repair
[URL="http://paste.ubuntu.com/837922/"]http://paste.ubuntu.com/837922/
[/URL]

Ubuntu Pastebin

Paste from boot-repair at Sat, 11 Feb 2012 16:27:07 +0000
Download as text

```

                 Boot Info Script 0.60-git      [2 Jan 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

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
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:  Syslinux looks at sector 7355312 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   156,392,447   156,185,600   7 NTFS / exFAT / HPFS
/dev/sda3         156,393,470   312,580,095   156,186,626   5 Extended
/dev/sda5         156,393,472   306,440,191   150,046,720  83 Linux
/dev/sda6         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4006 MB, 4006608896 bytes
124 heads, 62 sectors/track, 1017 cylinders, total 7825408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,818,695     7,818,634   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5C8AC2C68AC29BC0                       ntfs       System Reserved
/dev/sda2        EE80C76380C7313F                       ntfs       
/dev/sda5        9ed759f9-e94e-4c63-a08b-ac8eab1f782a   ext4       
/dev/sda6        17598eaf-60cd-4cfe-ac65-510ebd631f4e   swap       
/dev/sdb1        B349-DE08                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set default="5"
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
search --no-floppy --fs-uuid --set=root 9ed759f9-e94e-4c63-a08b-ac8eab1f782a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 9ed759f9-e94e-4c63-a08b-ac8eab1f782a
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 5C8AC2C68AC29BC0
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
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
UUID=9ed759f9-e94e-4c63-a08b-ac8eab1f782a /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda6 during installation
UUID=17598eaf-60cd-4cfe-ac65-510ebd631f4e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 122.704139709 = 131.752566784  boot/grub/core.img                             1
 122.704719543 = 131.753189376  boot/grub/grub.cfg                             1
  88.082542419 = 94.577909760   boot/initrd.img-2.6.38-13-generic              2
  87.172183990 = 93.600419840   boot/vmlinuz-2.6.38-13-generic                 2
  88.082542419 = 94.577909760   initrd.img                                     2
  87.172183990 = 93.600419840   vmlinuz                                        2

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 88 f1 08 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 88  f1 08 00 b0 5d 00 00 00  |............]...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-02-11__15h20 ****************
boot-repair version : 3.16-0ppa2~natty
boot-sav version : 3.16-0ppa4~natty
g2s version : 0.2-0ppa4~natty
internet: connected
/usr/share/boot-sav/gui-update.sh: line 226: hash: os-uninstaller: not found
/usr/share/boot-sav/gui-update.sh: line 228: hash: cleanubiquitybefore: not found
/usr/share/boot-sav/gui-update.sh: line 231: python-software-properties: command not found
python-software-properties version :
Reading package lists...
Building dependency tree...SET@_progressbar1.pulse()

Reading state information...
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 300 not upgraded.
Need to get 219 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) natty/main boot-sav all 3.16-0ppa4~natty [219 kB]
Download complete and in download only mode
Reading package lists...
Building dependency tree...SET@_progressbar1.pulse()

Reading state information...
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 300 not upgraded.
Need to get 41.5 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) natty/main glade2script all 0.2-0ppa4~natty [41.5 kB]
Download complete and in download only mode
Reading package lists...
Building dependency tree...SET@_progressbar1.pulse()

Reading state information...
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 300 not upgraded.
Need to get 119 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) natty/main boot-repair all 3.16-0ppa2~natty [119 kB]
Download complete and in download only mode
LIVESESSION is : yes (Ubuntu 11.04 , natty , Ubuntu , i686  )
BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.

OSPROBER:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda5:Ubuntu 11.04 (11.04):Ubuntu:linux

BLKID:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="System Reserved" UUID="5C8AC2C68AC29BC0" TYPE="ntfs"
/dev/sda2: UUID="EE80C76380C7313F" TYPE="ntfs"
/dev/sda5: UUID="9ed759f9-e94e-4c63-a08b-ac8eab1f782a" TYPE="ext4"
/dev/sda6: UUID="17598eaf-60cd-4cfe-ac65-510ebd631f4e" TYPE="swap"
/dev/sdb1: LABEL="PENDRIVE" UUID="B349-DE08" TYPE="vfat"

1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.
Total of 2 OS detected on sda disk.
TABLE_TYPE of sda is MSDos
sda1 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda1, with-os, no-gpt, notEFItable, no-fstab.
sda2 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda2, no-os, no-gpt, notEFItable, no-fstab.
sda5 : sda, not-sepboot, grub-install, grub2 , update-grub, apt-get, 32, with boot, /mnt/boot-sav/sda5, with-os, no-gpt, notEFItable, fstab-without-efi.

PARTED:

Model: ATA ST9160314AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  106MB   105MB   primary   ntfs            boot
2      106MB   80.1GB  80.0GB  primary   ntfs
3      80.1GB  160GB   80.0GB  extended
5      80.1GB  157GB   76.8GB  logical   ext4
6      157GB   160GB   3143MB  logical   linux-swap(v1)


Model: SKYMEDI USB Drive (scsi)
Disk /dev/sdb: 4007MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      31.7kB  4003MB  4003MB  primary  fat32        boot, lba


MOUNT:
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)


/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev:  agpgart autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem pktcdvd port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sda6 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 v4l vga_arbiter video0 zero
/dev/mapper:  control

DF:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    497M  138M  359M  28% /
none      devtmpfs    490M  684K  489M   1% /dev
/dev/sdb1     vfat    3.8G  1.4G  2.4G  37% /cdrom
/dev/loop0
squashfs    658M  658M     0 100% /rofs
none         tmpfs    497M  100K  496M   1% /dev/shm
tmpfs        tmpfs    497M   28K  497M   1% /tmp
none         tmpfs    497M  100K  496M   1% /var/run
none         tmpfs    497M     0  497M   0% /var/lock
/dev/sda1  fuseblk    100M   26M   75M  26% /mnt/boot-sav/sda1
/dev/sda2  fuseblk     75G   20G   55G  27% /mnt/boot-sav/sda2
/dev/sda5     ext4     71G   12G   56G  18% /mnt/boot-sav/sda5

FDISK:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009dea9

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   156392447    78092800    7  HPFS/NTFS
/dev/sda3       156393470   312580095    78093313    5  Extended
/dev/sda5       156393472   306440191    75023360   83  Linux
/dev/sda6       306442240   312580095     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 4006 MB, 4006608896 bytes
124 heads, 62 sectors/track, 1017 cylinders, total 7825408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7818695     3909317    c  W95 FAT32 (LBA)



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION yes (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB sda5, PART_TO_REINSTALL_GRUB_PURGE sda5, FORCE_GRUB no (sda) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sda2) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: connected

************************Actions
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION yes (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB sda5, PART_TO_REINSTALL_GRUB_PURGE sda5, FORCE_GRUB no (sda) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sda2) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
Reinstall the GRUB of sda5 into the MBR of sda
dpkg --configure -a sda5
grub-install (GRUB) 1.99~rc1-13ubuntu3
chroot: failed to run command `type': No such file or directory
INSTALLOUTPUT: Installation finished. No error reported.
INSTALLEXIT:0
Generating grub.cfg ...
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
ls: cannot access /mnt/boot-sav/sda2: No such file or directory
Found Windows 7 (loader) on /dev/sda1
Unhide GRUB boot menu in sda5/boot/grub/grub.cfg
internet: connected
pastebinit  packages needed
internet: connected
E: Package 'pastebinit' has no installation candidate
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
dpkg-preconfigure: unable to re-open stdin:

```

please help...

---

### Post by drs305 on 2012-02-11
For some reason the 10_linux section which normally creates your Ubuntu menu is missing from /boot/grub/grub.cfg.

There are several ways to fix this. The easiest is probably to just boot an Ubuntu LiveCD, mount your Ubuntu partition, open grub.cfg and paste in a standard Ubuntu menu entry. 

Boot a LiveCD/USB, get to an Ubuntu desktop and open a terminal.

```
sudo mount /dev/sda5 /mnt  # Mounts your Ubuntu partition.
gksu gedit +75 /mnt/boot/grub/grub.cfg # Opens your real Ubuntu's Grub menu at line 75.
```

This should open grub.cfg just before the 30_os-prober section. Paste in the following and save the file. Do NOT run 'update-grub'.

> ### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu 11.04' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 9ed759f9-e94e-4c63-a08b-ac8eab1f782a
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=9ed759f9-e94e-4c63-a08b-ac8eab1f782a ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-13-generic
}
### END /etc/grub.d/10_linux ###

Reboot and see if the Linux entry now appears and boots.

If it does, run this command to try to restore your 10_linux script:
```
sudo chmod +x /etc/grub.d/10_linux
```
If it runs and provides no output (no error messages), your system is probably fixed. You can now run this command to update the menu:
```
sudo update-grub
```
If you get errors, please post them.

Note in your previous post I inserted [noparse][```
 
```[/noparse] tags. These make the formatted code much easier to read. You can manually type the above and paste in between the tags, or you can generate the tags by pressing the # icon in the post's menu while creating the post.

---

### Post by noobshazbot on 2012-03-28
Hi - I need help. 
My son installed an update this morning and now Ubuntu wont boot. After reading a bit on this thread it looks like the same problem. Here is the boot info txt 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 30504 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   232,413,183   232,411,136  83 Linux
/dev/sda2         232,415,230   234,440,703     2,025,474   5 Extended
/dev/sda5         232,415,232   234,440,703     2,025,472  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8000 MB, 8000110592 bytes
255 heads, 63 sectors/track, 972 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    15,625,215    15,625,153   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        ae5f92f6-fb2d-4533-8610-53a67b5177ef   ext4       
/dev/sda5        16e5ba99-9850-4525-a40d-f0ec8be53a2e   swap       
/dev/sdb1        3827-E47A                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root ae5f92f6-fb2d-4533-8610-53a67b5177ef
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root ae5f92f6-fb2d-4533-8610-53a67b5177ef
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ae5f92f6-fb2d-4533-8610-53a67b5177ef
    linux    /boot/vmlinuz-3.0.0-17-generic root=UUID=ae5f92f6-fb2d-4533-8610-53a67b5177ef ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ae5f92f6-fb2d-4533-8610-53a67b5177ef
    echo    'Loading Linux 3.0.0-17-generic ...'
    linux    /boot/vmlinuz-3.0.0-17-generic root=UUID=ae5f92f6-fb2d-4533-8610-53a67b5177ef ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-17-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ae5f92f6-fb2d-4533-8610-53a67b5177ef
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=ae5f92f6-fb2d-4533-8610-53a67b5177ef ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ae5f92f6-fb2d-4533-8610-53a67b5177ef
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=ae5f92f6-fb2d-4533-8610-53a67b5177ef ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ae5f92f6-fb2d-4533-8610-53a67b5177ef
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ae5f92f6-fb2d-4533-8610-53a67b5177ef ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ae5f92f6-fb2d-4533-8610-53a67b5177ef
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=ae5f92f6-fb2d-4533-8610-53a67b5177ef ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ae5f92f6-fb2d-4533-8610-53a67b5177ef
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ae5f92f6-fb2d-4533-8610-53a67b5177ef
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ae5f92f6-fb2d-4533-8610-53a67b5177ef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=16e5ba99-9850-4525-a40d-f0ec8be53a2e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/initrd.img-3.0.0-16-generic               1
               =                boot/initrd.img-3.0.0-17-generic               3
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic                  2
               =                boot/vmlinuz-3.0.0-17-generic                  2
               =                vmlinuz                                        2
               =                vmlinuz.old                                    2

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  13 89 98 59 37 c6 7c 33  50 ad 9c 4c cd 03 8f a1  |...Y7.|3P..L....|
00000010  86 4a 3e 2b 73 b9 9c f3  52 2d 3e 0c f9 b2 4a 12  |.J>+s...R->...J.|
00000020  9a d6 75 8a 8e c8 52 7e  4a 4c 0d 2a d2 bb ce 62  |..u...R~JL.*...b|
00000030  40 6c ff 9a 0f c8 79 2e  d6 57 74 01 44 2d 6a 02  |@l....y..Wt.D-j.|
00000040  90 34 32 29 fc 3a 2c 2e  37 0f bc 02 24 7b c7 92  |.42).:,.7...${..|
00000050  21 1f 41 62 5e 14 19 36  74 12 ac 4b d1 39 00 0c  |!.Ab^..6t..K.9..|
00000060  09 cf f4 bd 13 69 5f 64  91 6e 7e 9a fe ff 11 3f  |.....i_d.n~....?|
00000070  71 7f 16 bc 9e 63 e7 d3  2b c7 cf fb fc cd 12 a5  |q....c..+.......|
00000080  27 93 ce 0f 08 88 57 53  0e 60 1d db ef 53 0c 61  |'.....WS.`...S.a|
00000090  dc c7 77 b6 05 78 48 aa  0e b2 6c 2a 44 cc f8 46  |..w..xH...l*D..F|
000000a0  83 d5 aa 77 b9 21 fc fd  42 40 20 ef 12 af 37 8d  |...w.!..B@ ...7.|
000000b0  e3 f0 fb b4 d3 d7 13 0c  2d 43 98 60 b2 e0 00 5e  |........-C.`...^|
000000c0  9b 07 02 8c 52 16 f0 0b  47 ee b5 bd a6 c2 3d c6  |....R...G.....=.|
000000d0  ab 10 10 5f 43 ba 03 d0  93 15 76 17 cf 6b e9 49  |..._C.....v..k.I|
000000e0  4f 72 59 2f 16 75 44 50  77 b2 6e 4f 0b fe 8c 06  |OrY/.uDPw.nO....|
000000f0  3a 0b 29 20 b6 7f a3 63  1b 9b 55 48 3d 2c b9 81  |:.) ...c..UH=,..|
00000100  55 fe a8 8a 5c 3a 10 33  41 48 7f 58 86 d6 50 c2  |U...\:.3AH.X..P.|
00000110  ca 9f 0d f1 91 f9 dc 7d  f1 b3 b4 62 1b a1 7b 87  |.......}...b..{.|
00000120  52 3f fd cc d6 80 a6 8e  42 a7 ec 66 ad 03 71 48  |R?......B..f..qH|
00000130  e6 6e df 9d 1f 57 40 49  25 4a d3 ac 29 f3 aa 1a  |.n...W@I%J..)...|
00000140  a8 db 1e 9b 77 7f d3 7d  9e 58 55 bf 8d a2 22 a9  |....w..}.XU...".|
00000150  53 27 e6 39 e9 5e 89 68  ec 35 99 fd f2 49 7c c6  |S'.9.^.h.5...I|.|
00000160  a5 ac dc 8b fe 7a af 18  09 4a 79 12 55 21 14 04  |.....z...Jy.U!..|
00000170  3e fd 1a b8 12 4c 29 09  59 a5 b7 d6 e1 dd c8 8f  |>....L).Y.......|
00000180  e2 84 12 7a b4 2a 7e 38  44 15 35 81 8a 95 d9 f9  |...z.*~8D.5.....|
00000190  71 c4 82 60 b4 d9 29 52  7a c3 79 98 a8 9e 72 1b  |q..`..)Rz.y...r.|
000001a0  53 3b e9 60 a6 2b 36 8d  32 32 4b 17 5c 60 3f 2a  |S;.`.+6.22K.\`?*|
000001b0  91 ed cd 18 65 42 bc 40  42 43 14 df b0 72 00 fe  |....eB.@BC...r..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 1e 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/bootinfo/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```Thanks in advance

---

