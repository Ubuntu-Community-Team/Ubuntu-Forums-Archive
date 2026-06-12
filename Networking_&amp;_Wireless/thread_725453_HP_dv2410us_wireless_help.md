---
title: "HP dv2410us wireless help"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by jtdelasalas on 2008-03-15
I was able to successfully install ubuntu onto my laptop and got everything to work but wireless.  I tried using ndiswrapper, but I'm pretty sure I lack the acumen to use it properly. A while ago I had to have a friend install it, but on my own, ndiswrapper is dauting and a mess hell.

Is there anyone who has the same laptop and can help me in the most verbose and easy fashion?

---

### Post by myddewji13 on 2008-03-15
see my signature...

---

### Post by jtdelasalas on 2008-03-15
I'm not sure what's going on on step five.

I found a link to my driver:
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-53245-1&lc=en&cc=us&dlc=en&product=3439333&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-53245-1&lc=en&cc=us&dlc=en&product=3439333&os=228&lang=en)

Could you elaborate on step 5?

---

### Post by myddewji13 on 2008-03-16
for step 5 you are opening up the command line (aka terminal)...an alternate way to run terminal would be to hit alt+f2 and then type in 'gnome-terminal' ... also a note on the drivers...once you download the .exe file extract it using file roller (double click... if u dont have wine installed it should default to file roller)... oh yea one more thing...if the driver is bcmwl6.inf then its for vista and probably wont work.... (atleast in my experience)......you need xp drivers (or lower)

PS... what card do you have?

---

### Post by jtdelasalas on 2008-03-16
I'm not actually sure what kind of wireless card I have.  I'm back using Windows Vista until I can figure out ndiswarpper 

I have an HP dv2410us

---

### Post by myddewji13 on 2008-03-16
open up terminal...type in 'lspci' ... post the output...

---

### Post by jtdelasalas on 2008-03-19
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by jtdelasalas on 2008-03-19
I set up my wireless, but now sound is an issue.  I'm posting a thread in the proper forum

---

