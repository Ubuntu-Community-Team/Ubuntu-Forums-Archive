---
title: "cant get intenet connection to work"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by thebrandon on 2007-10-09
I have been trying to get my internet connection to work for several days now to no avail!

I am running Ubuntu 7.04 and neither my onboard lan port (Marvell 88E8001 on an Asus A8V Deluxe motherboard) or my network card (Realtek RTL-8139/8139c/8139c+) will allow me to connect to the internet.  

I have tried to update drivers but havent had any luck.

Any help would be greatly appreciated

---

### Post by jonobr on 2007-10-09
Could you provide more information on your network setup,
are you using a static IP address setup or DHCP?

Are you receiving your IP address from your provideretc?
More info would be great

Thanks

---

### Post by thebrandon on 2007-10-10
I am using DHCP and i do receive my ip from my provider but I am not getting enough of a connection to ever get assigned one.  The Led's light up when I plug the ethernet cable in so I really dont think that it is bad.  As of yesterday I tried updating the bios (I read where someone with a similar problem did that and it magically worked) but it didnt fix it and I also tried installing OpenSuse instead to see if I could get it to work there but I got the same results.

---

### Post by kevdog on 2007-10-10
Can you post lshw -C network

Thanks

---

### Post by thebrandon on 2007-10-10
lshw -C network :

  *-network:0             
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@00:0a.0
       logical name: eth0
       version: 13
       serial: 00:11:2f:de:4a:98
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.9 duplex=full firmware=N/A latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:fab00000-fab03fff ioport:a800-a8ff irq:17
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth1
       version: 10
       serial: 00:00:c5:c1:e9:62
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:b000-b0ff iomemory:fac00000-fac000ff irq:18

---

### Post by kevdog on 2007-10-10
Ok you have drivers assigned to both, thats good.  Now are you trying to use eth1 or eth0??

Plug in the cable to either of the cards (doesnt matter), and then post
ifconfig
route -n
cat /etc/resolv.conf

---

### Post by thebrandon on 2007-10-10
I want to use eth0 but I had the pci one in as well in hopes that I could maybe double my chances of success.

**ifconfig :**

