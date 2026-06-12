---
title: "Sis Mirage 3+ VGA sucks!"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by Rabhak on 2011-03-15
Has anyone solved this issue on SIS mirage 3+? im using ubuntu 9.10 and followed every instruction in the internet and nothing worked! I've already reinstalled ubuntu for almost 10 times already because of this "low graphics" welcome note during startup...im tired.. 
Im using Neo Basic Laptop B2310N

Please help me.


PS. please do not give me any link. . i tell you i've tried that already. . i've tried to google about the problem and tried from page 1 until 15. .nothing worked. .

---

### Post by wep940 on 2011-03-16
First off, as frustrated as you may be, you WILL get links from us - that's the only way to point you to things.  But before we do, since you say you've done pages 1-15 on Yahoo, give us the following information:
 
- which version of the SIS Mirage 3 is it?  771?  761?  Try posting the complete output of lspci | grep VGA back here
 
- what search string did you use for your Yahoo search?  I did a simple search and found many sites that guide installing the driver (mostly 10.04).  It may be that you'll need to upgrade from 9.10 to the long term support 10.04 or the 10.10 release.

---

### Post by Rabhak on 2011-03-16
@wep940

here it is:


rabhak@rabhak-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 SATA controller: Silicon Integrated Systems [SiS] AHCI IDE Controller (0106) (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
03:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
03:00.5 Ethernet controller: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller (rev 02)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
rabhak@rabhak-laptop:~$ 



Oh by the way, i've already tried ubuntu 8.10, 10.04, 10.10, fedora and open suse. . nothing really worked. . . i hope you could help me

---

### Post by Rabhak on 2011-03-16
Any help???? please?

---

### Post by Rabhak on 2011-03-16
Please if anybody or an angel would want to help me please send me a message in my email. . [email]mcdebbiealbor@gmail.com[/email]

Thank you so much . . I'll be waiting!

---

### Post by LowSky on 2011-03-16
these instructions found here don't work?

[http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html)

---

### Post by Rabhak on 2011-03-16
> **LowSky said:**
> these instructions found here don't work?

[http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html)


Yeah i've tried that already. . and i had success doing it. but when i reboot my laptop my screen gets fuzzy and their is a welcome not that says "ubuntu is running in a low resolution" and then click ok to continue.

---

### Post by wep940 on 2011-03-16
Sounds like the driver is working but having trouble determining what your monitor is, so it is defaulting to low res.  I saw other instructions on the web for installing the driver for this very adapter as well, in Ubuntu 10.  In one of those it mentioned that the instructions were having you create a Xorg.conf file.  If the instructions you followed did the same, you can edit that file to define resolutions for your monitor and a default resolution.  If not, I know there is a way at the command line to add them, but I don't remember right now.  One of the posts in the last week or so talked about doing that.

---

### Post by Rabhak on 2011-03-17
> **wep940 said:**
> Sounds like the driver is working but having trouble determining what your monitor is, so it is defaulting to low res.  I saw other instructions on the web for installing the driver for this very adapter as well, in Ubuntu 10.  In one of those it mentioned that the instructions were having you create a Xorg.conf file.  If the instructions you followed did the same, you can edit that file to define resolutions for your monitor and a default resolution.  If not, I know there is a way at the command line to add them, but I don't remember right now.  One of the posts in the last week or so talked about doing that.

Hi wep. i tried connecting my laptop to a monitor of my desktop and restarted it. . it displayed the 1024x768 resolution automatically.. i knew my laptop is capable of that resolution but i reallt cant figure it out. . . it's a new hope for me. thanks.

---

### Post by MisterLambda on 2011-03-17
I have the Mirage 771 and it's sucktastic as well. No AGP or PCIe so the latest card I can plop in a GeForce 6 for PCI.

However, it did properly detect the monitor, albeit not using widescreen. 2D i tolerable but SDL games and apps will flicker on Lucid LTS. If you want to use SDL apps Intrepid works fine. No 3d accel, so don't bother unless you like Mesa software rendering.

---

