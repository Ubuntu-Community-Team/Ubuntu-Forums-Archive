---
title: "Wireless IPW2100 not detected"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by drfox on 2006-07-27
I decided to try Edgy because of the Evolution enhancement.
On Dapper everything was working fine. Now, everything seems to be working on my Toshiba laptop except for my wireless card (which is ETH1). It doesn't show up in the System>Networking>Connections window at all. In fact, no devices are listed there notwithstanding the fact that my wired ethernet card is working fine.

I know this is not enough information to get an answer, but perhaps you can tell me what commands to run to give you enough information to troubleshoot.

Thanks

Here's a printout of what I get when I restart the network:

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:a0:d1:35:bc:fc
Sending on   LPF/eth0/00:a0:d1:35:bc:fc
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.12.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:13:02:16:18:a1
Sending on   LPF/eth1/00:13:02:16:18:a1
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.15.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:13:02:16:18:a1
Sending on   LPF/eth1/00:13:02:16:18:a1
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:a0:d1:35:bc:fc
Sending on   LPF/eth0/00:a0:d1:35:bc:fc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.12.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.12.1
bound to 192.168.12.13 -- renewal in 128061 seconds.

---

