---
title: "Can't boot windows without external hard drive"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by bvirus on 2011-07-23
Ok when i tryed to install linux on my external hard drive so i could boot from it the installation went compleatly fine. however when i tryed to boot into windows after the installation i couldn't boot into anything unless i have my external hard drive plugged in. If i dont i get a grub error and the computer can't boot. i woul like it if anyoone could tell me a way i could fix this without loosing all the files on my internal hard drive. Thanks

---

### Post by Quackers on 2011-07-23
Welcome to UF.
It sounds like you didn't change the destination for the installation of grub. By default it goes to /dev/sda, which is likely to be your Windows drive.

From within the Ubuntu desktop please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by amjjawad on 2011-07-24
> **bvirus said:**
> Ok when i tryed to install linux on my external hard drive so i could boot from it the installation went compleatly fine. however when i tryed to boot into windows after the installation i couldn't boot into anything unless i have my external hard drive plugged in. If i dont i get a grub error and the computer can't boot. i woul like it if anyoone could tell me a way i could fix this without loosing all the files on my internal hard drive. Thanks

Hello and Welcome :)

I think you're in safe hands with Quackers so good luck :)

---

### Post by oldfred on 2011-07-24
Post boot script as requested by Quacker to confirm, but this is often the problem. This site is by one of the authors of the boot script as common fixes.

Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by beew on 2011-07-24
I think you have installed grub into the internal drive (sda). So you can't boot into Windows without the external drive plugged in but the other side of the coin is that you wouldn't be able to boot from the external drive if you plug it into a different computer from the one with which you installed Ubuntu.

You need to do two things.

1) Reinstall the mbr into the Windows partition. This can be done easily if you have the Win install CD but the procedure is a bit different for different versions of Win. With XP you just boot into the install CD and when prompted choose repair existing Windows install and then type fixmbr, then exit, remove the Cd and reboot. I don't know the exact procedures for Vista and Win7, never use them.

2)Install grub back into the external drive. 
Boot into a Ubuntu live usb or live CD. Then connect your external drive and run the boot script to find out the name of the Ubuntu boot partition installed in the external drive (let's say you boot from a live usb then the external drive is probably sdc,--sda the internal drive, sdb the live usb, if you boot from a CD then it would probably be sdb, the partition where Ubuntu is installed is probably sdc1)

Let's say you have found that Ubuntu is installed in sdc1. Open the terminal (still in live usb) and run the commands

```
[FONT=monospace]sudo mount /dev/sdc1 /mnt[/FONT]

sudo grub-install --root-directory=/mnt /dev/sdc

```Then boot into the Ubuntu install in the external drive and run 
```
sudo update-grub
```Now you should be able to boot off the external drive by plugging it into other machines as well (ie it is portable)

---

### Post by bvirus on 2011-07-30
> **Quackers said:**
> Welcome to UF.
It sounds like you didn't change the destination for the installation of grub. By default it goes to /dev/sda, which is likely to be your Windows drive.

From within the Ubuntu desktop please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


Thanks for responding so fast i had an unexpectedly busy week and was unable to check back. I did what you said and here is the contents of the results.txt


>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
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
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   931,987,455   931,577,856   7 NTFS / exFAT / HPFS
/dev/sda3         931,987,456   976,560,127    44,572,672   7 NTFS / exFAT / HPFS
/dev/sda4         976,560,128   976,771,119       210,992   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.1 GB, 750127153152 bytes
255 heads, 63 sectors/track, 91197 cylinders, total 1465092096 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,428,230,143 1,428,228,096  83 Linux
/dev/sdb2       1,428,232,190 1,465,090,047    36,857,858   5 Extended
/dev/sdb5       1,428,232,192 1,465,090,047    36,857,856  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        B61A0FCD1A0F8A17                       ntfs       SYSTEM
/dev/sda2        52E4659AE4658159                       ntfs       
/dev/sda3        DCB66DF0B66DCC18                       ntfs       RECOVERY
/dev/sda4        D294-E827                              vfat       HP_TOOLS
/dev/sdb1        2e3e9150-6e69-4fb5-a28c-a55293f61f36   ext4       
/dev/sdb5        e46c8748-2c2f-4a7a-bbac-260435612018   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 2e3e9150-6e69-4fb5-a28c-a55293f61f36
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 2e3e9150-6e69-4fb5-a28c-a55293f61f36
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
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 2e3e9150-6e69-4fb5-a28c-a55293f61f36
    linux    /boot/vmlinuz-2.6.35-30-generic-pae root=UUID=2e3e9150-6e69-4fb5-a28c-a55293f61f36 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 2e3e9150-6e69-4fb5-a28c-a55293f61f36
    echo    'Loading Linux 2.6.35-30-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-30-generic-pae root=UUID=2e3e9150-6e69-4fb5-a28c-a55293f61f36 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 2e3e9150-6e69-4fb5-a28c-a55293f61f36
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 2e3e9150-6e69-4fb5-a28c-a55293f61f36
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b61a0fcd1a0f8a17
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 52e4659ae4658159
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set dcb66df0b66dcc18
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 668.140979767 = 717.410914304  boot/grub/core.img                             1
 652.179019928 = 700.271890432  boot/grub/grub.cfg                             1
   0.594726562 = 0.638582784    boot/initrd.img-2.6.35-30-generic-pae          2
 668.136985779 = 717.406625792  boot/vmlinuz-2.6.35-30-generic-pae             1
   0.594726562 = 0.638582784    initrd.img                                     2
 668.136985779 = 717.406625792  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 ce 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 35 3a  |........?.... 5:|
00000020  30 38 03 00 19 03 00 00  00 00 00 00 02 00 00 00  |08..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 27 e8 94 d2 4e  4f 20 4e 41 4d 45 20 20  |..)'...NO NAME  |
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

Unknown BootLoader on sdb2

00000000  b5 16 b8 72 c2 38 a4 21  d6 65 4a 72 0e 78 32 14  |...r.8.!.eJr.x2.|
*
000001b0  b5 16 b8 72 c2 38 a4 21  d6 65 4a 72 0e 78 00 fe  |...r.8.!.eJr.x..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 68 32 02 00 00  |...........h2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




---

### Post by idoitprone on 2011-07-30
> **bvirus said:**
> => Grub2 (v1.97-1.9:cool: is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.

sdb1: __________________________________________________  ________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


Your boot script looks strange with that grub is installed on sda but looks for sector 1 one the same hardrive

I believe the route of the least hassle is this

First boot to ubuntu and install grub on your linux hard drive

```
sudo grub-install /dev/sdb
```shutdown then
Unplug you linux harddrive and rescue the windows boot loader

Now both harddrives can boot independently
All you have to do is change the prioty in the bios which harddrive boot first

Note: I am not sure how bios device numbering works if the device prioty changes. If it does then we have to change grub.
If you are unable to boot linux after changing device proty then we have to do the command

```
sudo update-grub
```
press e at the grub menu and edit the number in the boot menu from root='(hd1,msdos1)' to root='(hd0,msdos1)'
booted into grub type 
```
sudo update-grub
```

---

### Post by oldfred on 2011-07-31
When you change the boot drive you may  also need to update the reinstall location.

Grub saves a  location that it is install to and reinstalls to that location. So if  you change drives, you also need to update the saved location.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
                                                                                               __________________

---

