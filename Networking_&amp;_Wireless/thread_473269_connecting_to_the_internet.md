---
title: "connecting to the internet"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by Wally Paulnuts on 2007-06-13
In response to the advice:
<<<<<<<<<<Please tell me what happens when you complete these commands in order:
<<<<<<<<<<Code:

<<<<<<<<<<sudo ifdown eth0
<<<<<<<<<<sudo /etc/init.d/avahi-daemon stop
<<<<<<<<<<sudo ifup eth0


this is the data that was produced when i input the commands:

anthony@anthony-desktop:~$ sudo ifdown eth0
Password:
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5633
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:a5:1e:cc:95
Sending on LPF/eth0/00:02:a5:1e:cc:95
Sending on Socket/fallback
anthony@anthony-desktop:~$ sudo /etc/init.d/avahi-daemon stop
* Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon [ OK ]
anthony@anthony-desktop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:a5:1e:cc:95
Sending on LPF/eth0/00:02:a5:1e:cc:95
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

