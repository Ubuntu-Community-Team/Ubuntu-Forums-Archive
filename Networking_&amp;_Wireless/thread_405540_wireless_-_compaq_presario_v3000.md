---
title: "wireless - compaq presario v3000"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by helane on 2007-04-09
please help...

i tried to search pots and followed some advices/tutorials for my laptop.
i am new w/ Linux and have no idea how to make wireless work...

i am desperate! :)

---

### Post by mrpaco on 2007-04-10
Open up a terminal and type in:

```
lspci
```

Copy and paste the output of that here.  I will be able to help you from there

---

### Post by llchyun on 2007-04-10
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
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
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
01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by mrpaco on 2007-04-10
> 01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

That's what I figured.  Broadcom cards are a pain. [Follow this howto]("http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom+howto").  It worked for me.  If you continue to run into problems post back here and we will go from there.

---

### Post by mrpaco on 2007-04-10
I think you in the same situation as the GP and his/her Compaq, so I'll go ahead and post this.
Broadcom cards are a pain. [Follow this howto]("http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom+howto").  It worked for me.  If you continue to run into problems post back here and we will go from there.[/QUOTE]

---

### Post by mrpaco on 2007-04-10
^^^ That was supposed to be an edit, sorry for the dupe.  ^^^

---

### Post by dracule on 2007-04-22
i have the same model of laptop and i have tried your how-to that you posted and

it worked for about 5 seconds then stopped.  now under network icon by the time, i have wireless networks listed (i didnt before i did teh tutorial), and it has mine listed. I connect and it says connection speed 11mbps (it should be ~54mbps) and stuff. but i cant connect to any websites. it alays says "looking up google.com" or other website.

---

### Post by dracule on 2007-04-23
can anyone help us (or maybe just me)

---

### Post by dracule on 2007-05-10
still not working. it connects but doesnt actually connect to the internet (just times out)

---

