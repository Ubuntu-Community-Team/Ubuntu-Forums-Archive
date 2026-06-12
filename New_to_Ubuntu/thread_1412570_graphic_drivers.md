---
title: "graphic drivers"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by Christopher Newtoit on 2010-02-21
Hi-

I am wondering about geting better graphical interface with the Ubuntu OS, "no proprietary drivers in use" it says when I used the hardware driver tool. I have no idea how it works, any ideas?

---

### Post by nick_goodfate on 2010-02-21
what card do you have?

---

### Post by nick_goodfate on 2010-02-21
> **Christopher Newtoit said:**
> Hi-

I am wondering about geting better graphical interface with the Ubuntu OS, "no proprietary drivers in use" it says when I used the hardware driver tool. I have no idea how it works, any ideas?

if you have nvidia or ati download envy and install the driver it recomends you : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by halitech on 2010-02-21
open a terminal and run
```
lspci
```
post the results here so we can advise how to install any drivers that you may need

do not just grab the envy script as it may load improper drivers and make your system unusable without a lot of work.

---

### Post by Christopher Newtoit on 2010-02-21
"lspci" gives this

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:08.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)



have envyNG, unsure if it is recommending that I install some drivers or not.  It shows a column with X's in red boxes-meaning that they are missing or that they are not compatible?

thanks again.

---

### Post by halitech on 2010-02-21
Envy is only for supported ATI and Nvidia drivers. You have an S3 Unichrome card

[color="red"]01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)[/color]

try the info here
[http://ubuntuforums.org/showthread.php?t=1340466](http://ubuntuforums.org/showthread.php?t=1340466)

---

### Post by Christopher Newtoit on 2010-02-21
thanks for the help, i'll take a look at that thread

---