eth0      Link encap:Ethernet  HWaddr 00:11:2F:DE:4A:98  
          inet6 addr: fe80::211:2fff:fede:4a98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:561628 (548.4 KiB)  TX bytes:12642 (12.3 KiB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:00:C5:C1:E9:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:11:2F:DE:4A:98  
          inet addr:169.254.7.42  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

eth1:avah Link encap:Ethernet  HWaddr 00:00:C5:C1:E9:62  
          inet addr:169.254.9.92  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68508 (66.9 KiB)  TX bytes:68508 (66.9 KiB)

**route -n**

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth1


**cat /etc/resolv.conf**

cat: /etc/resolv.conf: No such file or directory

---

### Post by kevdog on 2007-10-10
Ok - you want to use eth0.

First bring down the eth1 interface

sudo ifdown eth1

Then for eth0 try the following:
sudo ifdown eth0
sudo dhclient -r eth0
sudo ifup eth0
sudo dhclient eth0

Then post ifconfig
route -n

---

### Post by thebrandon on 2007-10-10
brandon@brandon-desktop:~$ sudo ifdown eth1
Password:
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 5585
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:00:c5:c1:e9:62
Sending on   LPF/eth1/00:00:c5:c1:e9:62
Sending on   Socket/fallback

brandon@brandon-desktop:~$ sudo ifdown eth1
ifdown: interface eth1 not configured

brandon@brandon-desktop:~$ sudo ifdown eth0
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 11959
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:de:4a:98
Sending on   LPF/eth0/00:11:2f:de:4a:98
Sending on   Socket/fallback
brandon@brandon-desktop:~$ sudo dhclient -r eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:de:4a:98
Sending on   LPF/eth0/00:11:2f:de:4a:98
Sending on   Socket/fallback
brandon@brandon-desktop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:de:4a:98
Sending on   LPF/eth0/00:11:2f:de:4a:98
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

brandon@brandon-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2F:DE:4A:98  
          inet6 addr: fe80::211:2fff:fede:4a98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86253 (84.2 KiB)  TX bytes:6428 (6.2 KiB)
          Interrupt:17 

eth0:avah Link encap:Ethernet  HWaddr 00:11:2F:DE:4A:98  
          inet addr:169.254.7.42  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76780 (74.9 KiB)  TX bytes:76780 (74.9 KiB)

brandon@brandon-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

---

### Post by kevdog on 2007-10-10
Can you post output of:
ethtool eth0
ethtool eth1

Try the above again, this time with the wire plugged into eth1 and attempted to use eth1 interface.  What are these cards plugged into -- a router or modem??

---

### Post by thebrandon on 2007-10-10
I have them plugged into a modem.

Sorry if this next bit is something of a mess, hopefully I did this in the right order

brandon@brandon-desktop:~$ ethtool eth0
Settings for eth0:
Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
        Current message level: 0x00000037 (55)

Cannot get link status: Operation not permitted
brandon@brandon-desktop:~$ ethtool eth1
Settings for eth1:
Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
        Current message level: 0x00000007 (7)
Cannot get link status: Operation not permitted

brandon@brandon-desktop:~$ sudo dhclient -r eth0
Password:
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:de:4a:98
Sending on   LPF/eth0/00:11:2f:de:4a:98
Sending on   Socket/fallback


brandon@brandon-desktop:~$ sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:00:c5:c1:e9:62
Sending on   LPF/eth1/00:00:c5:c1:e9:62
Sending on   Socket/fallback


brandon@brandon-desktop:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:00:c5:c1:e9:62
Sending on   LPF/eth1/00:00:c5:c1:e9:62
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


brandon@brandon-desktop:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 12297
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:de:4a:98
Sending on   LPF/eth0/00:11:2f:de:4a:98
Sending on   Socket/fallback


brandon@brandon-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:00:C5:C1:E9:62  
          inet6 addr: fe80::200:c5ff:fec1:e962/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:191386 (186.9 KiB)  TX bytes:6312 (6.1 KiB)
          Interrupt:18 Base address:0x6000 

eth1:avah Link encap:Ethernet  HWaddr 00:00:C5:C1:E9:62  
          inet addr:169.254.9.92  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88068 (86.0 KiB)  TX bytes:88068 (86.0 KiB)


brandon@brandon-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth1


brandon@brandon-desktop:~$ ethtool eth1
Settings for eth1:
Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
        Current message level: 0x00000007 (7)
Cannot get link status: Operation not permitted


brandon@brandon-desktop:~$ ethtool eth0
Settings for eth0:
Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
        Current message level: 0x00000037 (55)
Cannot get link status: Operation not permitted


brandon@brandon-desktop:~$ sudo ethtool eth1
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes


brandon@brandon-desktop:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x00000037 (55)
        Link detected: no
brandon@brandon-desktop:~$

---

### Post by thebrandon on 2007-10-11
I still have had no luck but I did try this earlier and I think I might have identified a problem but I am not sure, here is what I did :

brandon@brandon-desktop:~$ sudo /etc/init.d/networking stop
Password:
 * Deconfiguring network interfaces...                                      RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 14631
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:de:4a:98
Sending on   LPF/eth0/00:11:2f:de:4a:98
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 11221
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:00:c5:c1:e9:62
Sending on   LPF/eth1/00:00:c5:c1:e9:62
Sending on   Socket/fallback
                                                                     [ OK ]
brandon@brandon-desktop:~$ sudo modprobe -r skge
brandon@brandon-desktop:~$ sudo modprobe skge debug=16
brandon@brandon-desktop:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                        There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:00:c5:c1:e9:62
Sending on   LPF/eth1/00:00:c5:c1:e9:62
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                     [ OK ]



Now my question is that when the network comes back up its doing  DHCPDISCOVER on eth1 when I am trying to use eth0 which is the device that the skge driver is assigned to.

I did the same thing with my other one and found that it was doing DHCPDISCOVER on eth0, is it possible that these are switched or messed up somehow?

---

### Post by thebrandon on 2007-10-12
I started a new thread with a bit more info, but I still cant get it to work......

The new thread is here :

[http://ubuntuforums.org/showthread.php?p=3520221#post3520221](http://ubuntuforums.org/showthread.php?p=3520221#post3520221)

---

