---
title: "Intermittent wireless connection"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by vuroth on 2007-11-24
Dell Inspiron 1720, dual booting Vista and Ubunutu 7.10.  Wireless works no problem in Vista, but generally does not connect.

Having spent most of the day reading and scratching my head, I apologize if I'm asking an overly common question, but I'm really out of frustration.

Here's what things look like when I boot up:

n@laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1d:60:a9:68:0c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:ae:79:b7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s
n@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If I run the manual network setup thingy, and get it to connect to my wireless network (why isn't it doing this automatically?), I get this:

n@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"preparation"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:14:BF:4A:9F:FF   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

n@laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1C:23:AE:79:B7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1D:60:A9:68:0C  
          inet6 addr: fe80::21d:60ff:fea9:680c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:87 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:397 (397.0 b)  TX bytes:11679 (11.4 KB)
          Interrupt:10 Base address:0x8000 

eth1:avah Link encap:Ethernet  HWaddr 00:1D:60:A9:68:0C  
          inet addr:169.254.4.181  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5872 (5.7 KB)  TX bytes:5872 (5.7 KB)


I have no idea what the eth1:avahi is. 

DHCP tells me it can't connect up.


n@laptop:~$ dhclient eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
warren@w-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1d:60:a9:68:0c
Sending on   LPF/eth1/00:1d:60:a9:68:0c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Not a lot of this makes sense to me.  I'm really hoping that someone can spot the key features I should be focusing on.

I've connected to the network once or twice, but I can't stay connected.

There's so much info out there that I'm getting overwhelmed.   Help, please?

V

---

### Post by sjmorris on 2007-11-24
This won't be much help, but I experienced the same thing.  For three days I tried to get past an intermittent connection and finally wound up with no connection at all.  After working most of this afternoon on that second and more frustrating problem, I got to the same outcomes that you did, I gave up and rebooted the machine, expecting to take it up again tomorrow.  

To my surprise, and confusion, the connection suddenly worked.  The frustration, of course, is not knowing why.  I won't post an independent query here, just to avoid more confusion, but will be watching yours closely, in case someone has an answer for both of us.

Good luck.

---

### Post by vuroth on 2007-11-25
Ok, some consistency.

When I power on, I have to click the network icon, do manual connection, and load my saved connection.  I then have to run dhclient eth1 manually.

V

---

