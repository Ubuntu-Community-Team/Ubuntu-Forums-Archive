---
title: "Unable to connect to LAN"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by remoir on 2008-02-06
hi , 

i recently installed Gutsy in my laptop, but i am having problems in connecting to the LAN (wired network- eth0), even though the wireless(eth1) works fine. Tested LAN in windows , it worked perfectly.

Tried using the Network GUI to disable and enable eth0, but it doesn't work.

and I tried the following commands 

[COLOR="Blue"]sudo ifdown eth1
sudo ifdown eth0
sudo ifup eth0[/COLOR]

but this doesn't work. I got the following results from the terminal.

[COLOR="Red"]There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:08:0d:33:57:51
Sending on   LPF/eth0/00:08:0d:33:57:51
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/COLOR]

i run this command "ifconfig -a" and got the following.

[COLOR="YellowGreen"]eth0      Link encap:Ethernet  HWaddr 00:08:0D:33:57:51  
          inet6 addr: fe80::208:dff:fe33:5751/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3668 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62146 (60.6 KB)  TX bytes:512618 (500.6 KB)

eth1      Link encap:Ethernet  HWaddr 00:04:23:5C:05:40  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3435906 (3.2 MB)  TX bytes:71249 (69.5 KB)
          Interrupt:11 Memory:fcefe000-fcefefff 
[COLOR="Red"]
eth0:avah Link encap:Ethernet  HWaddr 00:08:0D:33:57:51  
          inet addr:169.254.3.173  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/COLOR]

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1834 (1.7 KB)  TX bytes:1834 (1.7 KB)[/COLOR]

I don't why, but there's an additional eth0:avah in this list.( see the RED part )

The below is the results i got from "ifconfig -a" before executing any ifup or ifdown commands.

[COLOR="DarkOrange"]eth0      Link encap:Ethernet  HWaddr 00:08:0D:33:57:51  
          inet addr:192.168.0.131  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:dff:fe33:5751/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61546 (60.1 KB)  TX bytes:503554 (491.7 KB)

eth1      Link encap:Ethernet  HWaddr 00:04:23:5C:05:40  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe5c:540/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3435720 (3.2 MB)  TX bytes:71209 (69.5 KB)
          Interrupt:11 Memory:fcefe000-fcefefff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1076 (1.0 KB)  TX bytes:1076 (1.0 KB)[/COLOR]

Need some advice on how can i troubleshoot this issue. :(

---

### Post by aseemparanjape on 2008-02-08
Hello,
I have recently had a similar problem with the auto DHCP configuration setting... I get "No DHCP offers..." like remoir above. 
I've been using the wired network on my Lenovo Y500 laptop with ubuntu 7.10 for a couple of months now, with network settings set to Automatic DHCP configuration, and it has worked without any trouble.

Here are the specs of my ethernet interface eth0

[I] *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:ec:67:6a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=158.144.52.51 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
[/I]

I've noticed several other threads with similar issues, but I haven' found a consistent fix.
It's only in the last week or so that this problem has shown up. I've been consistently installing all released software updates, using the Update Manager. This is the only thing that has changed on my computer itself. (There may be problems with the DHCP server which I don't know about.) 
It'll be nice if someone can help.
Thanks,
Aseem
P.S. - I'm currently using a static ip address, and the network is functioning perfectly.

---

