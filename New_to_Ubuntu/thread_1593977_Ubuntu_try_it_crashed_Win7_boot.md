---
title: "Ubuntu try it crashed Win7 boot"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by rmadams1 on 2010-10-11
I downloaded 10.10 this afternoon to a boot stick and was checking out the try it on my Win7 work laptop. Somehow I've managed to hose things up, because now my laptop won't boot to anything but Ubuntu. I've installed 9.10 so I'm familiar with the install process and I didn't do anything even close to that. I can still see the Win7 OS file structure from 10.10, so I figure my boot files are corrupted. (Or improved depending on your pov :) ). 
 
In any case since this is my work computer I need to get this back to Win7. Is there a way to get this back to even giving me an option to boot win7 without blowing out the hdd and starting over?

---

### Post by BrockStrongo on 2010-10-11
It is possible that grub got messed up? if the windows partition is still intact you may wanna try reinstalling grub from a live cd or usb.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
There are a lot of how to's out there if this one doesn't make sense.
Hope this is of some assistance, if not, sorry
Cheers

---

### Post by rogueleader12345 on 2010-10-11
you mean a usb stick/flash drive? check your boot order, it's probably still booting off of the stick rather than the hdd. i've done that a few times

---

### Post by rmadams1 on 2010-10-11
I've gone in and ckd the boot order and its going to the hdd. The stick isn't even in the box and I'm booting to the try it or install it splash. 
 
I hope the grub link can help me save the data. I'm backing up some stuff to usb before I mess around any further.

---

