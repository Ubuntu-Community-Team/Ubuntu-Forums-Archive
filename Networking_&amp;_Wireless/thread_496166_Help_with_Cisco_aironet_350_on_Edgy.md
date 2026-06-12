---
title: "Help with Cisco aironet 350 on Edgy"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by kane314 on 2007-07-08
Hi everyone im kinda new to linux and iv been fighting with this thing for a while now...i had it up and running and even managed to get kismet running which was my current goal, however it stopped working for randomly and the only cause i can think of would be the recent updates...i ran the update manager and then restarted the computer and ever since it hasn't been able to get an ip from dhcp even when i use the dhclient command like i used to do...


heres what i get when i use the dhclient command now

root@Hermes:/home/kane# dhclient
There is already a pid file /var/run/dhclient.pid with pid 5644
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth1/00:0f:f7:78:ec:39
Sending on   LPF/eth1/00:0f:f7:78:ec:39
Listening on LPF/eth0/00:15:b7:81:39:52
Sending on   LPF/eth0/00:15:b7:81:39:52
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 6
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


anyone have any suggestions? thanks!

---

### Post by subulaz on 2007-08-05
Check this thread: [http://ubuntuforums.org/showthread.php?t=488300&highlight=aironet]("http://ubuntuforums.org/showthread.php?t=488300&highlight=aironet")

Looks like you have both eth0 (onboard?) and eth1 (assume that's the 350) both connected and trying to get an IP from your router. As noted in the thread above, NetworkManager expects to set up one configuration, not two, so unplugging eth0 might be the place to start.

FYI - I am having a similar problem with a 350 pulling a DHCP address from a router (WRT54GSv2), even with security disabled. I get the same DHCPDISCOVER messages, all the way down to "sleeping", and I have not even had any luck kicking it manually with dhcpcd eth1.

I'll post anything that works...if I get it to work. It kills me because this was all working great in Edgy.

&laz;

---

