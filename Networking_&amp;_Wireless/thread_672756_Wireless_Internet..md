---
title: "Wireless Internet."
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by Snakeyes11 on 2008-01-19
Hi Everyone. I am a currently using Microsoft Windows Vista. I personally think it's slow. That being said, I have gusty Gibbon 7.10 and I would like to use it wirelessly but I can't seem to get it to work. I am not sure what kinda of wireless card I have in my laptop but It would be great if someone could help me out. I have tried ndiswrapper, But had trouble downloading it. 

Thank you 

 - Snake - 


:)

---

### Post by RomeReactor on 2008-01-19
Hi. Can you get a wired internet connection to your system? IF so, you can install ndiswrapper by opening Synaptic (System->Administration->Synaptic) and searching for the following packages:

* ndiswrapper-common
* ndiswrapper-utils-1.9
* ndisgtk

Or to install them from the terminal (Applications->Accessories->Terminal):
```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```

If you can't get a wired connection, then download these packages in windows:

* [URL="http://mirrors.xmission.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb"]ndiswrapper-common
[/URL]* [ndiswrapper-utils-1.9]("http://mirrors.xmission.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb")
* [ndisgtk]("http://mirrors.xmission.com/ubuntu/pool/universe/n/ndisgtk/ndisgtk_0.7.2-1ubuntu1_i386.deb")

Transfer them to Ubuntu, then double-click on each to install them, in the order posted above. Once they're installed, you can find it in 'System->Administration->Windows Wireless Drivers'.

To proceed, we need to know what wireless card you have; from the terminal, paste the following:
```
lspci
```
press ENTER, and post the output.

---

### Post by Snakeyes11 on 2008-01-20
Yes I can get a wired signal on my laptop. I will try downloading that and i'll see what will happen. Thanks for the information.

---

### Post by jeffbray on 2008-04-16
I don't mean to jump in to this mediation here, but so far your advice has been the most promising. I've done what you said, and in the driver installation program I've got my driver installed (i found out which i needed from other threads), and it says "Hardware present: Yes"

I don't want to make any mistakes, so what should I do next?

(also, here is the readout to the lspci command you told Snakeyes11 to use:

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
)

Thanks
Jeff

---

