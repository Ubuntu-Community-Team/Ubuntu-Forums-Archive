---
title: "ubuntu 9.10 installation problem with wubi"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by nimal on 2009-12-31
[LEFT]I am a beginner to linux.I tried to install ubuntu ,as  a dual boot with vista home premium by using wubi. I downloaded the iso image and burned a cd using nero. At the begining everything was fine when I startted installing useing wubi to fully formatted E drive.  But unexceptedly the installation came to a halt after the following message  appeared.          Permission denied .Error occured.                                                                                 c:\ users \ my user name  \ appdata \ local \ temp \ wubi - 9 ,10  ubuntu 1 - rev 160 . log I  would be very much thankful if anybody could suggest me a method to overcome this issue and to get ubuntu installted  as  a dual bootable system on my desktop.The vista system has no disk problems or memory issues - have 2 Gb ram. I tried it twice but i could not succeed.  :confused:                                                                                                       
[/LEFT]

---

### Post by spiky001 on 2009-12-31
U should be able to dual boot straight off of cd dont go into windows 1st put cd in cd drive reboot machine then your away

---

### Post by Jose Catre-Vandis on 2009-12-31
You problem sounds confusing?

If you use wubi you are installing Ubuntu inside Windows, but you will get a windows bootloader entry to boot ubuntu. You don't need an E: drive for this?

If you are dual booting you don't need wubi, just boot from the CD you burned. Ubuntu will resize your Windows partition to provide space.

If you want to go the wubi route i suggest you do the following:

1. Having booted up in Windows, create a folder **C:\uboot** (It actually doesn't matter what you call it!) 

2. Copy the iso you downloaded into this folder.

3. Insert your burned CD, browse to it with explorer, and copy the file **wubi.exe** from the CD into your **C:\uboot** folder.

4. Remove the CD

5. Browse to your uboot folder and double click on **wubi.exe**. The install should proceed, and create the Ubuntu virtual disk and other files in a folder called **C:\ubuntu**. Wubi should ask you to uninstall any previous installation.

6. When done, reboot your PC, select Ubuntu at the bootloader screen, and allow the installation to complete.


Using wubi at least helps to preserve your Windows system, but you will get better long term performance if you install to the hard drive.

---

### Post by alzie on 2009-12-31
Simple things first.  When you boot to your Ubuntu CD there is a utility to check the CD for errors.  I'd run this first to ensure that we have a good starting point.

I'm going to assume that when you install with WUBI you are selecting drive E.  This should not be an issue.  The target drive should still be in NTFS format.  WUBI will not actually use this much other than storage.  WUBI creates a virtual disc for your Ubuntu install to run in.  My WUBI install was onto drive D which is basically a storage drive for Windows downloads.

As far as installation it should work fine from the CD but if you want to try Jose Catre-Vandis's suggestion it should work as well.  Personally I have a folder on my Windows desktop (XP) called Ubuntu that only has WUBI.exe and the 9.10 iso in it.  WUBI will look in its home folder first to install.

Hopefully this should get you going.

I'll give you a heads up,  some people have had an issue after the initial set of updates after the install.  To prevent this open the terminal and enter ```
sudo update-grub2
``` and enter your password when prompted.  This will update the Grub boot loader to "see" your WUBI install after the first set of updates.

I hope this helps

---

### Post by Sef on 2009-12-31
If you download [wubi]("http://wubi-installer.org/"), it installs on your Windows as a file.

---

### Post by nimal on 2010-01-01
Currently I am studying the replies of friends who responded to my question. I  would like to thank specially  alzie and Jose Catre-Vandis . Also I would like to invite others who can give valueble advice  to help me to broden my knowledge about ubuntu 9.10 .Also I wish all viewers  a happy 2010 :D

---

### Post by tom.swartz07 on 2010-01-01
> **nimal said:**
> Currently I am studying the replies of friends who responded to my question. I  would like to thank specially  alzie and Jose Catre-Vandis . Also I would like to invite others who can give valueble advice  to help me to broden my knowledge about ubuntu 9.10 .Also I wish all viewers  a happy 2010 :D

HI! Happy new year!

There are some really good guides here on the forums and elsewhere.

DEFINITELY read this one: it helped me greatly when I started out
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

This is a blog guide that helps show you some cool info about what you could do with Ubuntu.

[http://linuxowns.wordpress.com/2008/11/11/ubuntu-the-absolute-beginners-guide/](http://linuxowns.wordpress.com/2008/11/11/ubuntu-the-absolute-beginners-guide/)


If you want to keep up with the newest and hottest information with Ubuntu, such as new programs and neat little tricks, head on over to [http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)
Its updated quite regularly and has lots of interesting information.


Hope this helps!

---

### Post by Bartender on 2010-01-01
> **nimal said:**
> Also I would like to invite others who can give advice  to help me to broaden my knowledge about ubuntu 9.10 

My advice:  delete wubi and do a true dual-boot install.

---

