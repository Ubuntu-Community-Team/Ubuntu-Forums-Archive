---
title: "problem in display resolution while installing fresh copy of ubuntu 9.10"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by sundar.mailbocs on 2010-03-29
I have install ubuntu 9.10..
After the installation my default display resolution is set to 800x600
where i cant able to find 1024x768 in system->preference->display option...

help me to overcome this problem..

i had try out 
1---xrandr
2---cvt 1024 768
3--xrandr --newmode
4--xrandr --addmode

its works only until restart....
so after the my restart its not working..:shock:

---

### Post by roger_1960 on 2010-03-29
Hi

What is your video card?  Can you post the output from terminal of > lspci

---

### Post by sundar.mailbocs on 2010-03-29
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller:** Intel Corporation 82865G Integrated Graphics Controller (rev 02)**
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by sundar.mailbocs on 2010-03-29
HI roger,
i m new to linux os-
thank you for helping me....
My video card** -Intel Corporation 82865G Integrated Graphics Controller**

---

### Post by roger_1960 on 2010-03-29
Hi again

Not sure if this will help but..........

Open Synaptic Package Manager

system>administration>synaptic package manager

Click on search - wait for the small window to open

Enter i915 in the search box - click search

Select for installation the package xserver-xorg-video-intel

Click on "apply"

When installation is complete, cross fingers and reboot!

---

### Post by Grenage on 2010-03-29
It's bound to be an EDID issue, see [here]("http://www.grenage.com/xorg.html").  I wrote it as a rough guide; if you have issues following it, or with any of its content, let me know.

---

### Post by Roger Allott on 2010-03-29
If that doesn't help, look at [this thread]("http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283") which explains how I resolved an identical problem. FWIW, it had nothing whatsoever to do with drivers.

---

### Post by Roger Allott on 2010-03-29
> **Grenage said:**
> It's bound to be an EDID issue, see [here]("http://www.grenage.com/xorg.html").  I wrote it as a rough guide; if you have issues following it, or with any of its content, let me know.

That's a good guide. Loads of people seem to have had a problem with the non detection of their monitor. Your guide really ought to be a sticky in this Absolute Beginners Talk forum.

---

### Post by Grenage on 2010-03-30
Thank you; it's not very complete, but I think it covers the basic problem that a lot of people have.

---

