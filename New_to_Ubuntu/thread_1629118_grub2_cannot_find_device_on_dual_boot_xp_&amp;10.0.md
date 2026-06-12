---
title: "grub2 cannot find device on dual boot xp &amp;10.04 , aftr update"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by klimtelfe on 2010-11-23
A little history
[SIZE=1]I have an 32bit intel based laptop that was running xp. It blue screened so I figured it would be the perfect time to try a linux. So I made partitions (40 + 17 ) and put xp on the former and ubuntu LTS 10.04 on the second. The system worked perfectly till...[/SIZE]
[SIZE=2]
this last update If I remember correctly was grub related. It asked me to continue install without installing something else. (I remember now there being a small checkbox which I didnt check) Anyways..I reboot and the system, wont boot either xp or linux -

Initially it gave error unable to recongize device and gave the grub rescue prompt. I looked through the forums and tried a bunch of things[/SIZE] (update, reinstall, rescatux, subergrub2 disk ). The last time it said install complete no errors. NOW it says that no such file found. I was wondering if:

1. there is an obvious quick fix that can salvage / autocorrect this?
2. Can I simly uninstall and do a clean install that will find the changes?
3. I noticed (before it stopped working) that windoze add/remove list has ubuntu in its list of programs and it seems (even though I havent tried) you can remove everything like you would with a program. BUT I cant access personal files on the desktop, other folders. Hence I dont know how to back those before I nuke the linux partition
3.5 All the files are stored in root.disk ( I figure because that is practically the only file there 8gb big, there is also swap. disk but too small) SO is there a way to open it using terminal and copy out those files?

PLease help!

---

### Post by klimtelfe on 2010-11-23
Oh and I am pretty much a newbie. I can follow commands written here, but dont fully understand file/ installation structures hence my file paths and commands might be incorrect. :D

---

### Post by sikander3786 on 2010-11-23
Welcome to the forums :popcorn:

In order to let us know more about your current setup, please boot an Ubuntu Live CD and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Post your output here and wrap it using proper code tags # from the post menu. [ code] at the beginning and [ /code] at the end.

Thanks.

---

### Post by klimtelfe on 2010-11-23
I was not sure if you needed all of the results file, but I have attached the txt as well. ALso there was an external HD and a jump drive plugged in at time of run. Thnx



