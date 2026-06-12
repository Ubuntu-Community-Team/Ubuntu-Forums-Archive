---
title: "help with broadcom ndiswrapper setup"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by danieljay on 2006-11-26
I am working on trying to setup my new laptop with Edgy Eft and have configured most of the system. My specs are:
Compaq v3000z
AMD Turion 64 X2 1.6Ghz
1GB Ram
100 GB HD
14.1 Widescreen (1280x800)
I have the internal wifi and bluetooth card.

I have configured it with the nvidia drivers and have been referencing easylinux.info website for some help when things don't work. I am trying to get my wifi card to work. I found: [this site]("http://starbase-12.blogspot.com/2006/09/compaq-presario-v3000-with-ubuntu-606.html"), which talks about how this guy got his v3000 broadcom NIC installed. Following the steps on his post have not worked. I have also searched the forums for other help, but nothing has worked.

My lspci is:
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
[COLOR="Red"]01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)[/COLOR]
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:09.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

I see the Broadcom network controller but it does not recognize it. 

When I run ndiswrapper -l it says:
bcmwl5 driver installed, hardware present

Yet when I run ifconfig or iwconfig it does not show any new network adapters. 

Does anybody have any other ideas?

---

### Post by skale on 2006-11-26
I've got the same problem. I am going to try anc compile the ndiswrapper v 1.28.  I have the same driver, and know it works.  Right now, I think the newer version of ndiswrapper will work.  My thread:
[http://ubuntuforums.org/showthread.php?t=307582](http://ubuntuforums.org/showthread.php?t=307582)

I will try that and see if it works, and post. I have 4306 and you have 4310, but I don't think there is a really big difference.

As I said in the other thread,  I got it to work in Arch Linux, using the newer ndiswrapper, so I'll try that.
Good luck!

And if you figure out the problem, could you post the answer?

---

### Post by wmatlock on 2006-11-26
danieljay,

See my reply to Skale or go to this link and search for the article on a BCM4318 card. It give step by step instructions that worked for me. Oh it has been mentioned by other that they were having problems with AMD64 machines but I am running Dapper on a AMD64 Dual Core. I am running a K7 SMP Kernel. The link is as follows: [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Good Luck

---

### Post by skale on 2006-11-27
Yeah, It works.  I didn't use the script, but I did use the drivers.  So I guess the problem was the drivers.  However, earlier I did get it to work with the newer version of ndiswrapper from source and everything.  However, I got rid of it because compiled-from-source progrms are sometimes a pain to get rid of, and clutter up my desktop.  I suppose in the new version they added support for the driver I had.  

If only Dell switched to 3com or something, I heard they are the easiest to get working under linux.

---

