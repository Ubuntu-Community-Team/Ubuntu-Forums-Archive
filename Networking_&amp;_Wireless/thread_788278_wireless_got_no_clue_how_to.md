---
title: "wireless got no clue how to"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by zagloba on 2008-05-09
Hi all Im not tottal noob but can't get my wireless to work been trying all
I know and read here on the forum .
Ok I got compaq presario f500 with broadcom  BCM94311MCG wlan mini-PC
and this is my out put when i do ifconfig wlan0
 sudo ifconfig wlan0 
wlan0: error fetching interface information: Device not found
also this is the output for the lspci -nn
peter@peter-laptop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f3] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation MCP51 PCI-X GeForce Go 6100 [10de:0247] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02)

so I can see my card for the wireless is there, but how do 
I get it to work?

---

### Post by .rdg on 2008-05-09
> **zagloba said:**
> Hi all Im not tottal noob but can't get my wireless to work been trying all I know and read here on the forum .
Ok I got compaq presario f500 with broadcom  BCM94311MCG wlan mini-PC
and this is my out put when i do ifconfig wlan0
 sudo ifconfig wlan0 
wlan0: error fetching interface information: Device not found
cut ...

so I can see my card for the wireless is there, but how do 
I get it to work?

Try doing ifconfig without specifying the interface - there probably is no wlan0 interface as is stated in your post (device not found). Perhaps its name in system is different?

Regards,
.rdg

---

### Post by zagloba on 2008-05-09
ok "lo" is my wireles and eth1 is my wire so now what can I do
to get the wireless working plz help.

---

### Post by .rdg on 2008-05-10
The lo interface is just loopback - a virtual one, so you can test networking inside your own host. Please post what: ifconfig -a is printing out, so woe could say more.

Also - did you try setting up wireless with gnome's Network Manager?

---

### Post by Ayuthia on 2008-05-10
Your wireless card does not work out of the box in Ubuntu.  The b43 driver is not quite ready for your card yet, so NDISwrapper is the way to go.

Here is a link that might help you get started.  It uses NDISwrapper.  

[http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

Hope that helps.

---

### Post by zagloba on 2008-05-10
thx will try that thread this weekend
and if all goes good we will have 4 more new ubuntu happy
users with wireless connection :)

---

