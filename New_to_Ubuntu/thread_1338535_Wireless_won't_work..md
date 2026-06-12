---
title: "Wireless won't work."
date: 2009-11-26
forum: New to Ubuntu
---

### Post by amarumayo on 2009-11-26
Hi all,

I have a compaq presario v5015 that I just put ubuntu 9.04 on.  I have no wireless.  I enabled b43-fwcutter.  Any ideas why I can't connect or what I could do?

Thanks
Chris

---

### Post by mbzn on 2009-11-26
Hi, Please post the outputs of:

lspci
ifconfig

---

### Post by amarumayo on 2009-11-26
bluesky@Renpro:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
bluesky@Renpro:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:32:ad:bc  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe32:adbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7624982 (7.6 MB)  TX bytes:768700 (768.7 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:750 (750.0 B)  TX bytes:750 (750.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:6f:e6:7e  
          inet6 addr: fe80::214:a5ff:fe6f:e67e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10255 (10.2 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:14:a5:6f:e6:7e  
          inet addr:169.254.8.186  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-6F-E6-7E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

bluesky@Renpro:~$ 
Thanks

---

### Post by mbzn on 2009-11-26
Your computer does recognise the wireless, how did you try to connect?

also try reading through here:
[https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html](https://help.ubuntu.com/8.04/internet/C/wireless-connecting.html)

---

### Post by coffeecat on 2009-11-26
This is relevant:

> **amarumayo said:**
>  wlan0:avahi Link encap:Ethernet  HWaddr 00:14:a5:6f:e6:7e  
          inet addr:169.254.8.186  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

IP addresses in the 169.254.x.y range mean a failure of the DHCP server or a failure to connect to the DHCP server - [APIPA]("http://compnetworking.about.com/cs/protocolsdhcp/g/bldef_apipa.htm") in Windows speak. Or the [link local block]("http://www.rfc-editor.org/rfc/rfc3330.txt") as defined by IANA.

> 169.254.0.0/16 - This is the "link local" block.  It is allocated for
   communication between hosts on a single link.  Hosts obtain these
   addresses by auto-configuration, such as when a DHCP server may not
be found.I'm sorry but I have no experience of Broadcom wireless so I can't help any further, but I thought I would point that out to bump the thread so that someone with Broadcom experience could help.

---

### Post by amarumayo on 2009-11-26
Anyone with broadcom experience have any idea what is going on?  Thanks
Chris

---

### Post by coffeecat on 2009-11-26
Just came across this. There's some useful information in post #3 in this thread:

[http://ubuntuforums.org/showthread.php?t=1334906](http://ubuntuforums.org/showthread.php?t=1334906)

---

