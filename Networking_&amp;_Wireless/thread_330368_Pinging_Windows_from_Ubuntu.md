---
title: "Pinging Windows from Ubuntu"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by mevets on 2007-01-03
I cannot see my windows pc from ny ubuntu laptop and vice versa. I have tried going into System > Administration > Network Tools and under the Ping tab I have attempted to connect to the correct ip of the win computer.

What issue could I be having? Is it a firewall issue on linux or win maybe?

---

### Post by Iowan on 2007-01-03
Perhaps a few more details...:-D 
Connection: Crossover cable, hub, switch, wireless?
Address: Fixed or via DHCP?
The network is active on Ubuntu? (Post **ifconfig**, and contents of **/etc/network/interfaces**)

---

### Post by mevets on 2007-01-03
I can tell you I am on a wireless network encrypted with WPA.

DHCP is used to give both machines an IP.

I will do the ipconfig when I get home and provide those details.

Hopefully this helps answer my question!

---

### Post by mevets on 2007-01-03
IFCONFIG:
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:C0:CA:05  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:54:12:D7  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe54:12d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14919 errors:1 dropped:76 overruns:0 frame:0
          TX packets:4660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6719190 (6.4 MiB)  TX bytes:493277 (481.7 KiB)
          Interrupt:169 Base address:0x2000 Memory:d6000000-d6000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.2.1  Bcast:172.16.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.118.1  Bcast:192.168.118.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
----------------------
INTERFACES:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

