---
title: "Wireless issues since upgrade to Intrepid"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by Pa100ka on 2008-11-19
Hi,

I have a Toshiba laptop with an RTL8187b. Under 8.04 I used the datanorth patch, which seemed to work flawlessly, except that the notification area icon always showed 30% (as documented).

After upgrading to 8.10 - which apparently has RTL8187b support built in - I undid the datanorth stuff, and let Ubuntu get on with it. At first all seemed well - the notification area icon goes up and down, usually between 56% and 100%, and the internet connection seemed fine. I reconfigured it to use a fixed IPv4 address (192.168.1.3) which no other device is using.

But now, it seems to drop the connection overnight. The laptop reports connection to my home router as up, but there is no internet connection. Rebooting the laptop restores the internet connection.

Here is the output from iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"daddysnetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:A1:B9:B6   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-17 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Here is the output from ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:e9:45:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16024 (16.0 KB)  TX bytes:16024 (16.0 KB)

wlan1     Link encap:Ethernet  HWaddr 00:16:44:a9:9c:bb  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fea9:9cbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:543729 errors:0 dropped:0 overruns:0 frame:0
          TX packets:383717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:719973945 (719.9 MB)  TX bytes:101852174 (101.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-A9-9C-BB-63-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Can anyone help?

Thanks,
Pa100ka

---

### Post by befana on 2008-12-22
Can anyone help?
I have the same problem, plus a kernel panic when stopping my rtl8187b, i.e. keybord led indicators flashing, and nothing to do but a hard shutdown.
Please, help!

---

