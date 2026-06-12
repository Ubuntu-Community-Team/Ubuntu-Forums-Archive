---
title: "Internet Doesn't Work. (I can't seem to get an IP-address?)"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by pir on 2008-02-24
Hi!

This morning, while I was browsing, I had to remove my internetcable. When I plugged it back in, my internet didn't work anymore.
I tried solving it, but I have had no success yet.
The problem is that I dont't get an IP-address from the router (I think)

IFCONFIG:
> **karlo@karlo-desktop:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1A:4D:5C:97:62
          inet6 addr: fe80::21a:4dff:fe5c:9762/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:42982 (41.9 KB)
          Interrupt:16 Base address:0x4000

eth0:avah Link encap:Ethernet  HWaddr 00:1A:4D:5C:97:62
          inet addr:169.254.6.15  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:16170 (15.7 KB)  TX bytes:16170 (15.7 KB)



Screenshot of connection info: (It is in Dutch, but I think that shouldn't be aa problem):
[IMG]http://www.imgdumper.nl/uploads/47c186c52fefa/Schermafdruk-Verbindingsinformatie.png[/IMG]


Finally the results of sudo /etc/init.d/networking restart:

> karlo@karlo-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 7242
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:4d:5c:97:62
Sending on   LPF/eth0/00:1a:4d:5c:97:62
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:4d:5c:97:62
Sending on   LPF/eth0/00:1a:4d:5c:97:62
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persisten

I hope you can halp me, I don't know what to do anymore...

---

### Post by Iowan on 2008-02-24
Check System>Administration>Network>Wired connection>Properties to see if it slipped into "Local Zeroconf network" mode.
```
eth0:avah Link encap:Ethernet HWaddr 00:1A:4D:5C:97:62
inet addr:169.254.6.15 Bcast:169.254.255.255 Mask:255.255.0.0
```This section seems to come from the Zeroconf mode - and may be responsible for this line:```
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
```

---

### Post by pir on 2008-02-24
> **Iowan said:**
> Check System>Administration>Network>Wired connection>Properties to see if it slipped into "Local Zeroconf network" mode.
```
eth0:avah Link encap:Ethernet HWaddr 00:1A:4D:5C:97:62
inet addr:169.254.6.15 Bcast:169.254.255.255 Mask:255.255.0.0
```This section seems to come from the Zeroconf mode - and may be responsible for this line:```
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
```

Thanks Iowan. For some reason it worked after i closed "properties". I didn't change anything there :???:
What files should I backup to be shure I can directly make it works after it fails again?

(result of restart now: )
> 
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
There is already a pid file /var/run/dhclient.eth0.pid with pid 6147
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:4d:5c:97:62
Sending on   LPF/eth0/00:1a:4d:5c:97:62
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:4d:5c:97:62
Sending on   LPF/eth0/00:1a:4d:5c:97:62
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPOFFER from 192.168.1.254
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.35 -- renewal in 14294 seconds.
                                                                         [ OK ]


---

