---
title: "Any Prize for the 1000th RT73 post? Nearly there..."
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by nodcero on 2007-06-16
My apologies for succumbing and opening yet another one on that sore subject, but I'm more or less successfully running Feisty Fawn 7.04 on an old Desktop, and for 4 days I have been fighting to get a wireless connection with an Asus WL-1676 USB Adapter, which I had been using with comparative ease with a Puppy-Linux distribution.

Following all sorts of threads and HOW-TOs I have amongst others:
got rid of the network manager
installed the RT73
edited /etc/network/interfaces and others
and have religiously done all sort of things as advised for example in
[URL="http://ubuntuforums.org/showthread.php?t=447305"]

All sounds good and looks well, up to the point where iwconfig returns

> rausb0      RT73 WLAN   ESSID:""   Nickname:""
                   Mode:Auto Frequenzy=1MB  Bit Rate=54 Mb/s
                   RTS thr:off Fragment thr:off

and nothing let's me change the essid or set a key, neither with the startup scripts nor manually later.

I hope this helps the ones in the know:
> 
lsusb
Bus 001 Device 002: ID 0b05:1723 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 0000:0000


iwlist rausb0 scan
rausb0    Scan completed :
          Cell 01 - Address: 00:16:E3:4A:37:21
                    ESSID:"BTVOYAGER2091-21"
                    Mode:Managed
                    Channel:1
                    Encryption key:on
                    Bit Rates:0 kb/s

ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11600 (11.3 KiB)  TX bytes:11600 (11.3 KiB)

rausb0    Link encap:Ethernet  HWaddr 00:1A:92:59:4A:F3  
          inet6 addr: fe80::21a:92ff:fe59:4af3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1000004 (976.5 KiB)  TX bytes:998766 (975.3 KiB)

sudo dhclient3 rausb0
There is already a pid file /var/run/dhclient.pid with pid 5661
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/rausb0/00:1a:92:59:4a:f3
Sending on   LPF/rausb0/00:1a:92:59:4a:f3
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping

Any hint's highly appreciated...

Regards
Nodcero

EDIT: One more day and fifteen threads later: Solved :)

---

### Post by rnmartinez on 2007-07-05
I'd like to know too - network-manager sees rausb0 as a wired network and won't take any settings?

---

