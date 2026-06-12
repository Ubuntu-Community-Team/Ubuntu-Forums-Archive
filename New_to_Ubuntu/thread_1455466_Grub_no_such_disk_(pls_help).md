---
title: "Grub no such disk (pls help)"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by dacapo on 2010-04-16
Hi, I have a slight problem here.
I had a pretty good ubuntu inside windows xp set up going.
Then, today, I had the idea that I'd like to install ubuntu onto a spare external hdd I have.
Big mistake.. Now, my main hdd comes up with this "grub... no such disk" type of error.
I have gotten so far as to burn my super grub disk on a cd rom and finally boot back in.
But, I am stuck as to how I can restore my grub settings so I can boot this machine without having to use the SGD in my CD ROM drive.

Here also is the boot info script result:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=3a04ac98-26aa-4903-abea-a28ee37cdffb)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb7fdb7fd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,295,439   156,295,377   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe461a2f3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1         209,712,510   252,381,149    42,668,640   5 Extended
/dev/sdb5         209,712,573   250,517,609    40,805,037  83 Linux
/dev/sdb6         250,517,673   252,381,149     1,863,477  82 Linux swap / Solaris
/dev/sdb2                  63   209,712,509   209,712,447   b W95 FAT32
/dev/sdb3    *    252,381,150   312,576,704    60,195,555  af HFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       e0749447-549e-4625-8a76-9d0232388ad8   ext4                                     
/dev/sda1        90B85412B853F4E6                       ntfs                                     
/dev/sdb2        B969-15E6                              vfat       MEDIA                         
/dev/sdb3        658b8bbd-b805-3c17-9448-6e19130dd07d   hfsplus    MacOS                         
/dev/sdb5        3a04ac98-26aa-4903-abea-a28ee37cdffb   ext4                                     
/dev/sdb6        f963003d-f283-43ad-8b49-15e2dd9f2b94   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /host                    fuseblk    (rw)
/dev/sr0         /media/CDROM             iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu" 

======================== sda1/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 90b85412b853f4e6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 90b85412b853f4e6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 90b85412b853f4e6
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext4 loop,errors=remount-ro 0 1
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

================= sda1/Wubi: Location of files loaded by Grub: =================


   2.6GB: boot/grub/grub.cfg
   2.7GB: boot/initrd.img-2.6.31-14-generic
   2.4GB: boot/vmlinuz-2.6.31-14-generic
   2.7GB: initrd.img
   2.4GB: vmlinuz

=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set 3a04ac98-26aa-4903-abea-a28ee37cdffb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 3a04ac98-26aa-4903-abea-a28ee37cdffb
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3a04ac98-26aa-4903-abea-a28ee37cdffb ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 3a04ac98-26aa-4903-abea-a28ee37cdffb
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3a04ac98-26aa-4903-abea-a28ee37cdffb ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 90b85412b853f4e6
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Mac OS X (on /dev/sdb3)" {
    insmod hfsplus
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set 30834b8514fc9523
        insmod vbe
        do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 30834b8514fc9523 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devtree.txt ]; then
              xnu_devtree /Extra/devtree.txt
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=3a04ac98-26aa-4903-abea-a28ee37cdffb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=f963003d-f283-43ad-8b49-15e2dd9f2b94 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 109.0GB: boot/grub/core.img
 109.0GB: boot/grub/grub.cfg
 109.1GB: boot/initrd.img-2.6.31-14-generic
 108.9GB: boot/vmlinuz-2.6.31-14-generic
 109.1GB: initrd.img
 108.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e c0 8e d8 b0 48 e8  |.1............H.|
