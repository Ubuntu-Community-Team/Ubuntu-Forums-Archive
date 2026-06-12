---
title: "Problems with my internet"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by nawk168 on 2007-02-09
I have Kubuntu 6.06 and I'm having problems with the internet. It would randomly disconnect me while I'm online. Sometimes I am connected for hours and sometimes it disconnects me in a few minutes, especially when I am on DC++.

I have to use the following command to restart it each time:
> sudo /etc/init.d/networking restart
After a few times, that command doesn't even work anymore.

This is the output I get:
>  * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:a0:d1:20:52:9d
Sending on   LPF/eth0/00:a0:d1:20:52:9d
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 169.226.44.141 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:12:f0:71:f0:86
Sending on   LPF/eth1/00:12:f0:71:f0:86
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:a0:d1:20:52:9d
Sending on   LPF/eth0/00:a0:d1:20:52:9d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 169.226.208.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 169.226.208.1
bound to 169.226.212.21 -- renewal in 42700 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:12:f0:71:f0:86
Sending on   LPF/eth1/00:12:f0:71:f0:86
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
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
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]


I searched for this problem and tried configuring my /etc/network/interfaces to make my ip static. That didn't stop the problem.

Here is my /etc/network/interfaces:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


Does anyone have any idea how to fix this problem?

---

### Post by ingo on 2007-02-11
OK, first of all I'd uncomment (precede with #) all those interfaces in /etc/network/interfaces that you do not actually need (5 interfaces?). This will unclutter and speed up both booting and network restart. So next time it happens, open a shell and type
> sudo ifdown name_of_your_interface
sudo dhclient name_of_your_interface
and see whether you get an ip address.

As for your connection (I take it it is wifi), you appear to have a problem with leases. Unfortunately I do not know too much about that, did get rid of a similar problem using knetworkmanager though. If the above therefore does not work, do
> sudo apt-get install knetworkmanager
and now you have a programme that will sort out all your wireless concerns (even handles wpa in your stead) and makes switching networks as easy as it can possibly get.

HTH, if not, come back.

---