```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /ubuntu/disks/boot/grub/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

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
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 245.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    77,818,859    77,818,797   7 HPFS/NTFS
/dev/sda2          77,818,860   117,194,174    39,375,315   f W95 Ext d (LBA)
/dev/sda5          77,818,923   110,591,459    32,772,537   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders, total 2001888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *            245     1,999,871     1,999,627   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       88195e3a-d9fc-49a2-8dcc-b07d8f90dea7   ext4                                     
/dev/sda1        D230826F308259FD                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        822CECF82CECE85D                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        380493400492FFD4                       ntfs       Iomega HDD                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        6A13-B80B                              vfat       jujubee                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Iomega HDD        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/jujubee           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

======================== sda5/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 822cecf82cece85d
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 822cecf82cece85d
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 822cecf82cece85d
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 822cecf82cece85d
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 822cecf82cece85d
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 822cecf82cece85d
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d230826f308259fd
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda5/Wubi: Location of files loaded by Grub: =================


    .4GB: boot/grub/core.img
   2.8GB: boot/grub/grub.cfg
   2.0GB: boot/initrd.img-2.6.32-24-generic
   2.2GB: boot/initrd.img-2.6.32-25-generic
   1.6GB: boot/vmlinuz-2.6.32-24-generic
    .9GB: boot/vmlinuz-2.6.32-25-generic
   2.2GB: initrd.img
   2.0GB: initrd.img.old
    .9GB: vmlinuz
   1.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  f0 d4 b0 16 b0 4a d3 d7  78 88 64 49 78 58 9a d3  |.....J..x.dIxX..|
00000010  fa a5 5c b1 ea 47 05 b1  c8 29 cc c6 0e e0 e0 36  |..\..G...).....6|
00000020  01 8a f6 99 67 24 8a 29  fa 66 b1 20 94 d9 cc b8  |....g$.).f. ....|
00000030  a0 39 a1 23 84 7a 89 41  df 25 7f 4b 11 ef 3b 71  |.9.#.z.A.%.K..;q|
00000040  ae 9e c6 22 ba 09 06 48  d8 75 1d 41 5c 42 4a cb  |..."...H.u.A\BJ.|
00000050  c6 98 aa 45 d0 63 f7 41  bc c2 12 8c 9b 63 75 94  |...E.c.A.....cu.|
00000060  be b9 55 24 1b c8 c9 3e  76 39 df 30 93 aa f5 f3  |..U$...>v9.0....|
00000070  f2 55 cb 68 f5 8f 2f c1  ea 0c 6f f3 5f a0 26 ff  |.U.h../...o._.&.|
00000080  e8 d6 fd 2c 6e 26 c3 a9  7d 3b bc a3 15 ca da b9  |...,n&..};......|
00000090  fd be 66 58 b1 3b dd 03  29 29 96 46 c2 ee 2b 40  |..fX.;..)).F..+@|
000000a0  81 ec be 37 33 ca a0 23  a6 d9 95 2c a5 b1 9a 4f  |...73..#...,...O|
000000b0  01 71 5a 94 90 a4 1e 21  f1 15 31 47 e6 95 3b 56  |.qZ....!..1G..;V|
000000c0  dc ad 2a c2 66 f6 8a cf  4d 76 dc 8d 77 42 fa a4  |..*.f...Mv..wB..|
000000d0  d6 8f 38 e2 78 5e c0 06  e6 56 e6 f6 9d fa 63 f2  |..8.x^...V....c.|
000000e0  bb be c0 0f b9 11 fb 68  3b 83 44 eb 53 33 ac ca  |.......h;.D.S3..|
000000f0  d6 e9 2d 23 fe 87 60 75  c0 b2 f9 04 06 e5 75 76  |..-#..`u......uv|
00000100  20 d5 1d 33 19 66 f1 b7  fd d7 23 37 b0 c6 68 db  | ..3.f....#7..h.|
00000110  21 89 5f 6f dd 9c 24 e8  9e 75 4a b5 6f 7b 44 b2  |!._o..$..uJ.o{D.|
00000120  1e 91 b0 b1 05 59 24 8e  5b 99 17 9b fe f4 f3 ef  |.....Y$.[.......|
00000130  6b fe 7e 01 f5 83 dd d1  11 b7 7f 6f 84 82 ea f8  |k.~........o....|
00000140  eb 7b 6c d2 06 df 88 63  11 06 b7 06 a2 97 b3 a0  |.{l....c........|
00000150  7f b2 7c 48 96 10 8d a6  39 39 96 cd 9d a9 0a 67  |..|H....99.....g|
00000160  88 6d da f4 77 68 26 b6  5a 55 95 8f ac 9b e4 d7  |.m..wh&.ZU......|
00000170  2e 1e dc da 7a d9 b5 8a  95 61 93 e6 1b 29 c6 ac  |....z....a...)..|
00000180  c6 d8 0a 1b 2b c5 f8 80  5f 18 15 97 b9 fd 11 69  |....+..._......i|
00000190  9f 15 f9 c5 5d 9f 91 5f  28 32 c7 b3 f2 ba 73 ec  |....].._(2....s.|
000001a0  10 b2 16 bd 51 d4 82 fd  31 77 24 82 88 4b 36 a7  |....Q...1w$..K6.|
000001b0  a6 30 65 69 82 fb a6 eb  eb d4 34 cd e2 5f 00 01  |.0ei......4.._..|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 b9 11 f4 01 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by klimtelfe on 2010-11-23
with my last attempt to correctly install caused this ugliness  = boot/grub/boot/grub

```
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /ubuntu/disks/boot/grub/boot/grub.

```

---

### Post by Quackers on 2010-11-23
You do not have a true dual boot system, you have a wubi installation (Ubuntu inside Windows).
There have been a lot of problems after updating wubi installs lately. I'm sure googling will bring up something. Alternatively there is a wubi specialist around here somewhere and I'm sure he'll be along at some time :-)

---

### Post by klimtelfe on 2010-11-23
You know..I suspected it all along. Even pointers to extracting personal files from root.disk so that I can try again would help immensely!

---

### Post by drs305 on 2010-11-23
You can access you Wubi files with the following. Your partitions are messed up but hopefully you can mount the Windows sda5 and retrieve the files:

```

sudo mkdir /mnt/windows /mnt/wubi && sudo chown -R $USER: /mnt/wubi /mnt/windows
sudo mount /dev/sda5 /mnt/windows && sudo mount -o loop  /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
nautilus /mnt/wubi

```

---

### Post by klimtelfe on 2010-11-23
Thank you very much!  I was able to extract the home directory files just fine. Some other folders/ sub folders were restricted. Any recommendations on a different partition setup? I'll try and avoid wubi if I end up reinstalling. 

Generally speaking 10.04 is long term support as opposed to 10.10 so would that be a better option in terms of sturdiness ( for a beginner looking to learn)?

> **drs305 said:**
> You can access you Wubi files with the following. Your partitions are messed up but hopefully you can mount the Windows sda5 and retrieve the files:

```

sudo mkdir /mnt/windows /mnt/wubi && sudo chown -R $USER: /mnt/wubi /mnt/windows
sudo mount /dev/sda5 /mnt/windows && sudo mount -o loop  /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
nautilus /mnt/wubi

```

---

### Post by bcbc on 2010-11-24
Did you ever fix this? In order to get both os's booting you need to just install the windows bootloader (run 'fixmbr' from a windows repair command line). Post back if you still need help.

---

### Post by Quackers on 2010-11-24
> **Quackers said:**
> Alternatively there is a wubi specialist around here somewhere and I'm sure he'll be along at some time :-)

There he is :-) /\ /\ /\ /\

---

### Post by klimtelfe on 2010-11-25
> **bcbc said:**
> Did you ever fix this? In order to get both os's booting you need to just install the windows bootloader (run 'fixmbr' from a windows repair command line). Post back if you still need help.

Ah awesome, thanks:D! That worked very well. I am going to try to do a regular install since wubi seems to have issues.

---

### Post by bcbc on 2010-11-25
> **klimtelfe said:**
> Ah awesome, thanks:D! That worked very well. I am going to try to do a regular install since wubi seems to have issues.

Great! Glad you got that sorted out. 

Yes Wubi has some issues - to be more precise, it's grub+wubi causing most of the problems. Ironically I believe this latest grub update was specifically for wubi installs - a cosmetic update that didn't have any noticeable purpose, and it's caused nothing but problems. 

My personal recommendation is to install direct to partition if you're able. For those that cannot and choose Wubi, it's best to avoid updating packages grub-pc and grub-common.

---

