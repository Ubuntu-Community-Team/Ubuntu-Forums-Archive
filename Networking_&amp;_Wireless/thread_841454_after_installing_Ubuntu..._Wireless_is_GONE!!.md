---
title: "after installing Ubuntu... Wireless is GONE!!"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by ohbin on 2008-06-26
I just installed ubuntu on my laptop yesterday... so i'm like thebiggest noob... 

but i partitioned the disk for ubuntu and installed it there, so I'm dual booting with Ubuntu and XP On Ubuntu, 

it automatically installed the wireless driver for me.. 
then I switched back to XP, and it doesnt have the wireless adapter anymore 

There is a switch that I can turn on/off the wireless reciever, and usually, even if I dont have the driver installed, it turns blue when it's on.

But now it's only showing red... I tried re-installing the driver on XP, and uninstalled it on Ubuntu but nothing seems to work. 

I really need wireless on my XP, and I'm afraid to do system restore,cuz then it might mess my partition that i did yesterday  

Does anyone have a clue what happened to my wireless driver??? 

Thanks in advance  

ps. wireless didnt even work on Ubuntu

I'm on an HP Pavillion laptop

---

### Post by chalewa on 2008-06-26
that's weird... i don't think that installing ubuntu should have done anything to your xp wireless. 

did you try to manually reinstally the driver in xp? what kinda card is it?

---

### Post by jualin on 2008-06-26
The first step is to tell us what kind of wireless card do you have. To know this type on the terminal > lspci

---

### Post by ohbin on 2008-06-26
After looking at this for a while.. I realized I dont even have a wireless adapter

I remember having it one time, and i uninstalled it


But here is what i get..

Am I missing a wireless driver

Thanks in advance


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
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by jualin on 2008-06-26
I am not sure if I am understanding you correctly, do you have a wireless adapter in your computer?. According to your lspci results you don't seem to have one. And like chalewa said, Ubuntu doesn't uninstall anything from Windows so it should be mere coincidence.

---

