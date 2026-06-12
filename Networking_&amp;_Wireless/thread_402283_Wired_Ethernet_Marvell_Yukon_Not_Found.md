---
title: "Wired Ethernet Marvell Yukon Not Found"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by Zerhash on 2007-04-05
Hello,

I am a bit of a newb here but hopefully you can help

I installed ndis-wrapper i believe to get my wireless network working. I had to make changes to my /etc/network/interfaces for this to work. Then i had nm-applet take over.

My wireless works still, however something happend between then and now that caused my wired connection to disappear. I can not connect to a wired connection. The cable isnt detected and in System>Administration>Network it doesnt show up.

Here is my /etc/network/interfaces
> 
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

#iface eth1 inet dhcp

auto eth0

#auto eth1


This is the $  /etc/inet.d/networking restart
> 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 6648
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:e2:89:20
Sending on   LPF/eth1/00:0e:35:e2:89:20
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:e2:89:20
Sending on   LPF/eth1/00:0e:35:e2:89:20
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.115 -- renewal in 36498 seconds.
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
Failed to bring up wlan0.
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
                                                                         [ ok ]


dmesg | grep 'Ethernet' doesnt return anything but i noticed
> 
[17180938.800000] ipw2200: Firmware error detected.  Restarting.
[17181030.544000] ipw2200: Firmware error detected.  Restarting.
[17181499.224000] ipw2200: Firmware error detected.  Restarting.


---

### Post by cookfromfrozen on 2007-04-05
Hi

Firstly, you should check that the module that supports Yukon is loaded.  This command loads the driver:
```
sudo modprobe sk98lin
```
Then, it would be a good idea to check for any messages from the driver:
```
dmesg | grep skge
```
In your /etc/network/interfaces, at the moment there are entries for three wired network cards.  Likely you do not have that many so I would remove the entries for all ethX devices except eth0.  This should get rid of the "SIOCSIFADDR: No such device" messages and help diagnosing the problem a bit easier.

However, once the driver is loaded by modprobe, it *should* appear in the Networking applet.  If not, there will probably be some messages from the driver as to why it cannot start.

---

### Post by Zerhash on 2007-04-05
Hey,
thanks for the post

There werent any error messages from the skg

i changed my /etc/network/interfaces and the restart worked with errors

> 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 5354
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:e2:89:20
Sending on   LPF/eth1/00:0e:35:e2:89:20
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
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

Listening on LPF/eth1/00:0e:35:e2:89:20
Sending on   LPF/eth1/00:0e:35:e2:89:20
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.115 -- renewal in 34204 seconds.
                                                                         [ ok ]


This is what my dmesg says for grep eth
> 
[17179587.104000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179602.296000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179605.600000] device eth1 entered promiscuous mode
[17179605.600000] audit(1175806027.735:2): dev=eth1 prom=256 old_prom=0 auid=4294967295
[17179671.880000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179699.760000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179710.504000] eth1: no IPv6 routers present
[17179734.236000] eth1: no IPv6 routers present


I need to update that ipw2200, but how and with what i dont know...

There is still nothing appearing in the networking program

---

### Post by Zerhash on 2007-04-05
I modified my interfaces to be this
> 
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

#iface eth1 inet dhcp

#auto eth0

#auto eth1


on the network restart it does this.
> 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:e2:89:20
Sending on   LPF/eth1/00:0e:35:e2:89:20
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:35:e2:89:20
Sending on   LPF/eth1/00:0e:35:e2:89:20
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]


still nothing in the network interfaces for wired connections

---

