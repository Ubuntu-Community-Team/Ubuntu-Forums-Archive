---
title: "Grub doesn't show correct Ubuntu version after upgrade"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by fatboyfudge on 2010-05-09
Morning All,
 
I have a problem that I could do with some help with.
Yesterday I upgraded my Karmic Koala desktop to the new 10.04 LTS, all sempt to be going ok when I left it last night.
 
When I try to boot this morning Grub is showing the 9.04, kernel 2.6.28-11-generic instead of the 10.04 that I would have been expecting.  If I select the 9.04 option I the first message I get is:
 
mount: mounting none on /dev failed.
 
It thinks about it a bit then carries on, I sometimes get the 10.04 purple screen sometimes not.  Eventually I get to the text version of the login.
 
I upgraded through Ubuntu.
 
What have I done wrong, and how do I cure it?
 
I can't flatten it and start again because I have stuff on there that I really need to keep.
 
Thanks for your help in advance.

---

### Post by glennzo on 2010-05-09
First thing you should do is backup all that "stuff I really need to keep".

---

### Post by fatboyfudge on 2010-05-09
How do I back it up?  Only I'm not sure how to do it from the command prompt.

---

### Post by fatboyfudge on 2010-05-09
Ok, I've had a bit more of a tinker and I think I have made it worse.  I ran the sudo apt-get install ubuntu-desktop and it displayed a message that I needed to run sudo apt-get dpkg ....
 
It did its stuff and I rebooted, I now get the correct listings in the GRUB screen but it then sits there and after a bit I get:
 
Gave up waiting for root device.  Common Problems:
-Boot Args (cat /proc/cmdline)
  - Check rootdelay ....
  - Check root ...
- Missing Modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/some numbers does not exist.  Dropping to shell
 
BusyBox v1.13.3 ...
 
(initramfs)
 
So I would assume that I need to get the modules from somewhere and copy them in, where do I get them from?
 
Cheers

---

### Post by PocketDog on 2010-05-09
All that should be taken care of with ```
sudo update-grub
``` in a terminal. Does that not work?

---

### Post by ShadowMage on 2010-05-09
> **fatboyfudge said:**
> How do I back it up?  Only I'm not sure how to do it from the command prompt.
Or you could do it from a Live CD, assuming you'll still have somewhere to put the files while the Live CD is in your computer (e.g. USB drive or another optical drive). Hope this helps.

---

### Post by fatboyfudge on 2010-05-12
Ok here is the latest.
I can't run the sudo grub-update from the initramfs I get /bin/sh: sudo: not found.
The live CD loads ok but I can't get it do display the partitions on the sata drive, for this i tried sudo fdisk -l.
I tried the install from the Live CD and it didn't list any of my SATA drives so I could partition them.
This next bit probably won't help but I remember I had to add some extra bits into the command line in grub when I had installed 9.04 because it wouldn't see the hard disk.

---

### Post by kansasnoob on 2010-05-12
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You can use a Live CD if needed. That way we can see what's going on instead of guessing :)

---

### Post by fatboyfudge on 2010-05-17
> **kansasnoob said:**
> Please post the output of the Boot Info Script as described here:
 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
You can use a Live CD if needed. That way we can see what's going on instead of guessing :)
 
 
Hi sorry for the delay with the reply.  A log file would shed some light wouldn't it :).
I ran the boot_info_script055.sh from the link and this is what I got out of it (I've attached a copy of the file if that helps any).  I don't know if this will make any difference or not but I tried starting the windows installation from the grub menu and that just restarted the machine.
 
 
 
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 513 MB, 513802240 bytes
33 heads, 16 sectors/track, 1900 cylinders, total 1003520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             80     1,003,519     1,003,440   6 FAT16

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/sda1        2B99-9FED                              vfat                                     
/dev/sda: PTTYPE="dos" 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/2B99-9FED         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader  on sda1
00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 10 06 00  |.<.MSWIN4.1.....|
00000010  02 00 02 00 00 f8 f5 00  50 00 20 00 50 00 00 00  |........P. .P...|
00000020  b0 4f 0f 00 00 00 29 ed  9f 99 2b 4e 4f 20 4e 41  |.O....)...+NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|
00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|
00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U."..~..N......|
00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |....|.E...F..E.8|
00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}"....w.r...:f|
00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |..|f;..W.u.....V|
00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |....s.3..F...f..|
000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F....v.`.F|
000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |..V.. ....^...H.|
000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |..F..N.a....#.r9|
000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`....}..at9N|
000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t... ;.r.....}..|
000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.....t.<.t......|
00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |......}....}....|
00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f......}.}..E|
00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |..N....F..V.....|
00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.r....p..B.-`fj.|
00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j...t...3.|
00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |.v...v.B...v....|
00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |..........V$...d|
00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  [EMAIL="|.ar.@u.B.^.Iuw"]|.ar.@u.B.^.Iuw[/EMAIL]..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  [EMAIL="|.A....~...@...U"]|.A....~...@...U[/EMAIL].|
00000200

=======Devices which don't seem to have a corresponding hard drive==============
no block devices found

---

### Post by fatboyfudge on 2010-05-21
Fixed it.
Once I had got grub to show the correct version I had to add pci=nomsi apic into the kernel line.
Now for the network card.
:P

---

