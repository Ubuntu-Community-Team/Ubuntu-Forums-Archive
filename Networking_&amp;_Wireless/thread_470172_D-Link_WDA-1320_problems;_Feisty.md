---
title: "D-Link WDA-1320 problems; Feisty"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by cspence on 2007-06-10
Hi,

I gave up on a linksys WMP54G v4.1 (I think it was) because I couldn't fix it after buying a new router. Odd, but the advice in other threads didn't help anymore. I'm running Feisty. I bought a D-Link WDA-1320, since many people had said it worked well for them. I got it configured, but: 1) It doesn't successfully start at boot time. 2) Running "/etc/init.d/networking restart" gets it connected, but then it repeatedly disconnects and reconnects, so web surfing is pretty painful. I tried changing the hosts line in /etc/nsswitch.conf to "hosts: files dns" as was suggested elsewhere, but it didn't help.

The output of "/etc/init.d/networking restart" is:

[INDENT]Yam:~> sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.ath0.pid with pid 5595
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:89:67:7e
Sending on   LPF/ath0/00:15:e9:89:67:7e
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:15:e9:89:67:7e
Sending on   LPF/ath0/00:15:e9:89:67:7e
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
ip length 318 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.0.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
ip length 318 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.0.1
bound to 192.168.0.6 -- renewal in 965972292 seconds.
[/INDENT]
The "ip length 318 disagrees with bytes received 534. accepting packet with data after udp payload." messages are odd. Any suggestions?

Clay

---

### Post by cspence on 2007-06-10
Strangely, after rebooting and restarting networking, the "ip length 318 disagrees with bytes received 534. accepting packet with data after udp payload." message was gone. It still disconnects and reconnects frequently, making web surfing very slow.

Clay

---

### Post by cspence on 2007-06-10
My apologies if I wasted anyone's time. The problem was the router, a Netgear WPN824. It seemed to work fine with Windows, but then every now and then there would be problems under Windows too. This evening I tried power-cycling the router and it helped.  Temporarily. We bought this router because the old one, a Netgear FWG114P, seemed to be developing flaky behavior. I put the old one back in and the WDA-1320 card now works great under Ubuntu.  I'll see if the old router develops flaky behavior again. (I wish I knew whether the new router is bad, or I configured it incorrectly. There's not that much to configure.)

Clay

---

### Post by SkyScrap on 2007-06-11
You might try to update the routers firmware also. That helped for me, when I had problems with DHCP under Linux, which worked fine under Windows.

---

### Post by cspence on 2007-06-11
Thanks. However there was no newer firmware for the router, at least according to the upgrade utility built into the router. We took it back. For mysterious reasons, the old router (and an old DSL modem) were failing, and now seem to work fine.

Clay

---

### Post by cspence on 2007-06-13
There's still a problem: I had to set MTU for ath0 to 1492. This fixed browsing problems. The interface does not always come up correctly, however. I am the only user (sigh), so I can run "sudo /etc/init.d/networking restart", and this usually works, but it would be nice if it just came up.

Suggestions are welcome.

Clay

---

