---
title: "[SOLVED] wireless connection problem (no ping response)"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by muzehyun on 2008-11-27
1. It was running well until yesterday. Nothing has been changed.
2. Still well getting IP from router's DHCP.
3. router's log shows that wireless card's IP is assigned properly.

What can be the source of the problem?
Could wireless card be broken suddenly?

--- ifconfig wlan0

wlan0     Link encap:Ethernet  HWaddr 00:40:f4:94:36:95  
          inet addr:192.168.1.152  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe94:3695/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7052 (6.8 KB)  TX bytes:4800 (4.6 KB)
          Interrupt:19 Memory:ff9efc00-ff9efd00 

--- iwconfig wlan0

wlan0     IEEE 802.11b  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:88:A9:FA:C3   
          Bit Rate=11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:-171639040  Invalid misc:-109361886   Missed beacon:0

--- /etc/network/interfaces

iface wlan0 inet dhcp
wireless-essid default
wireless-mode managed
wireless-channel 6

--- down and up again

sean@sun:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6306
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:40:f4:94:36:95
Sending on   LPF/wlan0/00:40:f4:94:36:95
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67

sean@sun:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:40:f4:94:36:95
Sending on   LPF/wlan0/00:40:f4:94:36:95
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.152 from 192.168.1.1
DHCPREQUEST of 192.168.1.152 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.152 from 192.168.1.1
bound to 192.168.1.152 -- renewal in 249762 seconds.

--- ping

sean@sun:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.152 icmp_seq=1 Destination Host Unreachable
From 192.168.1.152 icmp_seq=2 Destination Host Unreachable
From 192.168.1.152 icmp_seq=3 Destination Host Unreachable
From 192.168.1.152 icmp_seq=4 Destination Host Unreachable

---

### Post by rlzyoner on 2008-11-27
It could be that the router is blocking pings, or that a firewall may be blocking you from pinging out.
Can you ping other places, google or whatever.
Also, can you telnet to the router on default port 23, if not, then this may indicate a firewall rule being the issue

---

### Post by muzehyun on 2008-11-27
I have XP desktop with wireless and it works just fine.
Ping and other things are good with XP machine.
ping to google is not working either in ubuntu.

---

### Post by muzehyun on 2008-11-28
I attached usb wireless and it worked.
So, I guess my wireless pci card is broken.
:)

---

### Post by muzehyun on 2008-12-01
My usb wlan1 is also stop working couple of days later.
So, I guess something block my device!!
I'm using comcast!!

I changed MAC address for my wlan0 and it works fine!!

---
auto wlan0
iface wlan0 inet dhcp
hwaddress ether 00xxxxxxxxxx
--

---

