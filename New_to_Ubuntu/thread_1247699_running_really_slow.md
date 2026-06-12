---
title: "running really slow"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by wordmaster on 2009-08-23
Hello,

I updated to Ubuntu 9.04 and everything is slow. Takes a long time to start any application, youtube movies just stop or at best jerk from frame to frame, sometimes even typing, I have to wait to  see the characters show up.

I am running an ASUS mb with the Splashtop linux that lets you jump right in and do things within seconds of turning your computer on. If I go into that, things run as fast as normal, movies play, etc. This makes me believe it is not a hardware problem or a connection problem. BTW, I have a 3gb internet connection and according to online speed tests, it is working as it should.

Any and all help appreciated.

---

### Post by wordmaster on 2009-08-23
BTW, that should have been 3Mb internet speed instead of 3Gb.

---

### Post by Old_Grey_Wolf on 2009-08-23
What graphics card do you have?

---

### Post by argos3016 on 2009-08-23
I was have the same problem and I solved creating another session.

---

### Post by Old_Grey_Wolf on 2009-08-23
9.04 has a known problem with some graphic cards. It causes the computer to run slow. There are ways to get them working. In the terminal type ```
lspci
``` and post the results. After we know what graphics card you have, we can determine if it is the problem, and work from there.

---

### Post by wordmaster on 2009-08-23
OK, here is what I got from lspc

p@p-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7050 PV / nForce 630a (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
01:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
01:07.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)

---

### Post by Old_Grey_Wolf on 2009-08-23
OK.

You have the GeForce 7050 PV / nForce 630a graphics card. I'm going to go to sleep now; however, continue to check this thread. Someone may be able to help you. 

I did a search for your graphics card but didn't find any fixes that seemed credible.

Sorry if I have killed your thread by replying. Sometimes we look for unanswered posts or those with few replies when we are trying to help others. Other helpful people may ignore this thread because it got a reply.

Sorry!

I will be back in about 20 hours.

---

