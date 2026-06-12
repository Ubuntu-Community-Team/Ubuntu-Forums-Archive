---
title: "unknown filesystem"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by Gretzky82 on 2010-12-07
Hi i am a total beginner and i dont know much about ubuntu, but i was trying to uninstall ubuntu on my laptop and i removed wrong partition. And now when i turn on my laptop it says: unknown filesystem grub rescue. When i type in "ls" i see four options: (hd0) (hd0,msdos5) (hd0,msdos3) (hd0,msdos1). And i have no idea what to do, i have been searching on google but no matter what i do it says unknown filesystem. Please help thanks.

---

### Post by amjjawad on 2010-12-08
> **Gretzky82 said:**
> Hi i am a total beginner and i dont know much about ubuntu, but i was trying to uninstall ubuntu on my laptop and i removed wrong partition. And now when i turn on my laptop it says: unknown filesystem grub rescue. When i type in "ls" i see four options: (hd0) (hd0,msdos5) (hd0,msdos3) (hd0,msdos1). And i have no idea what to do, i have been searching on google but no matter what i do it says unknown filesystem. Please help thanks.

Hello and welcome :)

I assume you have Dual Boot with Windows, right? could you please provide us with more details?

Thank you :)

---

### Post by karthick87 on 2010-12-08
Post your results of [**Bootscript**]("http://bootinfoscript.sourceforge.net/")

---

### Post by sikander3786 on 2010-12-08
If the intention was to un-install Ubuntu, I suspect you deleted the correct partition. Thats why Grub is unable to boot.

If you want to keep Windows as the sole OS, you need to repair MBR for Windows and install its bootloader to get rid of Grub.

I would suggest to post the output of bootinfoscript as per instructions here. You need to boot and Ubuntu Live CD/USB for that.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us about your setup and therefore we'd be able to advise more efficiently.

Please wrap your output with proper code tags from post menu. Click the # icon and then paste your text in between the generated code tags.

---

### Post by Gretzky82 on 2010-12-08
Thanks for the replays. I was running Ubuntu along side Windows7 and i cant even get in to that. The reason i wanted to un-install Ubuntu was that i got some error when it started and told me to contact system admin. So i thought i could un-install it and the re-install it with out any problems, i guess that didnt work.
 But i did the boot script info and this is what i got:

 ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 21202944.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    21,202,294    21,200,247  27 Hidden HPFS/NTFS
