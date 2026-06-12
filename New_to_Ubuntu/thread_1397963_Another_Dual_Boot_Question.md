---
title: "Another Dual Boot Question"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by Mike Green9 on 2010-02-03
[FONT=Verdana][SIZE=1]Feb.03.2010   22:37 EST[/SIZE][/FONT]
[FONT=Verdana][SIZE=1][/SIZE][/FONT] 
[FONT=Verdana][SIZE=1]Hi.[/SIZE][/FONT]
[FONT=Verdana][/FONT] 
[FONT=Verdana][SIZE=1]I have Windows 7 installed with a dual boot setup for XP or Windows 7.[/SIZE][/FONT]
[FONT=Verdana][SIZE=1][/SIZE] 
[SIZE=1]I just installed Ubuntu 9.10, and I want to boot with either XP, W7, or Ubuntu.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Using EasyBCD, I added 2 new entries as seen below (one with Linux/BSD and one with NeoGrub since I did not know which to choose):[/SIZE]
[SIZE=1]&#12288;[/SIZE]
[SIZE=1]Entry #5[/SIZE]
[SIZE=1]Name: Ubuntu Disk 1[/SIZE]
[SIZE=1]BCD ID: {10203afc-edb8-11de-a3ca-e2b506438538}[/SIZE]
[SIZE=1]Drive: C:\[/SIZE]
[SIZE=1]Bootloader Path: \NST\AutoNeoGrub0.mbr[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Entry #6[/SIZE]
[SIZE=1]Name: NeoGrub Bootloader[/SIZE]
[SIZE=1]BCD ID: {10203afd-edb8-11de-a3ca-e2b506438538}[/SIZE]
[SIZE=1]Drive: C:\[/SIZE]
[SIZE=1]Bootloader Path: \NST\NeoGrub.mbr[/SIZE]
[SIZE=1]&#12288;[/SIZE]
[SIZE=1]When I boot, the new boot options are displayed. All seems to be in order here.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Now the problem - what do I have to do to get either of the newly added options to actually boot into the Ubuntu partition (/dev/sdb4)?[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]When I installed Ubuntu, I did not allow it to touch the MBR, since [/SIZE][SIZE=1]I would prefer not to touch anything outside of the Ubuntu partition - big time fears of wiping out my ability to boot into Windows 7. Is this possible?[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]The contents of C:\NST\menu.lst is currently:[/SIZE]
[SIZE=1]*# NeoSmart NeoGrub Bootloader Configuration File*[/SIZE]
[SIZE=1]*#*[/SIZE]
[SIZE=1]*# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst*[/SIZE]
[SIZE=1]*# Please see the EasyBCD Documentation for information on how to create/modify entries:*[/SIZE]
[SIZE=1]*# [http://neosmart.net/wiki/display/EBCD/](http://neosmart.net/wiki/display/EBCD/)*[/SIZE]
*[SIZE=1][/SIZE]* 
[SIZE=1]I can boot the Ubuntu CD and bring up the Ubuntu desktop from the CD. [/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]What do I have to do, in super simple layman’s terms, to boot into Windows 7 or Ubuntu?[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Thanks,[/SIZE]
[SIZE=1]&#12288;[/SIZE]
[SIZE=1]MG...[/SIZE]
[/FONT]

---

### Post by samantha_ on 2010-02-03
> **Mike Green9 said:**
> [FONT=Verdana][SIZE=1]Feb.03.2010   22:37 EST[/SIZE][/FONT]
[FONT=Verdana][SIZE=1][/SIZE][/FONT] 
[FONT=Verdana][SIZE=1]Hi.[/SIZE][/FONT]
[FONT=Verdana][/FONT] 
[FONT=Verdana][SIZE=1]I have Windows 7 installed with a dual boot setup for XP or Windows 7.[/SIZE][/FONT]
[FONT=Verdana][SIZE=1][/SIZE] 
[SIZE=1]I just installed Ubuntu 9.10, and I want to boot with either XP, W7, or Ubuntu.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Using EasyBCD, I added 2 new entries as seen below (one with Linux/BSD and one with NeoGrub since I did not know which to choose):[/SIZE]
[SIZE=1]&#12288;[/SIZE]
[SIZE=1]Entry #5[/SIZE]
[SIZE=1]Name: Ubuntu Disk 1[/SIZE]
[SIZE=1]BCD ID: {10203afc-edb8-11de-a3ca-e2b506438538}[/SIZE]
[SIZE=1]Drive: C:\[/SIZE]
[SIZE=1]Bootloader Path: \NST\AutoNeoGrub0.mbr[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Entry #6[/SIZE]
[SIZE=1]Name: NeoGrub Bootloader[/SIZE]
[SIZE=1]BCD ID: {10203afd-edb8-11de-a3ca-e2b506438538}[/SIZE]
[SIZE=1]Drive: C:\[/SIZE]
[SIZE=1]Bootloader Path: \NST\NeoGrub.mbr[/SIZE]
[SIZE=1]&#12288;[/SIZE]
[SIZE=1]When I boot, the new boot options are displayed. All seems to be in order here.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Now the problem - what do I have to do to get either of the newly added options to actually boot into the Ubuntu partition (/dev/sdb4)?[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]When I installed Ubuntu, I did not allow it to touch the MBR, since [/SIZE][SIZE=1]I would prefer not to touch anything outside of the Ubuntu partition - big time fears of wiping out my ability to boot into Windows 7. Is this possible?[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]The contents of C:\NST\menu.lst is currently:[/SIZE]
[SIZE=1]*# NeoSmart NeoGrub Bootloader Configuration File*[/SIZE]
[SIZE=1]*#*[/SIZE]
[SIZE=1]*# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst*[/SIZE]
[SIZE=1]*# Please see the EasyBCD Documentation for information on how to create/modify entries:*[/SIZE]
[SIZE=1]*# [http://neosmart.net/wiki/display/EBCD/](http://neosmart.net/wiki/display/EBCD/)*[/SIZE]
*[SIZE=1][/SIZE]* 
[SIZE=1]I can boot the Ubuntu CD and bring up the Ubuntu desktop from the CD. [/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]What do I have to do, in super simple layman’s terms, to boot into Windows 7 or Ubuntu?[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Thanks,[/SIZE]
[SIZE=1]&#12288;[/SIZE]
[SIZE=1]MG...[/SIZE]
[/FONT]
I dont know about NeoGrub, since I use charmeleon, but

Very little people have booting into Windows 7 using Grub. In fact, you can even boot into windows 7 using grub-legacy, even though ill show windows vista.
The main problem that causes users to be unable to boot into windows 7, is that they resized their windows 7 partition using gparted/ubuntu partitiner...

p.s. what version of neogrub are you using? versions before 2.0 beta have no support for the default linux file system (since 9.10), which is ext4

---

