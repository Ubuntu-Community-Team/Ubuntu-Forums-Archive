---
title: "Dual Booting: XP &amp; any Linux OS results in freezing during installation"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by ptw on 2009-11-25
Hello all:

I recently formatted my hard drive (capacity of 160GB), with intentions of dual booting Windows XP and an OS with a KDE desktop environment (having Kubuntu in mind).  I've been going at this for hours during the last few days, and am pretty frustrated to say the least! 

So I initially created 4 partitions: (one for Windows XP, another for apps, another for data, and the last (about 90 GB I was reserving to install Kubuntu).  I burned the .iso image of the latest Kubuntu  onto a CD, and popped it in.  It appeared to inititially work, but then it freezes, and I was left with the Kubuntu logo on my screen.  I've rebooted countless times. 

I've burned the images of Fedora 12, Kubuntu, Ubuntu, Debian 5.0 onto a CD, and have tried to install all of them unsuccessfully.  They all, at some point, freeze up during the initial installation.

With Debian, it froze when trying to detect network hardware, so I disabled the Onboard LAN in BIOS and tried that...which didn't help either.

Since then, I have formatted my drive again, installed XP on just 1 big partition. and downloaded the Ubuntu Installer for Windows. Everything seems to have gone well during installation, and it asks me to reboot. I do...and it gets stuck on the Kubuntu logo again! 

Can anyone help me figure out what the problem is, and help me successfully install Windows XP & Kubuntu?

Thanks!

---

### Post by overdrank on 2009-11-25
Hi and welcome, Could you give us some system specs like memory, graphics card and so on.
I am assuming you are using the latest Ubuntu 9.10. Have you tried any other versions like 9.04 or even 8.04 lts?
Moved to Absolute Beginner Talk

---

### Post by desperado665 on 2009-11-25
Your freeze issue is due to hard drive limitations. You can only have 4 primary partitions per physical drive. Since you seem to already have 3 (XP, Data and Apps) you don't have the two primaries (swap and /) that a default install of Kubuntu or any linux distro requires. 

You can however pre-partition the remainder of the drive using your last exisisting primary partition as swap then adding / and /home as extended.

---

### Post by ptw on 2009-11-26
Specs:
 
NVIDIA GeForce4 MX 440 with AGP8X
Intel Pentium 4 CPU 2.80GHz
2.80 GHz, 512 MB of RAM
 
 
Yes, I'm using the latest Ubuntu 9.10. I have also tried 8.04 with no success.
 
Well after I had it divided in 3 partitions, and saw it didn't work, I decided to go with one primary partition instead. And having done that, it still freezes.

---

