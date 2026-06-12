---
title: "Need Help Enabling Wireless On An Old IBM Thinkpad"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by rockerphil on 2009-11-06
ok, the title pretty well says it all, but here's a quick rundown of the situation. i recently got my hands on an older IBM Thinkpad 2647 running 128 MB of RAM, a (i think) 700 MHz Intel Pentium III processor and a 30 GB SCSI HDD. seeing as the resources are pretty limited i did what i normally do with a machine this old and installed a minimal DE using the Ubuntu 8.04 minimal ISO to install a CLI then built the DE using Fluxbox as the WM, feh and idesk for desktop icon rendering, XDM as a display manager, rox-filer as the file manager and several other lightweight apps to round off the OS. now, here's where it gets tricky. i want to enable the wireless card, but have no network manager installed in which to make it easier. here's the outpupt of lspci:

```
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM)
```

i'm pretty sure that the machine has an internal wireless card since the Firestarter firewall GUI picks up two interfaces, the first being eth0, the second being irda0. i've searched around on Google, but i can't seen to make heads or tails of what to do. any help is appreciated, and if more information is needed please feel free to ask. much thanks in advance,

Phil

---

### Post by louieb on 2009-11-06
Have you looked at [ThinkWiki - Linux ThinkPad Wiki]("http://www.thinkwiki.org/wiki/ThinkWiki")

Easy enough to see if it has a internal wireless card. There is a plate on the bottom 2 screws uncover a mini-pci slot.  Probably an Intel or cisco card.  

Sound like you  have a T2x maybe a T21 or T22.  I have a T30 - wireless has always worked out of the box.    

 Thinkpads are easy laptops to work on and there is good documentation at the lenovo site (even for the older models) 

Another good place to get info [ThinkPad Forum]("http://forum.thinkpads.com/")

---

