---
title: "Am I stuck using windows?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Treelvr on 2009-01-17
Almost every morning ubuntu won't work right because it says I don't have enough disc space. So I'll delete any partial torrents and move completes to USB drive. It won't even let me get my mail or go in to administrative properties until I do. My disk usage says less than half and gparted shows only half.
So yesterday I got sick of it and cloned the install to a 750 gig drive. Swapped them. But this mourning I get the same error. And I had to take the same steps again. Gparted shows only 10% being used. Whats the problem? 
I tried installing with the 8.10 disk ith XP on C:
This is what happened.
I wiped my D; 750 g HD clean
I then use the 8.10 disk and installed on D:
Instantly I get a Grub loading error 17 and Lilo is gone.
Looked here in this forum and they say reinstall. So I fdisk and format.
I did, Same error.
Next I use the windows disc to restore windows.
Windows is done and it wants the last bootup. Again I get grub loading error 17.
I try fdisking the MBR. Still same error.
I realize that the MBR is trashed. So I remove the partitions on C: & D: and low dos format both.
Next clean install of windows. I then go grab wubi since its the only thing that ever worked for me.
I install ubuntu again this time it works at least I think. The original Ubuntu is still siting on E:
I told wubi to install to D: and gparted does show something on D: including an ubuntu folder. But I've got everything back as it was sitting on E: Tho I think it either coipuied it from E: or the backups on F:

This is the second time I've tried to install from the 8.10 disc both were fresh burns from different places. The first time I tried to do a guided install on my wifes lap top and it ate the whole disk wiping out windows. So I fdisked, reinstalled windows and used wubi on hers. Disk space not a problem on hers since its only for Net, Email and Word. Does everyone have these problems with straight install on to windows boxes?

So this yesterday I get the same no disk space error. So I get rid of all torrents and get clients for windows. Windows shows less than 30 gigs used of a 750 drive but I keep getting errors. Am I stuck using windows for torrents? Is there away I can “make” ubuntu use or see the whole drive?

treelvr@treelvr-desktop:~$ sudo fdisk -l



Disk /dev/sda: 250.0 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xbe10be10



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS



Disk /dev/sdb: 750.1 GB, 750156374016 bytes

255 heads, 63 sectors/track, 91201 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xbe4cbe4c



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1       91201   732572001    c  W95 FAT32 (LBA)



Disk /dev/sdc: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x7ea9fb6c



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1               1       19457   156288321    7  HPFS/NTFS



Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes

255 heads, 63 sectors/track, 182401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x5cbc8a83



   Device Boot      Start         End      Blocks   Id  System

/dev/sdd1               1      182401  1465136001    7  HPFS/NTFS

treelvr@treelvr-desktop:~$ cat /etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro,relatime 0       1

/host/ubuntu/disks/boot /boot           none    bind            0       0

/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

treelvr@treelvr-desktop:~$ df -h


I love ubuntu, just having a hard time installing. And I much rather use it than Windows.
Am I stuck using windows for torrents? Am I stuck using ubuntu only using a 30 gig on any size drive?

---

### Post by ibuclaw on 2009-01-17
> **Treelvr said:**
> treelvr@treelvr-desktop:~$ df -h
What is the output of df -h?

Also, have you tried to install Ubuntu by rebooting and running the Install CD on boot?

I don't really know the state of Wubi at the moment, though I've been told that it runs well, but I'd still prefer a real installation over having a disk image running on Windows.

Regards
Iain

---

### Post by cwsnyder on 2009-01-17
If you are running WUBI, you cannot access the entire drive, only the virtual partition which was set up when you installed WUBI.  I would backup any data files you want to save, remove WUBI using Add/Remove programs, and re-install from your CD, only this time pay attention and when it prompts you for the amount of disk space to set aside for Ubuntu, set aside more than the default 4 to 8 G HD space.  WUBI uses its own 'partitioning' software so Gparted won't help.

---

### Post by Hendrixski on 2009-01-17
If Windows is hogging up space so that Ubuntu can't run, then just delete Windows and install only Ubuntu.

