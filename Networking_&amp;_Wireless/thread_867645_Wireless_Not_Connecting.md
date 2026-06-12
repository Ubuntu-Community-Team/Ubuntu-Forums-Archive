---
title: "Wireless Not Connecting"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by craigmarti on 2008-07-23
Hi all,
     I am a n00b to Linux and I am attempting to install Ubuntu 8.04 linux on my desktop (Old sony Vaio).  For some reason my wireless networking doesn't seem to want to connect.  After much trouble with the ndiswrapper I think that I have it installed properly.  I can now see the wireless networks that are available but I am not able to connect to them.  For some reason I cannot get an ip address (DHCP).  I even tried to use a static ip and that didn't work either.  I even turned off the WPA key for my router and that didn't do anything.  I am kind of stuck.  Do any of you gurus have any suggestions on things to try or have you seen this before?  Thank you in advance.

Craig


System Specs
Ubuntu 8.04
Buffalo Air Navigator Wireless PCI Card
Netgear Router WNR3500

Result of Ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:e0:18:3d:59:fe  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fe3d:59fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2841 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3635078 (3.4 MB)  TX bytes:396713 (387.4 KB)
          Interrupt:16 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4007 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4007 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200844 (196.1 KB)  TX bytes:200844 (196.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0d:0b:cf:19:9d  
          inet6 addr: fe80::20d:bff:fecf:199d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10622 (10.3 KB)  TX bytes:26424 (25.8 KB)
          Interrupt:16 Memory:f7000000-f7002000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:0d:0b:cf:19:9d  
          inet addr:169.254.6.6  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:f7000000-f7002000 


**Note:  I am a little confused as to why I am getting two wlan's (wlan0 & wlan0:avahi)**


Result of Command:  sudo ndiswrapper -l

bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

---

