---
title: "Resolution Problem"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by happy2pester on 2010-08-07
I've just started trying to use Ubuntu 10.04. I installed it, and have discovered that the maximum screen resolution that it thinks that my laptop's monitor can display is 800x600, and I know it is capable of 1024x768. I've tried to research various options on the internet, and the best I've come up with is the instructions contained in this thread: [http://ubuntuforums.org/showthread.php?t=1474910](http://ubuntuforums.org/showthread.php?t=1474910)

Below is the what I've done, following the steps given in the thread above, and the results

$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

$ xrandr --addmode default 1024x768_60.00

$ xrandr --output default --mode 1024x768_60.00
xrandr: Configure crtc 0 failed

I want to know, if anyone can tell me, what I can do to change my screen's resolution.

---

### Post by cariboo on 2010-08-07
It would be a lot more helpful if you told us what graphics adapter you are using, and if you have install the proper drivers for it.

---

### Post by roger_1960 on 2010-08-07
Hi

I tried all the xrandr commands with no luck.  With my Trident Cyberblade an xorg.conf file was needed...we really need to know what graphics card you have.

Type > lspci in terminal and post the output here.

---

### Post by happy2pester on 2010-08-07
This is the output I get from lspci

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by roger_1960 on 2010-08-07
Hi

This appears to be a known bug

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/332140](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/332140)     Not sure, but this may give a solution.  It gives the content of the file /etc/X11/xorg.conf  This file can be created by using > gksudo gedit /etc/X11/xorg.conf in terminal and saving it.  Note that nothing appears when you type in your password.

Hi also have a look at post #119 in this link: [http://ohioloco.ubuntuforums.org/showthread.php?t=958967&page=12](http://ohioloco.ubuntuforums.org/showthread.php?t=958967&page=12)

---

### Post by happy2pester on 2010-08-07
Solved it. I had to use the stuff from Antonio J. de Oliveira, that i was linked to from that page that you linked me to roger_1960, thank you very much.

---

