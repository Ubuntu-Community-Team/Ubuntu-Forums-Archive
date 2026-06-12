---
title: "TEW424-UB wireless NIC and F5D7230-4 router"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by ajirons97 on 2008-04-17
As you can see, I have a Trendnet TEW424-UB USB wireless dongle in my home-built AMD machine. I am trying to connect to the internet through a Belkin F5D7230-4 Wireless g Router. I have successfully installed the driver through ndiswrapper and my device is showing up in Network Manager. I have configured the essid (belkin54g), set security type (WEP key hex), put in my 10 digit   key, and set it for DHCP. Here is the output of iwconfig:
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
and here is ifconfig
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:57:AB:7D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1191381 (1.1 MB)  TX bytes:242748 (237.0 KB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3017 (2.9 KB)  TX bytes:3017 (2.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:D1:44:9D:7B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:14:D1:44:9D:7B  
          inet addr:169.254.7.94  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

I cannot get to my router settings (192.168.2.1) and i cannot connect to the internet though wireless (wired works fine). I have checked the router settings on my windows machine, and it has shown the ubuntu machine as connected with an IP and MAC address. At this point, it seems like a quick setting change on either the router or my machine will fix this, but I am very new to Linux (this is my first install) and don't know where to look.
If you need any more info, let me know, and thank you for your time. Looking forward to detaching myself from windows!

---