/dev/sda2          21,202,942    27,265,023     6,062,082   5 Extended
/dev/sda5          21,202,944    27,265,023     6,062,080   7 HPFS/NTFS
/dev/sda3    *     27,265,024   625,139,711   597,874,688   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       24f918f2-bb58-4778-a2e0-80bbd6ce346e   ext4                                     
/dev/sda1        AE9ED3D49ED392E7                       ntfs       PQSERVICE                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        249CD5B89CD584A8                       ntfs       OS                            
/dev/sda5        A036648136645A74                       ntfs                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 249cd5b89cd584a8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 249cd5b89cd584a8
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ae9ed3d49ed392e7
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 249cd5b89cd584a8
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic-pae (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 317efa7f-76fd-4c18-9e8d-77cdb03c8be5
    linux /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=317efa7f-76fd-4c18-9e8d-77cdb03c8be5 ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 317efa7f-76fd-4c18-9e8d-77cdb03c8be5
    linux /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=317efa7f-76fd-4c18-9e8d-77cdb03c8be5 ro single
    initrd /boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

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

================= sda3/Wubi: Location of files loaded by Grub: =================


   4.4GB: boot/grub/grub.cfg
  15.3GB: boot/initrd.img-2.6.32-24-generic
  17.4GB: boot/vmlinuz-2.6.32-24-generic
  15.3GB: initrd.img
  17.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  e9 8a df d3 a1 d3 12 a9  53 d9 1f f4 27 ca a3 34  |........S...'..4|
00000010  4d 0f ed f4 61 00 ce b6  47 c6 d8 1e 99 f1 97 5d  |M...a...G......]|
00000020  4d 18 ba ed a1 b2 9b 2e  f8 16 e9 1a 97 46 75 84  |M............Fu.|
00000030  e9 7a b8 d6 ce 6a 91 aa  bf 36 8a ad 55 03 f7 77  |.z...j...6..U..w|
00000040  9a e3 8d de f7 a6 d3 57  d5 58 5a 68 4b 60 f5 f8  |.......W.XZhK`..|
00000050  7b 9a 0a c3 bd 7e 99 ed  c7 10 07 3f a7 12 cf 89  |{....~.....?....|
00000060  36 2f d0 56 51 27 ca c7  d5 75 73 f4 98 b8 82 11  |6/.VQ'...us.....|
00000070  c3 1a 97 2e 70 4b ee 63  d2 77 5a af 20 56 1e 92  |....pK.c.wZ. V..|
00000080  ab b7 46 b2 e8 11 78 21  1c c2 99 f1 e1 2d 9a 06  |..F...x!.....-..|
00000090  c8 38 e1 f8 e3 9b 0e 83  53 37 11 a8 d7 65 4d 36  |.8......S7...eM6|
000000a0  9b 89 3e ae 37 21 06 35  39 04 ac b5 22 71 af 36  |..>.7!.59..."q.6|
000000b0  a6 d0 b4 23 e6 76 1a d9  18 b3 26 63 eb 74 d1 fc  |...#.v....&c.t..|
000000c0  c9 fd bc 84 c2 bd 85 76  21 4b 8c e7 a7 7e 4b 31  |.......v!K...~K1|
000000d0  7e bb 1b 3e 3e ee d3 37  ec 3c cb 61 96 f0 ec 1a  |~..>>..7.<.a....|
000000e0  ea e3 1d 43 16 35 40 eb  f3 74 e6 f7 73 73 02 9c  |...C.5@..t..ss..|
000000f0  85 c4 2e 4a 33 cd 3a 1c  b4 d0 81 02 11 7c 40 e0  |...J3.:......|@.|
00000100  07 08 82 50 40 c2 10 10  06 2a 40 70 10 04 84 21  |...P@....*@p...!|
00000110  24 0c 61 68 08 81 43 22  18 8e 40 30 11 02 8a 24  |$.ah..C"..@0...$|
00000120  40 26 86 50 11 04 8b 31  5c c6 70 19 03 b0 04 83  |@&.P...1\.p.....|
00000130  c6 04 1b c7 c0 42 02 10  19 81 28 88 03 e0 38 04  |.....B....(...8.|
00000140  74 ec 40 00 0f 09 f4 f0  01 82 1f 13 00 10 04 02  |t.@.............|
00000150  42 86 80 30 10 38 39 8e  82 40 07 07 78 48 a0 80  |B..0.89..@..xH..|
00000160  0f 10 fc 98 00 81 40 0a  08 18 02 c2 40 05 08 0a  |......@.....@...|
00000170  42 70 10 10 2c 84 80 28  84 02 11 10 16 c4 c0 14  |Bp..,..(........|
00000180  81 c1 21 04 0f 88 60 44  04 40 22 11 8e 8a 30 40  |..!...`D.@"...0@|
00000190  02 84 24 31 54 4a 40 54  0c 60 31 04 8b 31 5c 4b  |..$1TJ@T.`1..1\K|
000001a0  80 c0 04 06 8c 18 38 63  e8 1c c1 e8 08 83 47 0c  |......8c......G.|
000001b0  23 24 90 27 c1 41 05 d6  79 aa 6f d7 71 46 00 fe  |#$.'.A..y.o.qF..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 80 5c 00 00 00  |............\...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb  
```I hope this tells you guys something :)
Thanks very much

---

### Post by sandyd on 2010-12-08
Windows 7 : [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Windows Vista : [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Use one of the above (according to your windows OS), or your windows recovery disc.

Make sure you don't have any USB drives connected; it won't work if you do.

Choose "Startup Repair"

if that doesn't work, check out #3 of [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by Patrick R Curry on 2010-12-08
I ran into that a few times,,  although new to ubuntu,, i have  done several other flavors;;; some flavors if they can not acess a hd will boot os to memory;;; and on some note books dose not work so well;;; you will get a limited  shell... your best bet I thiink is to reinstall... could be the hd was never formated...

---

### Post by bcbc on 2010-12-08
Looks like you had Ubuntu on /dev/sda5 but formatted it as ntfs. So all you need to do is install the windows bootloader or lilo to get Windows to boot (as grub is still in the MBR pointing at /dev/sda5). You also have a wubi install which looks like it's still active (it has boot entries for the old install on /dev/sda5).

To install the windows bootloader boot to a repair prompt and run:
bootrec.exe /fixmbr

You can also use lilo from a live CD (ignore big warnings related to booting linux, not windows):
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

### Post by Gretzky82 on 2010-12-08
Thank you guys so much i got it runing now :D

---