00000010  3d 01 66 8b 44 08 e8 54  01 66 31 c0 66 a3 00 e4  |=.f.D..T.f1.f...|
00000020  80 7c 04 af 75 03 e9 09  00 be a6 7d e8 10 01 e9  |.|..u......}....|
00000030  c2 00 b0 5d e8 18 01 b0  01 31 db 8e c3 bb 00 14  |...].....1......|
00000040  66 b9 02 00 00 00 e8 ae  00 73 03 e9 9b 00 a1 00  |f........s......|
00000050  14 3d 42 44 75 3f b0 7c  e8 f4 00 66 8b 1e 14 14  |.=BDu?.|...f....|
00000060  66 0f cb 66 c1 fb 09 66  31 c0 a1 7e 14 86 c4 52  |f..f...f1..~...R|
00000070  66 f7 e3 5a 66 31 db 8b  1e 1c 14 86 df 66 01 d8  |f..Zf1.......f..|
00000080  66 40 66 40 66 89 c1 b0  01 31 db 8e c3 bb 00 14  |f@f@f....1......|
00000090  e8 64 00 72 54 b0 7d e8  b5 00 a1 00 14 3d 48 2b  |.d.rT.}......=H+|
000000a0  74 05 3d 48 58 75 42 b0  2a e8 a3 00 66 a1 28 14  |t.=HXuB.*...f.(.|
000000b0  66 0f c8 66 c1 f8 09 66  8b 1e c0 15 66 0f cb 52  |f..f...f....f..R|
000000c0  66 f7 e3 5a 66 48 66 48  66 01 c1 b0 21 e8 7f 00  |f..ZfHfHf...!...|
000000d0  b0 7e bb 00 20 8e c3 bb  00 02 e8 1a 00 72 0a b0  |.~.. ........r..|
000000e0  59 e8 6b 00 ea 00 02 00  20 be bd 7d e8 50 00 b0  |Y.k..... ..}.P..|
000000f0  58 e8 5b 00 f4 eb fd 66  60 89 e5 1e 1e 66 03 0e  |X.[....f`....f..|
00000100  00 e4 66 03 4c 08 66 51  06 53 30 e4 50 50 b0 2d  |..f.L.fQ.S0.PP.-|
00000110  e8 3c 00 66 89 c8 e8 54  00 b0 3d e8 31 00 58 e8  |.<.f...T..=.1.X.|
00000120  4b 00 68 10 00 89 e6 b4  42 cd 13 73 0d e8 3d 00  |K.h.....B..s..=.|
00000130  b0 52 e8 1a 00 31 c0 cd  13 f9 89 ec 66 61 c3 bb  |.R...1......fa..|
00000140  01 00 fc ac 3c 00 74 06  b4 0e cd 10 eb f5 c3 66  |....<.t........f|
00000150  60 bb 01 00 b4 0e cd 10  66 61 c3 66 60 31 c9 88  |`.......fa.f`1..|
00000160  c1 b0 20 e3 05 e8 e7 ff  e2 f9 66 61 c3 66 60 b9  |.. .......fa.f`.|
00000170  04 00 66 0f c8 50 c0 c8  04 e8 17 00 58 e8 13 00  |..f..P......X...|
00000180  66 c1 c8 08 e2 ef b0 0a  e8 c4 ff b0 0d e8 bf ff  |f...............|
00000190  66 61 c3 24 0f 04 30 3c  39 76 02 04 07 e8 af ff  |fa.$..0<9v......|
000001a0  c3 b4 00 cd 16 c3 0a 0d  48 46 53 2b 20 70 61 72  |........HFS+ par|
000001b0  74 69 74 69 6f 6e 20 65  72 72 6f 72 00 0a 0d 45  |tition error...E|
000001c0  72 72 6f 72 20 6c 6f 61  64 69 6e 67 20 62 6f 6f  |rror loading boo|
000001d0  74 65 72 00 00 00 00 00  00 00 00 00 00 00 00 00  |ter.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```Someone, please help! Thanks!

---

### Post by Silent Warrior on 2010-04-16
I'll stress that I'm no expert - consider NOT doing anything I tell you, or at least testing at a time when you can remember/write down your changes and have the time to revert. But since there are no other replies...
I don't know what having two bootable HDDs will do for you (I might actually have a similar setup myself, not sure, but I don't have any such problems), but try changing all the references in the grub configuration-files from hd(0,1) to hd(1,1) - it is, after all on a different drive.
Remember to run update-grub after saving this change! (And to revert back if it doesn't work.)

---

### Post by dacapo on 2010-04-16
> **Silent Warrior said:**
> 
I don't know what having two bootable HDDs will do for you (I might actually have a similar setup myself, not sure, but I don't have any such problems), but try changing all the references in the grub configuration-files from hd(0,1) to hd(1,1) - it is, after all on a different drive.
Remember to run update-grub after saving this change! (And to revert back if it doesn't work.)

Thanks for the response.  Yeah, that's the part that confuses me.  I'm guessing that my attempt to install ubuntu on my external hdd actually didn't work and it somehow wrote to two different partitions(?) on my internal hdd?  

In any case, I'm really a noob here, so I'm not sure how I would be able to "change all the references in the grub configuration-files"?  Thanks for any advice.

---

### Post by kansasnoob on 2010-04-16
Can you boot into the Ubuntu on the external using SGD?

If yes run this command from terminal:

```
df
```

Look at this sample output:

```
lance@lance-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
**[COLOR="Red"]/dev/sda2[/COLOR]**              8649576   4053860   4156340  50% /
none                   1021872       320   1021552   1% /dev
none                   1026016       200   1025816   1% /dev/shm
none                   1026016        96   1025920   1% /var/run
none                   1026016         0   1026016   0% /var/lock
none                   1026016         0   1026016   0% /lib/init/rw
/dev/sda5              4617268    315776   4066952   8% /home
/dev/sda7             10388064   2420436   7439900  25% /mnt/sda7
/dev/sda8             21023124    148624  19806592   1% /mnt/sda8
/dev/sda9             21195728   8841536  11277440  44% /mnt/sda9
/dev/sda10            10866200     87468  10226920   1% /mnt/sda10

```

You see where I highlighted /dev/sda2? I think yours should show /dev/sdb5. Is that correct?

**If no then tell me so and do not proceed any further!**

**Only if yes** then run the following commands:

```
sudo grub-install /dev/sdb
```

If that returns any errors run:

```
sudo grub-install --recheck /dev/sdb
```

Then:

```
sudo update-grub
```

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

```
sudo apt-get remove lilo
```

Now if your BIOS is set to boot from USB before the internal hard drive you should be able to select which OS to boot when the USB drive is plugged in. And if the USB drive is not plugged in you should get the Wubi boot menu.

---

### Post by dacapo on 2010-04-16
> **kansasnoob said:**
> Can you boot into the Ubuntu on the external using SGD?



Thanks for the tips! I left my external hdd at home and am at work now, so I can try this later after lunch or something.  (Although, I don't recall being able to boot into the ubuntu on the external last night..)

But, I'm wondering, do I have to boot from the external hdd to do this? I can boot into my ubuntu on my internal hdd using SGD.. Only asking because I'm just itching to try it out now. :)

---

### Post by kansasnoob on 2010-04-16
Well, the last three commands are for restoring a Windows "readable" mbr to the internal drive (/dev/sda). To be honest I've never tried it from a Wubi install but it should work.

However the other "grub" commands are for installing grub to the mbr of the external and as written they'd only work if you're booted into the Ubuntu on /dev/sdb5.

I'll explain a bit just so you have a better understanding of grub and bootloaders in general. When we refer to an mbr we mean master boot record:

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

From your Boot Info:

> => **Grub 2 is installed in the MBR of /dev/sda** and looks for 
    (UUID=3a04ac98-26aa-4903-abea-a28ee37cdffb)/boot/grub.
 => **Windows is installed in the MBR of /dev/sdb**



And I can tell that XP w/Wubi is on /dev/sda1 and the Karmic install is on /dev/sdb5. By default grub installs to the mbr of /dev/sda unless you tell it different and when installing to external drives grub should be installed to the mbr of the external.

When you're installing using a live CD when you get to the last screen where it "reviews" your installation there's an Advanced "tab" in the lower right hand corner:

[http://members.iinet.net.au/%7Eherman546/p22/036.png](http://members.iinet.net.au/%7Eherman546/p22/036.png)

You should have chosen to install grub to **/dev/sdb**.

I should also take a moment to explain how Ubuntu "names" devices. Drives are numbered /dev/sda for drive #1, /dev/sdb for drive #2, etc. Partitions are numbered /dev/sda1 for drive #1 partition #1, /dev/sdb5 for drive #2 partition #5, etc. Clear as mud?

It's almost NEVER a good idea to install grub to a partition! Really bad things can happen :(

Anyway it's always good to know how to restore a Windows or grub mbr. This is a pretty good guide:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But Lilo, which is actually just another bootloader, can be used a handy tool for restoring a Windows "readable" mbr. You can always use it from any Ubuntu Live CD:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sd**[COLOR="Red"]X[/COLOR]** mbr
```

Note: the **[COLOR="Red"]X[/COLOR]** must be replaced with the proper drive designation, eg: "a", "b", etc.

If I use Lilo from an "installed" Ubuntu I always run "sudo apt-get remove lilo" when I'm done just so Lilo won't mess with the grub configuration at some point. It probably wouldn't anyway, but I like to play it safe :)

So I would think you could run the three commands:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
sudo apt-get remove lilo

```
from your Wubi installation, I've just never done it. It may be safer to just use a Live CD :)

As far as getting grub2 on the mbr of the external (/dev/sdb), if you can boot into the Ubuntu on the external you should just be able to run:

```
sudo grub-install /dev/sdb
```

Occasionally that will return errors, in which case you'd run:

```
sudo grub-install --recheck /dev/sdb
```

If you can't boot into the Ubuntu on the external you can follow the steps in the aforementioned guide for **How to restore the Ubuntu grub bootloader (9.10 and beyond)**. I have another "failsafe" method that I prefer. It involves mounting and "chrooting" the desired OS from a Live CD:

```
sudo mount /dev/sdb5 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sdb
```

And if needed:

```
grub-install --recheck /dev/sdb
```

Then exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Note: I used your proper drive and partition designations in that example.

Have I completely confused you yet?

---

### Post by dacapo on 2010-04-17
Kansasnoob!  
Wow, thanks so very very much!!!! I'm all set now... woohoo!
(I used the 3 lilo related commands to restore the mbr to sda.)

---