If you need Windows (I can't imagine why) then just install it in a virtual machine inside of Ubuntu.

---

### Post by Treelvr on 2009-01-17
I need windows cause I need frontpage. I have a frontpage website. I have tried every which way to install frontpage using WINE and Play on Linux. None have worked.
Everytime I've tried to install using the ubuntu disc its fried my windows install. On this desktop I've tried twice. Both times I got the grub loading error 17.
Ubuntu is on a 750 gig drive by itself. The only thing else on the drive is 2 folders XP put on there. "Recycled & System Volume Information" the rest is clear.
Ok I just checked gparted and its apparently using the original install on E: which is a 169 gig again its all by it self.

---

### Post by Hendrixski on 2009-01-17
Frontpage is holding you back from switching?

Have you tried some of the HTML editors in Ubuntu?  Or any of those CMS systems that can set up a website better than frontpage can, like Joomla, Drupal, Wordpress, TikiWiki, Plone, etc.?




Anyway, sorry I didn't offer much help yet... umm. Did you install using WUBI, or with an install disk?  Are you able to boot directly into Ubuntu without any error messages popping up.   Did you install just the default settings or did you change something in the config (like maybe instead of using ext3 did you use ntfs, or something)?

Most importantly, is there a LUG (Linux Users Group) or an Ubuntu LoCo team near your area?  Those are full of people who would be willing to sit down with you in-person and try the install.

---

### Post by Treelvr on 2009-01-17
I was never able to boot from the install off the cd. Just "grub loading error 17" and it would just stay there.
My website has over 5000 pages so changing over to another format isn't an option. Also my server only supports frontpage extensions.
Do I need to have the drive ext3 before I attempt another install. Will it setup Lilo for me so I can dual boot?

---

### Post by northern lights on 2009-01-17
> **Treelvr said:**
> My website has over 5000 pages so changing over to another format isn't an option. Also my server only supports frontpage extensions.You can always edit the existing files with another editor. They should not need changing for that. (X)HTML is universal. I'd at least look at *Kompozer* if you want a WYSIWYG editor or *Quanta* for a Dreamweaver like app.

> **Treelvr said:**
> Do I need to have the drive ext3 before I attempt another install?Nope. You need free space only. At best unallocated already. Just make sure to not select "Guided - Use entire disk", as that will wipe your current Windows and data.

> **Treelvr said:**
> Will it setup Lilo for me so I can dual boot?
It will setup GRUB. Does the job well.

---

### Post by Hendrixski on 2009-01-17
> **Treelvr said:**
> I was never able to boot from the install off the cd. Just "grub loading error 17" and it would just stay there.
My website has over 5000 pages so changing over to another format isn't an option. Also my server only supports frontpage extensions.
Do I need to have the drive ext3 before I attempt another install. Will it setup Lilo for me so I can dual boot?

Interesting.  Is it the CD that gets the error 17 or is it the computer once you've installed?  If it's the CD then you can also Download an install CD from Ubuntu that DOESN"T have the live-cd feature to it... it's JUST an installer.  I've often seen those succeed where a liveCD failed to even boot.

Also.... have you googled the error message?  
[http://www.google.com/search?q=grub+loading+error+17&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=grub+loading+error+17&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

I found that most problems I have are just a google search away from being solved.

---

### Post by jimmy the saint on 2009-01-17
I am going to get a plug in for virtualbox here.  Frontpage (if you are really dedicated to it) will work just fine in a virtual machine.  Enter VirtualBox.  With VirtualBox, you can create a Virtal Machine, install windows on it and install Frontpage and manage your website comfortable from there.  As an added bonus, your windows install is a little safer because you can make a "snapshot" and should you have an issue with malware, you can simply go back to the snapshot.  Think of it as system resotore that actually works!  The best part is its free, easy and kind of fun to have multiple OSs running at the same time.

---

### Post by Treelvr on 2009-01-17
It was the install. I had XP C: a cloned copy of a wubi install on D: which I told it to write over which it did. The original wubi install on E:. Which when I reinstalled to D: for some reason LILO set up to go to E:. So I've got a new XP on C: and the original Wubi install on E:

I just don't want to take all day rebuilding C: again.

---

### Post by theozzlives on 2009-01-17
[VirtualBox]("http://www.virtualbox.org/") is a good idea... I to run Windows along with Front Page and various certification programs and it runs fine.

---

### Post by Treelvr on 2009-01-17
OK, I'm D/L another copy of the 8.10 686 copy. Should I do anything to the D: HD with gparterd. Right now it fat32. Should I remove partitions should I reformat before I try install again?

---

### Post by Treelvr on 2009-01-17
OK got figured out. I installed 8.10 and got the same error 17 message with grub. Turns out that it has to do with the BIOS. Now my BIOS will only allow you to have one HD in the booting process. And for that right one to be listed it has to #1 drive. So because C:s MBR was telling to go to D: for grub but because its not listed in the boot process it couldn't find it. So I used a low DOS formater to figure out which drive was which and rearrange them accordingly it now boots to grub.

---

### Post by Treelvr on 2009-01-18
[QUOTE=jimmy the saint;6567399]Enter VirtualBox.  With VirtualBox, you can create a Virtal Machine, install windows on it and install Frontpage and manage your website comfortable from there.  As an added bonus, your windows install is a little safer because you can make a "snapshot" and should you have an issue with malware, you can simply go back to the snapshot.  Think of it as system resotore that actually works! 

How do I run anything without the use of a mouse? I DLd virtual box and added XP but now I can't do anything with the mouse. Is there a trick I don't know about?

---

### Post by blackmail on 2009-01-18
Ok so first I think a clean ubuntu instalation would be quite nice.And if you can you should use reiserfs in stead of ext3, because it is many times stronger just for an idea, here's what it can do: [http://en.wikipedia.org/wiki/ReiserFS](http://en.wikipedia.org/wiki/ReiserFS)
Second you should order a cd on the ubuntu homepage, because i also got some similar errors with a downoladed copy, and you should check your power suply, because when mine was dying the grub just kept having errors, and i ended up reinstalling it after every shutdown.And regarding your frontpage issue you can make it run on ubuntu using wine, the only issues I saw while looking after this info was that the frontpage ran with wine cannot acess sites from servers, but you could run windows on ubuntu, for your editing work in frontpage. Here are 2 links:
[http://ubuntuforums.org/archive/index.php/t-91022.html](http://ubuntuforums.org/archive/index.php/t-91022.html) - frontpage on ubuntu, and
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo) this shows how to install windows under ubuntu.

---

### Post by cwsnyder on 2009-01-23
Just a quick reply to using your mouse with VirtualBox:  You click on the VirtualBox window and your mouse and keyboard will then be 'captured' by the VB Windows.  To get your keyboard and mouse back to Ubuntu, hit your right hand control (CTRL) key (the one two keys under your Enter key).

---

### Post by LowSky on 2009-01-23
Want to get rid of that error 17 garbage set u your boot hard drive properly.

The hard drive you want to use  Ubuntu on set that as the bootable drive, then install Ubuntu on it. The secondary one with windows will be left alone and its MBR will be untouched.

Fixing windwos MBR is very eay aslong as you have a Winfdows install CD. Just boot the Windows cd (with Ubutnu drive disconnected) and run recovery mode, type fixmbr

now reconnect ubuntu drive, make sure it the bootable drive form BIOS and away you go

---

### Post by Treelvr on 2009-01-23
I got virtbox to work by deleting the one from syaptic and installing the one from sun. It was a known bug fixed in 2.12. I got xp to work in VB but the controls are really slow with the game we want. Still looking for Luxor clone for Linux. Everytime I install with WINE its fries my Ubuntu install.

---

### Post by fishman78 on 2009-01-23
> **Treelvr said:**
> I got virtbox to work by deleting the one from syaptic and installing the one from sun. It was a known bug fixed in 2.12. I got xp to work in VB but the controls are really slow with the game we want. Still looking for Luxor clone for Linux. Everytime I install with WINE its fries my Ubuntu install.


Don't forget to install the guest additions in your XP VM.  It will smooth out the performance.  HTH

Under the Devices drop down at the bottom is Install Guest Additions...   Click that and it will mount a virtual disk which you install like any other CD/DVD in Windows.  Once you get VBox working, you won't need Wine anymore...  At least I didn't.

---

### Post by Treelvr on 2009-01-23
OK tried addons. When I click on it it doesn't do anything. Do I need to get a file somewhere?? Do I need to put my XP disk back in??

---

### Post by fishman78 on 2009-01-23
> **Treelvr said:**
> OK tried addons. When I click on it it doesn't do anything. Do I need to get a file somewhere?? Do I need to put my XP disk back in??


If you are refering to the guest additions, it should show up in "my computer" as a inserted disc.  Just double click and go.  If that's not what you are refering to, then never mind.:D

---

