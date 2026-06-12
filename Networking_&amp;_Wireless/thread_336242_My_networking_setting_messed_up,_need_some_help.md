---
title: "My networking setting messed up, need some help"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by recon69 on 2007-01-11
Hi all,

I'll try keep this short, my router's ADSL modem stopped working, the LAN part of the router was working fine but no connection to my adsl. so I setup my speedtouch 330 USB modem to get a internet connection while I went about getting a new router. while i was sorting that out i tried to set up webmin_1.310 to see if i could share my connection though the partly working router, I did not manage to do this. so i removed webmin. 

Now I got a new router and it's working fine but my ether netcard will not get a ip address from it. I think that i may have setup so routes in ipchains or somthing like that that is causing these problems. 

I am hoping for some pointers/links to help guides on what files I need to look at on Ubuntu 6.06 LTS - the Dapper Drake  to try fix this. also what is the command to get all thr networking to restart without rebooting.

I am attaching some info below about my system  in the hope it will help someone help me :)

IFCONFIG 
```

mec@mec-desktop:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:6A:62:35:0B
          inet6 addr: fe80::20b:6aff:fe62:350b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1494 (1.4 KiB)
          Interrupt:193 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:81.179.108.25  P-t-P:62.241.161.241  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2021 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1744899 (1.6 MiB)  TX bytes:326006 (318.3 KiB)

mec@mec-desktop:/$


```

sudo ifup eth0   
eth0 is connected to the router 
```

mec@mec-desktop:/$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0b:6a:62:35:0b
Sending on   LPF/eth0/00:0b:6a:62:35:0b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
Trying recorded lease 192.168.2.3
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.


```

/etc/network/interfaces 
```

auto lo
iface lo inet loopback
iface eth0 inet dhcp
        up ip route add 192.168.2.0/24 dev eth0
iface eth1 inet dhcp
iface eth2 inet dhcp
iface ath0 inet dhcp
iface wlan0 inet dhcp

```

and I am sure there are more but i dont know what file are of interest

thx

---

### Post by recon69 on 2007-01-11
Never mind, I unpluged the adsl line from my speedtouch modem and rebooted and everything seems to be working now. 

ubuntu rocks 

:)

---

