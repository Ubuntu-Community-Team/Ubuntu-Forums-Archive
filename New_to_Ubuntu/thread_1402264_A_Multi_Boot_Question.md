---
title: "A Multi Boot Question"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by Mike Green9 on 2010-02-08
[FONT=Verdana][SIZE=1]I want to multi boot XP, Windows 7 or Ubuntu 9.10.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Windows XP is installed in the 1st partition on Disk0[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Windows 7 is installed in the 6th partition on Disk0[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Ubuntu 9.10 is installed in the 10th partition on Disk1 i.e. /dev/sdb4.[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1](I instructed the Ubuntu Install to NOT touch the MBR.)[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]I have added the following boot option to Windows 7 using EasyBCD (v2.0.0.76)[/SIZE]
[SIZE=1][/SIZE] 
[/FONT][FONT=Calibri][FONT=Calibri][SIZE=1]Entry #3[/SIZE]
[SIZE=1]Name: NeoGrub Bootloader[/SIZE]
[SIZE=1]BCD ID: {10203b00-edb8-11de-a3ca-e2b506438538}[/SIZE]
[SIZE=1]Drive: C:\[/SIZE]
[SIZE=1]Bootloader Path: \NST\NeoGrub.mbr[/SIZE]
[/FONT][/FONT][FONT=Verdana][B][U][SIZE=1][/SIZE] 
[SIZE=1]Questions[/SIZE]
[/B][/U][SIZE=1]1. Did Ubuntu install GRUB at the beginning of the Ubuntu partition (Partition Boot Record) ?[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]2. How can I modify "C:\nst\NeoGrub.mbr" (Or "C:\nst\menu.lst") to boot from /dev/sdb4 ?[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1][/SIZE] 
[SIZE=1]Thanks,[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]M...[/SIZE]
[/FONT]

---

### Post by Brandon Williams on 2010-02-09
Unfortunately, there is a grub2 bug in 9.10 that prevents it from correctly install to a partition. It can only be installed to the MBR. It's possible to save the MBR, install grub2 to the MBR, copy the grub2 image from the MBR, and then restore the original MBR. That's what I did. [This post](http://ubuntuforums.org/showthread.php?t=1304667) was quite helpful as I tried to figure this out a few days ago.

---

