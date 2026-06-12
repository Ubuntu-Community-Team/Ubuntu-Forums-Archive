---
title: "Installing on PC without OS"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by er63c on 2011-06-26
I'm buying a brand new desktop PC without an operating system installed and plan on installing Ubuntu myself as the sole OS.  My current PC has Windows XP and I've never used Ubuntu before.  I've read various instructions for installing Ubuntu and would be grateful for help with these 2 questions:

(1) The computer store have said the hard disk will be "formatted".  I don't know what that means, but are there any special instructions I need to give them when they do that in order to make sure Ubuntu will work properly afterwards?  I haven't told them what OS I'll be using, so they probably assume it will be Windows.  

In case it makes any difference, the CPU is an AMD Phenom II X4 955, the memory is 2x2GB PC10666 DDR3/1333mhz Dual Channel, the motherboard is an Asus M4A88TD-M EVO and the hard disk is 500GB SATA-II.

(2) When I get the computer and switch it on for the very first time, how do I install Ubuntu?  Do I really just open the CD-drive, put the Ubuntu CD in and follow the on-screen instructions?

---

### Post by Elfy on 2011-06-26
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

1 - it's likely that it'll be ntfs - no use. You can tell the installer to use the whole disc - that's what it will do and it will format the disc as appropriate.

2 - see the link above :)

---

### Post by nerdy_kid on 2011-06-26
> **er63c said:**
> I'm buying a brand new desktop PC without an operating system installed and plan on installing Ubuntu myself as the sole OS.  My current PC has Windows XP and I've never used Ubuntu before.  I've read various instructions for installing Ubuntu and would be grateful for help with these 2 questions:

(1) The computer store have said the hard disk will be "formatted".  I don't know what that means, but are there any special instructions I need to give them when they do that in order to make sure Ubuntu will work properly afterwards?  I haven't told them what OS I'll be using, so they probably assume it will be Windows.  

In case it makes any difference, the CPU is an AMD Phenom II X4 955, the memory is 2x2GB PC10666 DDR3/1333mhz Dual Channel, the motherboard is an Asus M4A88TD-M EVO and the hard disk is 500GB SATA-II.

(2) When I get the computer and switch it on for the very first time, how do I install Ubuntu?  Do I really just open the CD-drive, put the Ubuntu CD in and follow the on-screen instructions?

1:  it doesn't matter, Ubuntu setup will format the drive again anyway.  

2.  Yup!

---

### Post by Rex Bouwense on 2011-06-26
Yes that is all that you have to do especially if you are planning on using the whole disk for Ubuntu.  Part of the installation process is a disk format or a partition format if you are dividing your hard disk.  You can sit back and let it install and 20-30 minutes later the installation will be complete.  Problems or questions, post here and someone will be more than happy to provide assistance.
You two must have taken typing in school.  I'm still using two fingers.

---

### Post by Swagman on 2011-06-26
You might want to create /home on its own partition but it's up to you.

You'll have to switch on to open the cd tray. You will get an error message on screen about no bootable medium.

Ignore it.. Open the cd tray.. stick the Ubuntu (or distro of choice) in the drive, close the tray and press ctrl + Alt + Del or hit the reset button.

Bobs your Mothers brother

---

### Post by dFlyer on 2011-06-26
If your installing linux for the first time on a fresh new hard drive, my advice is to first download several various distro's of linux beside Ubuntu that provide live desktop cds. To name a few that provide live desktop:

Ubuntu
OpenSuSE
Febora
Mint

Run each cd from the live desktop for a day or so, to be sure all your hardware works including wifi if you have it and any printers. Each distro comes with various desktop environments, decide which desktop environment you want to run.

Remember that linux what ever distro version you choose is not windows. In the beginning just go slow and have fun. When you have problems ask for help by providing as much information about your system and problem as possible. I've been running linux since the mid 90's and find it as a very solid OS and have been using Ubuntu as my sole OS since 2006. 

Should you choose to install Ubuntu or what ever distro it will format your system for you. You can do custom install so you can have a separate /home folder, should you choose that route, make sure you give most of your free space to your /home folder. I myself find 12 - 20 gig for a / (root) partition as good and the rest goes to my /home folder minus the amount I use for swap. Your swap should be at least equal to or double your system ram.

You have choices with linux. Again welcome to the forum, go slow and have fun. Most problem can be worked out.

---

### Post by ajgreeny on 2011-06-26
> **Swagman said:**
> You might want to create /home on its own partition but it's up to you.

You'll have to switch on to open the cd tray. You will get an error message on screen about no bootable medium.

Ignore it.. Open the cd tray.. stick the Ubuntu (or distro of choice) in the drive, close the tray and press ctrl + Alt + Del or hit the reset button.

Bobs your Mothers brother
I totally agree with this and recommend that you do make a separate /home by following the link [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

It will make life a great deal easier when and if you ever need to re-install the OS.

---

### Post by er63c on 2011-06-27
Many thanks for all the replies, which were very helpful!

---

