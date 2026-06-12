---
title: "borked my network"
date: 2017-04-29
forum: Networking &amp; Wireless
---

### Post by ubuntubrian on 2017-04-29
Hello all and thanks in advance!

I'll try to be brief but concise.
I had some intermittent issues with wireless on 16.04 (my system). I upgraded Thunderbird to 52.0 and wonder if that added some pckgs or confs that made messed up things but I have no idea. I uninstalled t-bird but no diff.

Here's the issue. I can see the networks available but cannot connect. My home network is psswd protected and I can't get past a continual request for authentication. Using my phone as a hotspot shows up but will not connect-just spins then quits. I figured my network config was borked so I have googled and reconfigured until I give up!
Here's what I have so far, in some sort of order:

```
~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 20:6a:8a:7f:1d:4f  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226a:8aff:fe7f:1d4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4349290 (4.3 MB)  TX bytes:4371878 (4.3 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:17969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17969 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:2189220 (2.1 MB)  TX bytes:2189220 (2.1 MB)

wlan1     Link encap:Ethernet  HWaddr c0:18:85:6f:b5:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3966 errors:0 dropped:0 overruns:0 frame:99861
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:531186 (531.1 KB)  TX bytes:30602 (30.6 KB)
          Interrupt:18 

```

Seems OK?

So:
```
~$ sudo ifup eth1
ifup: interface eth1 already configured

```
looks good
Then:
```
~$ sudo ifdown eth1
Killed old client process
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/20:6a:8a:7f:1d:4f
Sending on   LPF/eth1/20:6a:8a:7f:1d:4f
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67 (xid=0x60942b5f)

```

Is this OK?

Then:
```
~$ sudo ifdown --exclude=lo -a && sudo ifup --exclude=lo -aInternet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/20:6a:8a:7f:1d:4f
Sending on   LPF/eth1/20:6a:8a:7f:1d:4f
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0x618b1e73)
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5 (xid=0x618b1e73)
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7 (xid=0x618b1e73)
DHCPREQUEST of 192.168.1.10 on eth1 to 255.255.255.255 port 67 (xid=0x731e8b61)
DHCPOFFER of 192.168.1.10 from 192.168.1.1
DHCPACK of 192.168.1.10 from 192.168.1.1
RTNETLINK answers: File exists
bound to 192.168.1.10 -- renewal in 35743 seconds.

```

Here's my /etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback
#The primary network interface
auto eth1
iface eth1 inet dhcp
#auto tap0
#iface tap0 inet manual
 #  up ifconfig $IFACE 172.16.1.1 netmask 255.255.255.0 up
  # down ifconfig $IFACE down
  # tunctl_user brianokeefe

```

this allows an ethernet connection but commenting out "auto eth1" kills that so I have no connection. uncommenting it restores ethernet connection.

So I have an "eth1" that looks functional but isn't. Any help??

Many, many thanks



If I comment out

---

### Post by papibe on 2017-04-29
Hi ubuntubrian.

If this is a Desktop edition, by default the network is manage by NetworkManager (unless you disabled it).

Restore /etc/network/interfaces as its default:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```
and use this to restart your network:
```
sudo systemctl start NetworkManager.service
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by ubuntubrian on 2017-04-30
Perfect!

thanks

---

