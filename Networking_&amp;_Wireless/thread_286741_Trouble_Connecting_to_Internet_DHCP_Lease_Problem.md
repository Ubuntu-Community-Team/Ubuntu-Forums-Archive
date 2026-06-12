---
title: "Trouble Connecting to Internet DHCP Lease Problem"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by juan_in_nippon on 2006-10-28
1. Complete newbie and have installed 6.10

2. Installed Wired pci Linksys NC 100 Fast Network Everywhere card (OEM manufactuer Planex)

3. Have verified that Linksys NC 100 Network Everwhere wired card is at eth1 using ifconfig (both activity lights are on (green) but no packets going out or in as would be indictaed by flashing of the bottom LED on the card.

4. Have used gedit /etc/interfaces/network to veify that polling of dhcp is properly configured

4. Have tried to get new dhcp lease by running the following commands in terminal but with no luck. Readout follows and would appreciate any suggestions from those in the know if there something else I can do to get this card working.*

Many thanks in advance!*](*,) 

Note: I am connected to a network router where all other clients (Mac & Windows) are getting a lease via DHCP so network is not a problem.

Note: I have tried to set up a static address as well using the ip on this netwrk and that didn't work either!

Terminal commands issued in order of execution:

* * * * *[COLOR="Red"] ifconfig[/COLOR]

eth1* Link encap:Ethernet* HWaddr 00:4C:69:6E:75:79**
* * * * * UP BROADCAST MULTICAST* MTU:1500* Metric:1
* * * * * RX packets:0 errors:0 dropped:1245165 overruns:0 frame:0
* * * * * TX packets:0 errors:1 dropped:0 overruns:0 carrier:0
* * * * * collisions:0 txqueuelen:1000*
* * * * * RX bytes:0 (0.0 b)* TX bytes:0 (0.0 b)
* * * * * Interrupt:10 Base address:0x1800*

lo* * * * Link encap:Local Loopback**
* * * * * inet addr:127.0.0.1* Mask:255.0.0.0
* * * * * inet6 addr: ::1/128 Scope:Host
* * * * * UP LOOPBACK RUNNING* MTU:16436* Metric:1
* * * * * RX packets:50 errors:0 dropped:0 overruns:0 frame:0
* * * * * TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
* * * * * collisions:0 txqueuelen:0*
* * * * * RX bytes:3652 (3.5 KiB)* TX bytes:3652 (3.5 KiB)





[COLOR="red"]sudo /etc/init.d/networking restart[/COLOR]


** Reconfiguring network interfaces...* * * * * * * * * * * * * * * * * * * * * There is already a pid file /var/run/dhclient.eth1.pid with pid 4206
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:4c:69:6e:75:79
Sending on * LPF/eth1/00:4c:69:6e:75:79
Sending on * Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:4c:69:6e:75:79
Sending on * LPF/eth1/00:4c:69:6e:75:79
Sending on * Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
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
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.*

[COLOR="red"]sudo ifdown eth1 [/COLOR]

There is already a pid file /var/run/dhclient.eth1.pid with pid 4872
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:4c:69:6e:75:79
Sending on * LPF/eth1/00:4c:69:6e:75:79
Sending on * Socket/fallback 

[COLOR="red"]sudo ifup eth1[/COLOR]

There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:4c:69:6e:75:79
Sending on * LPF/eth1/00:4c:69:6e:75:79
Sending on * Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ianshort@ianshort-desktop:~$ **

---

### Post by juan_in_nippon on 2006-10-30
Update: Case Closed: Attached WOL (Wakeup on Lan) cable* to motherboard and problem solved!

Unbuntu rocks!

---

