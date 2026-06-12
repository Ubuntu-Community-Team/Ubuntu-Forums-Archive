---
title: "Realtek RTL8185 issues"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by dlbrando on 2008-04-01
My wireless card has a couple of weird glitches at the moment.  It works, but does not connect securly.  And It does not ever display signal strengh.  It also seems to have problems connecting reliably to any wireless signal at school some days.  I can sit 10 ft from the transmitter and not get any results. 

Should I be looking into ndiswrapper or some other sort of program, or should I look at a different solution?

It is an Emachines N-10 running 7.10 with the recent partial upgrade.  

link to gateway specs for the card:
[http://support.gateway.com/s/Mobile/eMachines/StormE/105825/105825sp2.shtml](http://support.gateway.com/s/Mobile/eMachines/StormE/105825/105825sp2.shtml)

thanks for any help.

---

### Post by dstew on 2008-04-01
Open a terminal window (Applications --> Accessories --> Terminal) and enter the commands```
lspci
ifconfig
iwconfig
```Post the results to the forum.

---

### Post by dlbrando on 2008-04-01
lspci:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:03:25:30:9C:29  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe30:9c29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3671198 (3.5 MB)  TX bytes:446169 (435.7 KB)
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:C0:A8:B8:E1:BD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:941 errors:284 dropped:196 overruns:0 frame:0
          TX packets:1466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79744 (77.8 KB)  TX bytes:61572 (60.1 KB)
          Interrupt:11 Memory:f8938000-f8938100 

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.417 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Also, most of the stuff I have been tweaking and installing I have been using the 32bit stuff and it works fine, but I see a lot of 64bit spots in my code in places..

thanks for the help

---

### Post by dlbrando on 2008-04-01
and I am hardwired in my Apt at the time of typing this if that makes a difference on the output

---

### Post by dstew on 2008-04-01
It looks like your native linux driver has detected the card, and it is running. I don't know how to help you exactly, except by trying things. Look at your System --> Administration --> Networking window, select wlan0 and click properties. If roaming is checked, uncheck it. You don't need this "feature", and it can sometimes cause problems. If this doesn't help, you might try ndiswrapper with a windows driver.

---

