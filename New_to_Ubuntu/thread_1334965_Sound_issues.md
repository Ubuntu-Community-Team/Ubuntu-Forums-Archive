---
title: "Sound issues"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Howard Roark on 2009-11-23
Hay guys, anyone out there Know what: pulseaudio[1893]: ratelimit.c: 1510 events suppressed could possibly mean? I got it of of sys log and as I would imagine most of you out there could guess my audio isn't working. I don't know if it's my sound card my driver or my BIOS settings any suggestions as to what I can do to find out
Thanks

---

### Post by mgranet on 2009-11-23
Can you post the output of ```
lspci
```

---

### Post by Howard Roark on 2009-11-23
-desktop:~$ lspci
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
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
04:06.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
04:08.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

---

### Post by mgranet on 2009-11-23
You may want to look into the following thread:
[http://www.uluga.ubuntuforums.org/showthread.php?t=1308034]("http://www.uluga.ubuntuforums.org/showthread.php?t=1308034")

---

### Post by Howard Roark on 2009-11-23
*[sudo apt-get install pulseaudio]* solved my issue of no sound after switching to *Karmic* 
Howard Roark

---

