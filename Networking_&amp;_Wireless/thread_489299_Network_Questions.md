---
title: "Network Questions"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by digicrime on 2007-07-01
So I decided to install ubuntu to my laptop (thinkpad R50) so far so good but couple things. I can see my network on my other desktops which are windows XP but i cant play music or view the video across the network, I have to copy it to the laptop then I can view it, Particular reason why?

Also my network strength on my wireless says its 69% Router is like right next to me. I havent moved the laptop away yet to see how bad it gets but with being only a few inches away that cant be good?

Remote Desktop on ubuntu.. I use the IP 192.168.1.x like I did on windows
to connect to my desktop but the connect button is shadowed out doesnt let me connect?

---

### Post by digicrime on 2007-07-01
Oh something else ive noticed is when I close the lid it shuts down the computer rather then put it in sleep mode, itll restart back up where I left off though kinda weird but my network isnt coming back u punless i restart it manually from shell is this normal or something else. After restarting wireless works fine just wondering if thsi is something i have to do everytime

```

root@laptop:/etc/init.d# ./networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 14272
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:0d:60:b0:f9:ff
Sending on   LPF/eth0/00:0d:60:b0:f9:ff
Sending on   Socket/fallback
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.ath0.pid with pid 14323
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:05:4e:46:21:cc
Sending on   LPF/ath0/00:05:4e:46:21:cc
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:05:4e:46:21:cc
Sending on   LPF/ath0/00:05:4e:46:21:cc
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPOFFER from 192.168.1.254
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.65 -- renewal in 42503 seconds.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:0d:60:b0:f9:ff
Sending on   LPF/eth0/00:0d:60:b0:f9:ff
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

```

---

### Post by digicrime on 2007-07-02
To bump my own thread coming out of sleep mode network seems to be restarting up now but my other issues im still concerned about, remote desktop I got fixed but not being able to play a video/music file acrossed my local network is a concern

---

