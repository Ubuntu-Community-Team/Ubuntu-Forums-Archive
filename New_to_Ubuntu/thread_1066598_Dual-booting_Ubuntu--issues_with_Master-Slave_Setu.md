---
title: "Dual-booting Ubuntu--issues with Master-Slave Setup?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by xadion on 2009-02-11
Hey guys this is my first time on these forums and I'm completely new to Linux/Ubuntu. So I'm sorry if I sound a bit newbie about certain things!

So what I'm trying to do is dual-booting Ubuntu 8.10 and Windows XP Home Edition on my slightly older Dell 2400 PC. I have two hard-drives set up--the Master Drive is naturally Windows XP and is partitioned into drives C: and D:. My slave drive is just an HDD that I took from another PC that crashed and it's one complete partition--G:. After I downloaded the ISO from Ubuntu's Live CD page, I couldn't burn it (don't know if it's the ISO, my Nero, or my disk drive), but I mounted the ISO using DAEMON Tools with no problems. I tried to install Ubuntu alongside window when the Autoplay started on my Slave Drive G:. After installation, it asked to reboot and when I got to the screen I chose to boot up Ubuntu, but it didn't start up the OS in any way--just some sort of CMD prompt. So I rebooted back into Windows XP and uninstalled Ubuntu using Add/Remove, then re-installed with the same method into my D: Master Drive. When I rebooted and selected Ubuntu, it successfully loaded up. Here come my questions: 1) Ubuntu's built-in install (for installing straight into a partitioned drive) didn't detect my Slave at all when in Live CD mode, can I alternatively install Ubuntu by re-formatting my G: drive and installing Ubuntu on it as I would Windows? 2) Is this a method of "dual-booting," which is selecting which OS I'd like to boot in every time I turn on my PC? 3) Will Ubuntu run regular AIM 6.8? because I don't really use ICQ, MSN, Yahoo, etc. 4)Is OpenOffice intercompatible with Microsoft Office 2007 and all previous versions of it, and vice-versa? 5) Is networking much more "processed" than it is on clunky and confusing Windows XP?--are there Linux programs that help smooth out networking issues, is it specifically better than Windows for server-hosting concerns? 6)Whats with the 5,6,7,8gb to 15gb installation choices? Am I missing out by only installing 8gb of the OS? What should I do if I'm planning to install Ubuntu legitly onto my HDD? These are just the gists of my questions for Linux. I've been using Windows for a long time, and I'm a casual PC user; internet, AIM, games, and schoolwork--I just wanna know if there's anything more to Linux than Windows, other than "Open-source" and a noticably faster processing time for progs and software. I'd like to know your reccomendations for Anti-virus, multimedia, softwares etc etc. Thanks in advance guys! Sorry again if this post is a little too clustered.

PC Specs:
Intel Pentium 4 2.4 Ghz
nVidia Geforce FX 5200 256mb
1024mb Ram
Razer Diamondback Mouse
40gb WD Slave Drive :(
35gb Master:(

---

### Post by tarps87 on 2009-03-11
Lots of questions :) I will try to answer as many as I can.

The first one where you mention about installing Ubuntu, the auto run feature that ran when using daemon tools would be the wubi installer, this installs Ubuntu with in windows. You will need to burn the iso to cd or create a live usb, this can be do with UNetbootin
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

This installer will format the and install to the drive/partition you tell it to. I would recommend backing up any important data first just in case you select the wrong drive or there is a problem

About the command line bit, did you download the server or desktop version? The server version is optimised for being a server so not gui and modified memory management. I would suggest the desktop version

About AIM 6.8, I think the version numbering is different in Linux, there are alternatives but I don't use aim so I can not be much help with this

About OpenOffice, OpenOffice is completable with all Microsoft Office formats up to and including 07, Microsoft Office is only completable with Microsoft Office formats. How ever OpenOffice will also save to any Microsoft Office format/version

About networking, I find it easier but that just me :) The default network manager is simple to use how ever in some cases there are problems with wireless networking, a program called wcid will solve this. It is an alternative network manager

About the 5,6,7,8gb to 15gb installs, I think this is the maximum size the wubi install can use, I haven't use wubi so I am not positive about this. If you do a full/normal install this option does not appear

Last comments:
The drive letters c:,d: and g: are the windows drive lettering scheme, they will look something like sda1,sda2,sdb1 in GNU/Linux. sda,sdb being the drive sda1,sda2 being the partition.

Back up any important data in case the worst happens

Check  the checksum of the iso before burring it, it will have cd's :)
This link should help with this [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

This may help with burning the CD, it suggest an free(I think open-source) cd burner which may be worth a try if you can't get nero to work
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I thinks that's all of them :)

I hope this help, if you have any other questions just post back or start a new thread

---

### Post by carml on 2009-03-11
For quite any kind of istant messaging on Ubuntu there's Pidgin,a SW that supports any protocols,so if you have any SW like MSN,AIM, etc on Windows, on Ubuntu you'll have Pidgin for all those networks. :)

---

### Post by PunkLV on 2009-03-11
Newbie as I am. Heed my words:

- Backup on a removeble/network drive everything you consider useful/important!
- Make one partition instead of C: D:
- Install via rebooting and running the LiveCD. Not as a programm. You will have a choise which OS to boot at startup.

---

### Post by tarps87 on 2009-03-12
> **PunkLV said:**
> Newbie as I am. Heed my words:

- Backup on a removeble/network drive everything you consider useful/important!
- Make one partition instead of C: D:
- Install via rebooting and running the LiveCD. Not as a programm. You will have a choise which OS to boot at startup.

It does not matter how many partitions you have (although there is a limit off 4 primary partitions there is not limit on logical partitions). Many new computers have to partitions, one is the windows os and one is a backup/restore partition. Therefore one partition would not work.

---

