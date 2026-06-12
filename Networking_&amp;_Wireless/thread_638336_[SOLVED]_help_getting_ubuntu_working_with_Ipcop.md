---
title: "[SOLVED] help getting ubuntu working with Ipcop"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by evil316 on 2007-12-11
My network setup is DSL -> Ipcop PC -> Linksys wireless router/gateway wrt54gs -> wired ubuntu desktop and wireless clients.

I'm trying to get ipcop set up for the first time.  What I've been trying to do is set my linksys up as a WAP (wireless access point).  To do so I change the mode from gateway to router.  I then set up the Local IP address to 192.168.10.2 and subnet mask to 255.255.255.0.  I then disable DHCP on the router.  I cable it up as follows.  DSL -> red NIC on ipcop then I go green NIC on ipcop to LAN port on Linksys router (should now be a WAP).  I'm no longer using the WAN (Internet) port on the Linksys.  I get all this set up and then bring up my Ubuntu box which is connected to a LAN port on the Linksys.  Ubuntu doesn't see anything.  

My ipcop config is as follows.  Green interface is set up with IP of 192.168.10.1 (I believe this is also referred to as the internal firewall).  Red interface is set up as DHCP.  Default gateway is set up as 192.168.10.1.  Primary DNS is set up as 192.168.1.1.  My DHCP range is set to 192.168.10.101 - 150.   

This is what I get when using ifdown eth0 and ifup eth0 on the Ubuntu desktop:
-----------------------------------------------------------------------------------------
darren@ubuntu-desktop:~$ sudo ifdown eth0
[sudo] password for darren:
There is already a pid file /var/run/dhclient.eth0.pid with pid 5852
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:18:f3:6e:46:d1
Sending on   LPF/eth0/00:18:f3:6e:46:d1
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
darren@ubuntu-desktop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:18:f3:6e:46:d1
Sending on   LPF/eth0/00:18:f3:6e:46:d1
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
-----------------------------------------------------------------------------------

Any ideas on what I'm doing wrong?  I've been looking at everything I can online on how to set this up and this is the best I've come up with so far.  Any help would be greatly appreciated.

Thanks!

---

### Post by evil316 on 2007-12-12
I got it working.  I had to tweak a few things but the main problem turned out to be the LAN port on my Linksys wasn't working.  I changed ports and away I went.

---

