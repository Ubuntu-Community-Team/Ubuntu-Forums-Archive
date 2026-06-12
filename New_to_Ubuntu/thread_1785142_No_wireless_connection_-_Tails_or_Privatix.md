---
title: "No wireless connection - Tails or Privatix"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by gambang07 on 2011-06-17
I tried anonymous Live CDs: Tails and Privatix. The problem is I can't even make the wireless connection work. It simply refuses to get connected. Do they work only with Lan cable? No available wireless networks appear (even there are in my location when using other PC). The message is always saying something like 'disconnected'.

---

### Post by wildmanne39 on 2011-06-17
> **gambang07 said:**
> I tried anonymous Live CDs: Tails and Privatix. The problem is I can't even make the wireless connection work. It simply refuses to get connected. Do they work only with Lan cable? No available wireless networks appear (even there are in my location when using other PC). The message is always saying something like 'disconnected'.
Hi, you have install the drivers for most wireless cards, and it is done when you install to the hard drive, if you went through the trouble of doing it while running a livecd you would have to do it every time you restart your system.
I can not be of more help because I do not what anonymous Live CDs: Tails and Privatix are.

---

### Post by jtarin on 2011-06-17
Let's see what wireless card you have. Post the results from the command in the terminal of ```
lspci
```Also.....do you have a hard wired connection for Ubuntu that works?

---

### Post by gambang07 on 2011-06-18
Thanks for your response. Actually it is OK now after changing another wifi dongle though each of them can be detected without installing drivers. These two live cd's is for anonymous browsing.


amnesia@amnesia:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by wildmanne39 on 2011-06-18
Hi, ok that is good, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

