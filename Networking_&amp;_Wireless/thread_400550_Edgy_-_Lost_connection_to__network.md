---
title: "Edgy - Lost connection to  network"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by mickcalcara on 2007-04-03
Please Help. I just lost connection to my home network.  I can ping out and the package manager still seems to work. However, Firefox, Thunderbird, my local mapped drives and ftp do not.

Thanks.

I am using the ndiswrapper with 'D-Link DWL-520 Wireless PCI Adapter Card'

Here are the vitals...

from ifconfig

ath0      Link encap:Ethernet  HWaddr 00:19:5B:6F:00:F5  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fe6f:f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31576 (30.8 KiB)  TX bytes:14926 (14.5 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-19-5B-6F-00-F5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14421 errors:0 dropped:0 overruns:0 frame:3638
          TX packets:330 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1238014 (1.1 MiB)  TX bytes:25402 (24.8 KiB)
          Interrupt:225 Memory:f8b00000-f8b10000 



cat /etc/network/interfaces

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


auto wlan0
iface wlan0 inet dhcp






iface ath0 inet dhcp
wireless-essid home

auto ath0

---

### Post by mickcalcara on 2007-04-03
I used wi-fi radar to find my network connection and it was able establish a connection. How would have done this via command line? Also  curious why ping would work but nothing else?  Anyway I am backup and running.

---

