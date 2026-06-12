---
title: "Broadcom B43 wireless doesnt see or connect to any networks"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by sxfx on 2008-09-23
Hey,

I have a strange problem where the system sees my wifi card but it doest want to connect to anything at all or detect any wifi networks. 

Here is a print out of my, uname-m, iwlist scan, lspci -nn as requested.

I have also tried using the proprietary drivers (Broadcom B43 wireless driver)  I have not yet tried running the windows drivers.  Any infor is appreciated thank you.

This is also on Ubuntu 8.04

> 
uname -m
i686


> 
iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results



> 
lspci -nn

00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)


---

### Post by Idefix82 on 2008-09-23
See if this helps you:
[http://ubuntuforums.org/showthread.php?t=190177]("http://ubuntuforums.org/showthread.php?t=190177")

The only thing is that you shouldn't have to install the network manager, so you can probably skip step 4.

---

### Post by Idefix82 on 2008-09-23
This might be even more relevant to you:
[http://ubuntuforums.org/showthread.php?p=4604505#post4604505]("http://ubuntuforums.org/showthread.php?p=4604505#post4604505")

---

### Post by sxfx on 2008-09-23
> **Idefix82 said:**
> This might be even more relevant to you:
[http://ubuntuforums.org/showthread.php?p=4604505#post4604505]("http://ubuntuforums.org/showthread.php?p=4604505#post4604505")

Ok gents so I followed these steps I even got the new network manager installed which is awesome.

I have the driver enabled in the Hardware drivers panel.  Every thing seems to be working except its not detecting any wireless networks.  I tried typing the name of it in and it wont connect.

Here is my ifconfig

> eth0      Link encap:Ethernet  HWaddr 00:16:d4:08:b7:ca  
          inet6 addr: fe80::216:d4ff:fe08:b7ca/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:129808 (126.7 KB)  TX bytes:14427 (14.0 KB)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60100 (58.6 KB)  TX bytes:60100 (58.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:a9:89:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-A9-89-B6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Let me know if you need any more information thank you.

---

### Post by Bucky Ball on 2008-09-23
This:

```
wlan0     Link encap:Ethernet  HWaddr 00:14:a5:a9:89:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          [quote]RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```Needs to look like this (from my ifconfig):

```
 Link encap:Ethernet  HWaddr 00:1a:73:2b:0e:9f  
         ** inet addr:192.168.0.162  Bcast:192.168.0.255  Mask:255.255.255.0**
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2585048 (2.4 MB)  TX bytes:383793 (374.7 KB)

```Are you attempting to connect with a router, and if so, do you have the correct details and security in there?

---

### Post by sxfx on 2008-09-23
Yes, its basically and open DHCP network here on my school campus.  My buddy right next to me right now with Vista is connected to it with out a problem.

I don't see it and even when I type in the ESSID manually and tell it its an infrastructure, no security network it gives me the lil animation connecting and then it says failed.

---

### Post by superprash2003 on 2008-09-23
please post your iwconfig output...think its a driver issue..you may want to try this too [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by sxfx on 2008-09-23
> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Going to try your suggested idea right now.

---

### Post by sxfx on 2008-09-23
Ok I'm almost there.  I went through the steps got NDIS Wrapper installed with having to recompile it with the extra steps then making it permanent.

And I used the Step 2C for Broadcom 4318 Rev2 :)..

---

