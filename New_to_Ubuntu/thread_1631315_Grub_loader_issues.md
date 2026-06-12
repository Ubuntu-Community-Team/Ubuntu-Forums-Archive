---
title: "Grub loader issues"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by Tumblweed on 2010-11-26
Is there a way to edit my grub loader? I had the 32 bit 10.10 installed,I was having a few issues (wow grafis and my ram wasn't showing up) I read that the 32bit  would not read any more then 3gig of ram so i downloaded the 64bit version burned the iso and installed,unfortunately i didn't format the partition prior to installing i thought it would just  write over the 32 bit. Well it did sorta..... but now I have 2 ubuntu versions in grub to choose from only 1 does not do anything but sit at the splash screen.
I would like to move the windows partition to be the default (ie if i don't choose anything it loads windows) at least till/if I can get everything I need to work, and remove the choice for the ubuntu that don't work.

---

### Post by TeoBigusGeekus on 2010-11-26
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by Tumblweed on 2010-11-26
why did didnt  grub2 load by default on my system?  and it wont let me install it now 
ken@ken-Studio-1737:~$ grub-install -v
grub-install (GRUB) 1.98+20100804-5ubuntu3
ken@ken-Studio-1737:~$ sudo aptitude install grub-pc
sudo: aptitude: command not found
ken@ken-Studio-1737:~$

---

### Post by Tumblweed on 2010-11-27
bump

---

### Post by wilee-nilee on 2010-11-27
> **Tumblweed said:**
> bump

Give us a screen shot of gparted from the live cd or a Linux setup.

---

### Post by Tumblweed on 2010-11-27
_[IMG]http://img808.imageshack.us/img808/558/screenshotgo.png[/IMG]_

---

### Post by wilee-nilee on 2010-11-27
So to begin with we can just restore the MS bootloader to the MBR. Here are two links one for Vista one for W7 choose then one for your system and run the one command I highlight.
Vista:[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
W7:[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Command run just the highlighted one.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

If it is XP a install disc then fixmbr is the fix, and here is a XP link.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

So with a quick look at Ubuntu is there anything you want to save there? it can be done with a live Ubuntu CD. You only show one Ubuntu install, hard to say the nature of its problems without a little forensic looks, but getting the MS back for now seemed to be a goal here.

---

### Post by Tumblweed on 2010-11-27
I dont want to get rid of ubuntu I  would like to move the windows partition to be the default (ie if i  don't choose anything it loads windows) at least till/if I can get  everything I need to work, and remove the choice for the ubuntu option that  don't work.                                                           
                 [[IMG]http://ubuntuforums.org/images/buttons/collapse_thead.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10168443#top")

---

### Post by wilee-nilee on 2010-11-27
> **Tumblweed said:**
> I dont want to get rid of ubuntu I  would like to move the windows partition to be the default (ie if i  don't choose anything it loads windows) at least till/if I can get  everything I need to work, and remove the choice for the ubuntu option that  don't work.                                                           
                 [[IMG]http://ubuntuforums.org/images/buttons/collapse_thead.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10168443#top")

Post 2 has a link to some grub basics and if you look in the signature of drs305 there are a bunch of specialized grub tutorials.

---

### Post by Tumblweed on 2010-11-28
Tnx for the help.I got my boot  screen all cleaned up and nice and purty now...lol 
Even got that neat game on it :D

---

