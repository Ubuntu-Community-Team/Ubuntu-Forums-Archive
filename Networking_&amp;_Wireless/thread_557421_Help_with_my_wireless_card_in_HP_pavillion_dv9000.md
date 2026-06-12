---
title: "Help with my wireless card in HP pavillion dv9000"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by DOH on 2007-09-22
I've been trying to get my wireless card to work for a couple of days now and am beating my head against the wall in frustration. I followed darknoobs instructions to the t and now when i go into my network options it doesn't even show a wireless option. when i installed the firmware with the installer it looked like everything was fine.  I am really lost here.  I only started using ubuntu about 4 days ago.  I am dual booting currently with vista home and ubuntu 7.04. Any help on this would be greatly appreciated. Thanks in advance.

---

### Post by noob12 on 2007-09-22
Do you mean you used the automated installer from this thread [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)  ?  If not, try using that.

If so, you need to post these to see where you are now:

```

lspci -nn

sudo lshw -C network

iwconfig

sudo iwlist scan

```

Then if readers on this thread can't see anything, try posting back on that thread where the Broadcom 43xx experts are hopefully watching.

---

### Post by DOH on 2007-09-22
yeah thats the automated installer that I used.

here is what came up after i typed in the command lspci -nn

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 PCI Express Bridge [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 02)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Unknown device [1180:0832]
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:0843] (rev 01)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

---

### Post by DOH on 2007-09-22
*-network UNCLAIMED     
       description: Network controller
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:b6000000-b6003fff irq:255

lo        no wireless extensions.

eth1      no wireless extensions.

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

I'm really really new at this, so i don't know what most of this means...I really appreciate your help!

---

### Post by noob12 on 2007-09-22
This confirms you have a Broadcom 4311 device, which means that method should apply to you just fine.
```

03:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 02)

```

This tells us that whatever you did it didn't work to set up the driver.  The device remains UNCLAIMED, meaning no driver has claimed the device.
```

*-network UNCLAIMED
description: Network controller
product: Dell Wireless 1390 WLAN Mini-PCI Card
vendor: Broadcom Corporation
physical id: 0
bus info: pci@03:00.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: iomemory:b6000000-b6003fff irq:255

```

Did you get any errors when running their installer?  Did you run it using **sudo** ?

Try rerunning the installer from that thread with **sudo** and post back to them if the device remains UNCLAIMED like this.

You can get some additional diagnostics by posting the output of this:
```

cat /etc/modules

cat /etc/modprobe.d/blacklist

ndiswrapper -l

```

---

### Post by DOH on 2007-09-22
It works.  I used this how to post to help me wipe ndsiwrapper completely off my system.  then i used the installer again. It started right up and connected instantly.  thank you so much for your help..You have relieved the pain of this whole process.

---

