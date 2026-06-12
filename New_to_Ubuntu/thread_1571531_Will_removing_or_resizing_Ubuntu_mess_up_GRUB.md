---
title: "Will removing or resizing Ubuntu mess up GRUB?"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by The_Pirate_King on 2010-09-09
I've been running low on room in windows.  I originally divided my HDD is half between windows and linux, but since I rarely use Ubuntu I don't really see the point. 

So, can I safely remove Ubuntu without making it impossible to boot windows?

---

### Post by RJ12 on 2010-09-09
You will need to take GRUB off of your hard drive, if you delete Ubuntu, you delete some of GRUB's files, and it will stop working. The easiest way to remove GRUB is to either use EasyBCD or fixmbr

If you have Vista or 7 EasyBCD will help you remove GRUB with the click of a button.

If you have XP, you will need your XP cd and boot into the repair option, once you get to the CMD prompt type "fixmbr" without the quotes and it should erase GRUB.

Once you have erased GRUB you may delete Ubuntu with either the Windows Disk Management (If you have Vista or 7) or with GParted on your LiveUSB/LiveCD

---

### Post by wilee-nilee on 2010-09-09
I would avoid easybcd it is not needed, and even though some like it, is not maintained and updated and upgraded like Grub2 is. 

Here is a link to a recovery iso for W7 and the instructions to set the MS bootloader in the MBR before you remove Ubuntu. Only run the highlighted command.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

You never mentioned the actual Windows distro the same site has a Vista recovery link, and if you need it I can give you a link to a legit XP iso.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

