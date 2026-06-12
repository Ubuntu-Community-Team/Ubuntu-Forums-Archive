---
title: "Wifi Issue"
date: 2015-01-26
forum: Networking &amp; Wireless
---

### Post by ruby4 on 2015-01-26
Hello Ubuntu community,

Last week I installed Ubuntu 14.04 on my mac as the primary Os on the drive. After the installation was complete I noticed that the WiFi function was lost (doesn't allow me to scan and enter the password) but I do have the ability to plug in directly and works very efficiently. Do any of you know how to fix this problem? Any help will be greatly appreciated.

These are the specs  
Memory: 7.5 GiB
Processor: Intel® Core™2 Duo CPU T9600 @ 2.80GHz × 2
Graphics: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OS: 64-bit
Disk: 484.0 GB

Thanks,
Ruby

---

### Post by jeremy31 on 2015-01-26
You could start by opening a terminal window and enter ```
lspci -nnk | grep -iA2 net
``` and pasting the results

---

### Post by ruby4 on 2015-01-26
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
	Subsystem: NVIDIA Corporation Apple iMac 9,1 [10de:cb79]
	Kernel driver in use: forcedeth
--
04:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
	Subsystem: Apple Inc. AirPort Extreme [106b:008d]
	Kernel driver in use: b43-pci-bridge

---

### Post by Hadaka on 2015-01-26
Hi, please do..
```
sudo apt-get remove --purge firmware-b43-installer
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
thanks

---

### Post by ruby4 on 2015-01-26
WOW thank you very much it worked!!!

---

### Post by Hadaka on 2015-01-27
Hi, Jeremy31 and i are pleased that worked for you.
please use thread tools to mark your thread solved
thanks.

---

