---
title: "Having trouble getting speakers to work after re-install"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by boddingtons on 2011-06-17
Hello everyone, 

I am having trouble getting some speakers to work after I have re installed Ubuntu 10.4 LTS.

Back Story and Problem
The back story is that I upgraded to 11.4 but was told that the "Input  format not supported". So I did a clean install of 10.4 again with  universal U.S.B. And this is what I am now working on. I keep backups  regularly so it wasn't a problem, and the computer is less than a year  old anyway.

The problem is that the speakers worked fine on the old install of 10.4,  so far as I can tell it is the same this time around, only now I can't  get anything out of them. The speakers themselves seem to be fine, they  work on my windows laptop.

Technical Specifications

lspci
william@william-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control

Speaker Specification

PC World essentials
2.0 PC Speakers
RMS: 1W
Speaker Driver Unit: 2.25" 4<Omega Symbol> x 2
They run on U.S.B. power and a 3.5mm jack.

Computer
This is the computer itself, I have not yet had to opportunity to modify it.
[http://www.overclockers.co.uk/showproduct.php?prodid=FS-265-OK](http://www.overclockers.co.uk/showproduct.php?prodid=FS-265-OK)

Motherboard is S-Series M68MT-S2

Contacting Me
I should be on this forum all evening, my email is [EMAIL="w.g.slater@ncl.ac.uk"]w.g.slater@ncl.ac.uk[/EMAIL],  I am also a redditor, boddigntons, if you need to PM me.

Thank you in advance for any help you can offer, I am very appreciative.

---

### Post by wildmanne39 on 2011-06-17
> **boddingtons said:**
> Hello everyone, 

I am having trouble getting some speakers to work after I have re installed Ubuntu 10.4 LTS.

Back Story and Problem
The back story is that I upgraded to 11.4 but was told that the "Input  format not supported". So I did a clean install of 10.4 again with  universal U.S.B. And this is what I am now working on. I keep backups  regularly so it wasn't a problem, and the computer is less than a year  old anyway.

The problem is that the speakers worked fine on the old install of 10.4,  so far as I can tell it is the same this time around, only now I can't  get anything out of them. The speakers themselves seem to be fine, they  work on my windows laptop.

Technical Specifications

lspci
william@william-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control

Speaker Specification

PC World essentials
2.0 PC Speakers
RMS: 1W
Speaker Driver Unit: 2.25" 4<Omega Symbol> x 2
They run on U.S.B. power and a 3.5mm jack.

Computer
This is the computer itself, I have not yet had to opportunity to modify it.
[http://www.overclockers.co.uk/showproduct.php?prodid=FS-265-OK](http://www.overclockers.co.uk/showproduct.php?prodid=FS-265-OK)

Motherboard is S-Series M68MT-S2

Contacting Me
I should be on this forum all evening, my email is [EMAIL="w.g.slater@ncl.ac.uk"]w.g.slater@ncl.ac.uk[/EMAIL],  I am also a redditor, boddigntons, if you need to PM me.

Thank you in advance for any help you can offer, I am very appreciative.
Hi, click on the speaker in the top right corner and make sure nothing is muted,when I installed it was muted by default. Also go into sound preferences you may have to change a setting for your system.

---