### Post by BrockStrongo on 2010-10-11
[http://ubuntuforums.org/showthread.php?t=1437155](http://ubuntuforums.org/showthread.php?t=1437155)
here some more info on restoring grub in case you get stuck.

---

### Post by rmadams1 on 2010-10-11
I d/l'd the bootinfo tool and this is what I've got.
 
Boot Info Script 0.55 dated February 15th, 2010 
============================= Boot Info Summary: ==============================
=> Syslinux is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: /bootmgr /Boot/BCD
sda2: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe
sda3: _________________________________________________________________________
File system: vfat
Boot sector type: Unknown
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition Boot Start End Size Id System
/dev/sda1 2,048 2,459,647 2,457,600 7 HPFS/NTFS
/dev/sda2 2,459,648 467,914,743 465,455,096 7 HPFS/NTFS
/dev/sda3 * 467,914,752 488,394,751 20,480,000 c W95 FAT32 (LBA)
 
blkid -c /dev/null: ____________________________________________________________
Device UUID TYPE LABEL 
/dev/loop0 squashfs 
/dev/sda1 46025BD9025BCC95 ntfs SYSTEM_DRV 
/dev/sda2 5A785E8F785E69B1 ntfs Windows7_OS 
/dev/sda3 B0F7-80E3 vfat PENDRIVE 
/dev/sda: PTTYPE="dos" 
============================ "mount | grep ^/dev output: ===========================
Device Mount_Point Type Options
aufs / aufs (rw)
/dev/sda3 /cdrom vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 /rofs squashfs (ro,noatime)
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader on sda3
00000000 eb 58 90 53 59 53 4c 49 4e 55 58 00 02 10 f6 11 |.X.SYSLINUX.....|
00000010 02 00 00 00 00 f8 00 00 3f 00 f0 00 00 d0 e3 1b |........?.......|
00000020 00 80 38 01 05 27 00 00 00 00 00 00 02 00 00 00 |..8..'..........|
00000030 01 00 06 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
00000040 80 00 29 e3 80 f7 b0 4e 4f 20 4e 41 4d 45 20 20 |..)....NO NAME |
00000050 20 20 46 41 54 33 32 20 20 20 fa fc 31 c9 8e d1 | FAT32 ..1...|
00000060 bc 76 7b 52 06 57 8e c1 b1 26 bf 78 7b f3 a5 8e |.v{R.W...&.x{...|
00000070 d9 bb 78 00 0f b4 37 0f a0 56 20 d2 78 1b 31 c0 |..x...7..V .x.1.|
00000080 b1 06 89 3f 89 47 02 f3 64 a5 8a 0e 18 7c 88 4d |...?.G..d....|.M|
00000090 bc 50 50 50 50 cd 13 eb 4b f6 45 b4 7f 75 25 38 |.PPPP...K.E..u%8|
000000a0 4d b8 74 20 66 3d 21 47 50 54 75 10 80 7d b8 ed |M.t f=!GPTu..}..|
000000b0 75 0a 66 ff 75 ec 66 ff 75 e8 eb 0f 51 51 66 ff |u.f.u.f.u...QQf.|
000000c0 75 bc eb 07 51 51 66 ff 36 1c 7c b4 08 cd 13 72 |u...QQf.6.|....r|
000000d0 13 20 e4 75 0f c1 ea 08 42 89 16 1a 7c 83 e1 3f |. .u....B...|..?|
000000e0 89 0e 18 7c fb bb aa 55 b4 41 8a 16 74 7b cd 13 |...|...U.A..t{..|
000000f0 72 10 81 fb 55 aa 75 0a f6 c1 01 74 05 c6 06 32 |r...U.u....t...2|
00000100 7d 00 66 b8 b0 0d 16 00 66 ba 00 00 00 00 bb 00 |}.f.....f.......|
00000110 7e e8 10 00 66 81 3e 24 7e 34 be f5 72 75 76 ea |~...f.>$~4..ruv.|
00000120 38 7e 00 00 66 03 06 64 7b 66 13 16 68 7b b9 10 |8~..f..d{f..h{..|
00000130 00 eb 2b 66 52 66 50 06 53 6a 01 6a 10 89 e6 66 |..+fRfP.Sj.j...f|
00000140 60 b4 42 e8 7f 00 66 61 8d 64 10 72 01 c3 66 60 |`.B...fa.d.r..f`|
00000150 31 c0 e8 70 00 66 61 e2 da c6 06 32 7d 2b 66 60 |1..p.fa....2}+f`|
00000160 66 0f b7 36 18 7c 66 0f b7 3e 1a 7c 66 f7 f6 31 |f..6.|f..>.|f..1|
00000170 c9 87 ca 66 f7 f7 66 3d ff 03 00 00 77 17 c0 e4 |...f..f=....w...|
00000180 06 41 08 e1 88 c5 88 d6 b8 01 02 e8 37 00 66 61 |.A..........7.fa|
00000190 72 01 c3 e2 c9 31 f6 8e d6 bc 6c 7b 8e de 66 8f |r....1....l{..f.|
000001a0 06 78 00 be cc 7d e8 09 00 31 c0 cd 16 cd 19 f4 |.x...}...1......|
000001b0 eb fd 66 60 ac 20 c0 74 09 b4 0e bb 07 00 cd 10 |..f`. .t........|
000001c0 eb f2 66 61 c3 8a 16 74 7b cd 13 c3 42 6f 6f 74 |..fa...t{...Boot|
000001d0 20 65 72 72 6f 72 0d 0a 00 00 00 00 00 00 00 00 | error..........|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200
 
Honestly, not sure where to go from here....

---

### Post by MooPi on 2010-10-11
What is in the CD-rom tray ?

---

### Post by rmadams1 on 2010-10-11
> **MooPi said:**
> What is in the CD-rom tray ?
 
It's empty.
 
ETA: The Win 7 did have a virtual cd installed. I'd hope that wouldn't hang on through this  though?

---

### Post by Quackers on 2010-10-11
Boot from your Windows repair disc/system disc/recovery disc and choose repair your computer. It probably won't fix it but then go to the command prompt and type
bootrec.exe /fixmbr and hit enter    then type
bootrec.exe /fixboot and hit enter.
Reboot and hopefully Windows will boot again.

---

### Post by Quackers on 2010-10-11
Was your pendrive plugged in when you ran the boot script?

---

### Post by rmadams1 on 2010-10-11
> **Quackers said:**
> Was your pendrive plugged in when you ran the boot script?
 
Yep. Sorry -

---

### Post by Quackers on 2010-10-11
No problem. Have a look at post #9 and see if you can get Windows back.

---

### Post by rmadams1 on 2010-10-11
Trying it now.....

---

### Post by rmadams1 on 2010-10-11
Getting a BOOTMGR is missing. Arguing with it a bit more. I may have it.

---

### Post by Quackers on 2010-10-11
Right, run the repair disc again and go to the command prompt and type bootrec.exe /rebuildbcd and hit enter.
If that runs ok you will get the option to add a Windows system to add the entry to the boot store, type y for yes.
Reboot and try again.
If that doesn't work get back to us

---

### Post by oldfred on 2010-10-11
This may be your problem, move the boot flag to sda2 as that looks like your main install. That partition does have bootmgr but the windows boot loader uses the boot flag to find the partition to boot.

You can use gparted or disk utility from the liveCD to set boot flag. Only one flag per drive on a primary partition. Windows uses it to know what partition to boot. Grub does not use it. Some BIOS require it on a primary partition or they will not let you even start to boot.

---

### Post by Quackers on 2010-10-11
Oldfred, that was my next port of call, but using Diskpart :-)

---

### Post by rmadams1 on 2010-10-12
I've made it through to post #17 above, but while Windows repair sees a Win7 load, when I run rebuildbcd it doesn't. Total identified Windows installations: 0. 
 
Downloading gpart now to try to move the bootflag. Its been awhile since I've used it so hopefully its like riding a bike. Without the crashing and falling off part.

---

### Post by Quackers on 2010-10-12
You can move the boot flag with the command prompt in the windows cd.
Type this one line at a time and press enter
Diskpart
select disk 0
select partition 2
active
exit
bootrec /rebuildbcd
Then see if it finds windows installations to add to the boot store, if so answer Y
or try running "repair my computer again.

---

### Post by rmadams1 on 2010-10-12
Well, I'm back to being a slave to Bill Gates. I've got another laptop laying around here somewhere that I can use to get a little more up close and personal with 10.10. 
 
Thank you so much for the assist on this - it's much appreciated.

---

### Post by Quackers on 2010-10-12
Is Windows booting ok now? :-)

---

### Post by rmadams1 on 2010-10-13
Yep! It's doing everything Windows is supposed to do, including letting Outlook run my life. 
 
Thanks so much for the assist. :)
 
How can I mark this thread solved? Just put it in the title?

---

### Post by Quackers on 2010-10-13
Nice one :-)
Top right of the screen click on Thread Tools and select solved.

---

