---
title: "[SOLVED] Broadcom Wireless Troubles"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by suzypeppercorn on 2008-04-30
I am very new to linux and i am having a hard time adjusting from windows. I just installed ubuntu 8.04 on monday and i am loving everything except the wireless internet.

I have tried around 5 different guides on how to get my wireless working and to no avail.

My computer is a hp laptop model dv6448se.

I am going to take a break until friday because i have a lot of work to do for school. But can anyone give a plan on how to get my wireless working. I can give you any needed information about the model number of my card if you could tell me how to get it.

I'm just completely lost on how to do this. I will check back tonight if anyone would need any more info about my computer.

thank you for any help.

---

### Post by ToM-X on 2008-04-30
As you did not give the wireless card name and it wasn't on HP's website this may not work.

This has been reported working with your laptop.

```
http://ph.ubuntuforums.com/showthread.php?t=405990
```

---

### Post by suzypeppercorn on 2008-04-30
no go on that method.

whats the command so that i can tell you what type and version of card i have.

thank you for your patience. i'm trying my best and i would really love to mess around with linux and learn more but its frustrating not having an internet connection.

---

### Post by ToM-X on 2008-04-30
Open the terminal and paste:

```
lspci
```

Then paste the results.

---

### Post by suzypeppercorn on 2008-04-30
heres the printout from the terminal:

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
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

what do you think?

---

### Post by ToM-X on 2008-04-30
Right, It *may* be your lucky day, the card has been reported working fine with ndiswrapper.

Try:

```
http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/
```

Report back.

---

### Post by suzypeppercorn on 2008-04-30
ladies and gentlemen. after years of searching. we got em.

i followed this guide to the T.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

It looks like it will work for a variety of cards. Thank you for all your help. I'm so excited to finally use ubuntu for the majority of my work.

---

