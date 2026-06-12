---
title: "Need to restart network 2x before I get an IP"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by robucf on 2007-05-16
Upon boot my wireless network will not connect until I restart the network 2x, I cannot figure out why and it so annoying to have to do that every time I boot.  Also, where is wifi0 and eth0 coming from I do not have those references in my interfaces files, posted below.

~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.ath0.pid with pid 5498
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:18:e7:1b:46:5c
Sending on   LPF/ath0/00:18:e7:1b:46:5c
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:18:e7:1b:46:5c
Sending on   LPF/ath0/00:18:e7:1b:46:5c
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                          There is already a pid file /var/run/dhclient.ath0.pid with pid 5917
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:18:e7:1b:46:5c
Sending on   LPF/ath0/00:18:e7:1b:46:5c
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:18:e7:1b:46:5c
Sending on   LPF/ath0/00:18:e7:1b:46:5c
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 18
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.200 -- renewal in 40527 seconds.
                                                                                                                                         [ OK ]

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wpa-driver madwifi
wpa-ssid myssid
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk my key

---

### Post by biTaZ on 2007-05-18
I have the same kind of problem with my usb0 interface in Feisty. It used to work properly,but now, if I plug my usb ethernet device, udev properly assigns the name but it's not brought up automatically...

auto mspot-c
iface mspot-c inet static
        address 10.0.0.3
        netmask 255.255.255.0
        broadcast 10.0.0.255

...

Was working fine on Edgy before the upgrade...

**EDIT: **I found that the problem comes from the fact that the interface is not ifdowned automatically when I unplug the device. Where to look now? hotplug? udev? Any pointers appreciated.
**EDIT: **Ok, I found my problem is actually completely different to yours, It is actually related to udev. I will start a new post.

---

### Post by cgirda on 2007-07-20
Hi robucf,

   Where you able to find a solution for your usb0 to come up automatically without a network restart.

---

