---
title: "DHCP not working on gutsy"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by JulesBl on 2007-11-15
Hi

Having a problem with my ethernet connection, it looks like the DHCP setup is partially working, its gets the DNS server(s), but not a working address so I have no network.

The ethernet card is the internal one on a GeForce6100SM-M

The network system is properly configured for DHCP (had a look at the /etc/network/interfaces and that is fine)

Here is what I get from  grep dhclient /var/log/daemon*

julianb@julianb-desktop-main:~$ grep dhclient /var/log/daemon*
/var/log/daemon.log:Nov 15 13:43:41 julianb-desktop-main dhclient: DHCPOFFER from 192.168.1.1
/var/log/daemon.log:Nov 15 13:43:41 julianb-desktop-main dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
/var/log/daemon.log:Nov 15 13:43:42 julianb-desktop-main dhclient: DHCPACK from 192.168.1.1
/var/log/daemon.log:Nov 15 13:43:42 julianb-desktop-main dhclient: bound to 192.168.1.2 -- renewal in 33864 seconds.
/var/log/daemon.log:Nov 15 13:52:22 julianb-desktop-main dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 4155
/var/log/daemon.log:Nov 15 13:52:22 julianb-desktop-main dhclient: killed old client process, removed PID file
/var/log/daemon.log:Nov 15 13:52:22 julianb-desktop-main dhclient: Internet Systems Consortium DHCP Client V3.0.5
/var/log/daemon.log:Nov 15 13:52:22 julianb-desktop-main dhclient: Copyright 2004-2006 Internet Systems Consortium.
/var/log/daemon.log:Nov 15 13:52:22 julianb-desktop-main dhclient: All rights reserved.
/var/log/daemon.log:Nov 15 13:52:22 julianb-desktop-main dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
/var/log/daemon.log:Nov 15 13:52:22 julianb-desktop-main dhclient: 
/var/log/daemon.log:Nov 15 13:52:22 julianb-desktop-main dhclient: Listening on LPF/eth0/00:1b:b9:be:33:89
/var/log/daemon.log:Nov 15 13:52:22 julianb-desktop-main dhclient: Sending on   LPF/eth0/00:1b:b9:be:33:89
/var/log/daemon.log:Nov 15 13:52:22 julianb-desktop-main dhclient: Sending on   Socket/fallback
/var/log/daemon.log:Nov 15 13:52:22 julianb-desktop-main dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
/var/log/daemon.log:Nov 15 13:52:38 julianb-desktop-main dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
/var/log/daemon.log:Nov 15 13:52:38 julianb-desktop-main dhclient: Internet Systems Consortium DHCP Client V3.0.5
/var/log/daemon.log:Nov 15 13:52:38 julianb-desktop-main dhclient: Copyright 2004-2006 Internet Systems Consortium.
/var/log/daemon.log:Nov 15 13:52:38 julianb-desktop-main dhclient: All rights reserved.
/var/log/daemon.log:Nov 15 13:52:38 julianb-desktop-main dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
/var/log/daemon.log:Nov 15 13:52:38 julianb-desktop-main dhclient: 
/var/log/daemon.log:Nov 15 13:52:39 julianb-desktop-main dhclient: Listening on LPF/eth0/00:1b:b9:be:33:89
/var/log/daemon.log:Nov 15 13:52:39 julianb-desktop-main dhclient: Sending on   LPF/eth0/00:1b:b9:be:33:89
/var/log/daemon.log:Nov 15 13:52:39 julianb-desktop-main dhclient: Sending on   Socket/fallback
/var/log/daemon.log:Nov 15 13:52:42 julianb-desktop-main dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
/var/log/daemon.log:Nov 15 13:52:42 julianb-desktop-main dhclient: DHCPOFFER from 192.168.1.1
/var/log/daemon.log:Nov 15 13:52:42 julianb-desktop-main dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
/var/log/daemon.log:Nov 15 13:52:42 julianb-desktop-main dhclient: DHCPACK from 192.168.1.1
/var/log/daemon.log:Nov 15 13:52:42 julianb-desktop-main dhclient: bound to 192.168.1.2 -- renewal in 37848 seconds.
/var/log/daemon.log.0:Nov 15 13:20:49 julianb-desktop-main dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
/var/log/daemon.log.0:Nov 15 13:20:49 julianb-desktop-main dhclient: DHCPOFFER from 192.168.200.1
/var/log/daemon.log.0:Nov 15 13:20:49 julianb-desktop-main dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
/var/log/daemon.log.0:Nov 15 13:20:49 julianb-desktop-main dhclient: DHCPACK from 192.168.200.1
/var/log/daemon.log.0:Nov 15 13:20:50 julianb-desktop-main dhclient: bound to 192.168.200.109 -- renewal in 269662 seconds.
/var/log/daemon.log.0:Nov 15 13:22:09 julianb-desktop-main dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5241
/var/log/daemon.log.0:Nov 15 13:22:09 julianb-desktop-main dhclient: killed old client process, removed PID file
/var/log/daemon.log.0:Nov 15 13:22:09 julianb-desktop-main dhclient: DHCPRELEASE on eth0 to 192.168.200.1 port 67

