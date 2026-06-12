---
title: "Where to find a driver."
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by ErusGuleilmus on 2008-01-28
Google did not shed any light on where I could download the bcmlw5 driver(s). I found in some other Linux forums that this is a common Dell driver, but could not find it on there website. If you know where it is at, could you please give me a link to a download? Thank You!

---

### Post by Seisen on 2008-01-28
Do you have the cd for you wireless card?

---

### Post by NullHead on 2008-01-29
Here is some I use. Yes the folder name does say bcm4318, but they WILL work for any card that needs bcmwl5.inf & .sys

EDIT: Don't bother with the script located inside the folder ... it's designed for edgy.

---

### Post by ErusGuleilmus on 2008-01-29
Thank you both. I do have the CD that came with this laptop, but it has the sixth version of the driver, and from both some research and first hand experience I have found to not work. I will give the provided driver a try. Thanks again!

---

### Post by ErusGuleilmus on 2008-01-29
Neither the 64bit(I use 7.10 64bit) nor the 32bit driver seems to work.After installing both, I did a reboot. The problem appears to be that it doesn't detect my card. If it helps at all, the laptop that I am trying to make wireless work on is a Compaq Presario F572US. Thanks.

---

### Post by NullHead on 2008-01-29
OK copy and past the output of lspci into a post here. Also you need bcm43xx blacklisted and rmmoeded to let ndiswrapper work.

So to blacklist bcm43xx```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```
and because of a bug with ndiswrapper you need to manually load ndiswrapper at boot. So to make it automatically load you just need to do this.```
echo 'ndiswrapper' | tee -a /etc/modules
```

---

### Post by ErusGuleilmus on 2008-01-29
The output of the lspci command:

> william@LINUXLAPTOP:~$ lspci
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
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
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
william@LINUXLAPTOP:~$ 



---

### Post by ErusGuleilmus on 2008-01-29
When I enter "echo 'ndiswrapper' | tee -a /etc/modules", I get a permission denied, I did try putting "sudo" at the beginning, with the same results.

---