Looks like the daemon is just exiting.

Anybody got any ideas?

Jules

---

### Post by R00t3rMan on 2007-11-15
I don't have any ideas, but if you need something to do a stare and compare with, here's what (I think) you should see when it's working:

Nov 11 18:20:29 glenkinchie dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 11 18:20:29 glenkinchie dhclient: DHCPOFFER from 10.0.0.1
Nov 11 18:20:29 glenkinchie dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 11 18:20:29 glenkinchie dhclient: DHCPACK from 10.0.0.1
Nov 11 18:20:29 glenkinchie dhclient: bound to 10.0.0.4 -- renewal in 487 seconds.
[COLOR="Red"]Nov 11 18:20:39 glenkinchie dhclient: isc-dhclient-V3.0.5[/COLOR]
Nov 11 18:28:36 glenkinchie dhclient: DHCPREQUEST on eth0 to 10.0.0.1 port 67
Nov 11 18:28:36 glenkinchie dhclient: DHCPACK from 10.0.0.1
Nov 11 18:28:36 glenkinchie dhclient: bound to 10.0.0.4 -- renewal in 409 seconds.
Nov 11 18:35:25 glenkinchie dhclient: DHCPREQUEST on eth0 to 10.0.0.1 port 67
Nov 11 18:35:25 glenkinchie dhclient: DHCPACK from 10.0.0.1
Nov 11 18:35:25 glenkinchie dhclient: bound to 10.0.0.4 -- renewal in 415 seconds.
Nov 11 18:42:20 glenkinchie dhclient: DHCPREQUEST on eth0 to 10.0.0.1 port 67
Nov 11 18:42:20 glenkinchie dhclient: DHCPACK from 10.0.0.1
Nov 11 18:42:20 glenkinchie dhclient: bound to 10.0.0.4 -- renewal in 411 seconds.
Nov 11 18:49:11 glenkinchie dhclient: DHCPREQUEST on eth0 to 10.0.0.1 port 67
Nov 11 18:49:11 glenkinchie dhclient: DHCPACK from 10.0.0.1
Nov 11 18:49:11 glenkinchie dhclient: bound to 10.0.0.4 -- renewal in 494 seconds.
Nov 11 18:57:25 glenkinchie dhclient: DHCPREQUEST on eth0 to 10.0.0.1 port 67
Nov 11 18:57:25 glenkinchie dhclient: DHCPACK from 10.0.0.1
Nov 11 18:57:25 glenkinchie dhclient: bound to 10.0.0.4 -- renewal in 449 seconds.
[COLOR="Red"]Nov 12 06:50:08 glenkinchie dhclient: isc-dhclient-V3.0.5[/COLOR]


I'm not sure why it's doing this, but you obvoiusly have the same version of dhcp client that I do.  There must be some mechanism in there somewhere that isn't being triggered so the daemon thinks it needs an IP address.  I'm gonna dig around a little more.

---

### Post by JulesBl on 2007-11-16
Hi

Been googling around about this and a suggestion that has come up a couple of times is to comment out the ethernet definition in 

/etc/network/interfaces

I changed

iface eth0 inet dhcp

to

#iface eth0 inet dhcp

rebooted the system and it worked!!! :)

Jules

---

### Post by JulesBl on 2007-11-16
Had a bit more of a look at how the system is now behaving

The configuration thinks it is roving mode and effectively not connected, though it does show the connection information, guess I will just have to leave it alone and hope for the best.

Jules

---

