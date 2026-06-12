---
title: "Edgy Wireless not coming up automatically"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by ottothecow on 2007-03-06
I updated from dapper to edgy and I have everything working as it did before the update except for my wireless.

When I first boot my laptop (Thinkpad T23), I have no connection until I:
sudo ifdown eth1
sudo ifup eth1

doing this will make the wireless work for certainly as long as the computer is in a powered on state.  When I suspend the system and wake it back up after some time, sometimes the wireless will work but sometimes it wont.  repeating the ifdown ifup steps from before does not fix the issue (it hangs on the dhcp discover).

Any ideas?

---

### Post by ottothecow on 2007-03-11
bump?

---

### Post by trash on 2007-03-11
on a mac here but I have a strange issue that if i login too quickly my wireless will not connect but if i wait 20-30 seconds it connects everytime.

---

### Post by ottothecow on 2007-03-15
that doesnt seem to be the issue, I have given it time after startup to log in and the problem still requires an ifup / ifdown to fix (on the initial bootup...if the computer sleeps and wakes up, an ifdown / ifup wont fix the problem and I have to reboot which makes it see like an initialization issue that wasnt present in dapper)

---

### Post by ottothecow on 2007-03-15
My ifdowns and ifups look like this:

otto@littleblue:~$ sudo ifdown eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:02:2d:b5:b5:12
Sending on   LPF/eth1/00:02:2d:b5:b5:12
Sending on   Socket/fallback
suDHCPRELEASE on eth1 to 128.135.199.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.


otto@littleblue:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:02:2d:b5:b5:12
Sending on   LPF/eth1/00:02:2d:b5:b5:12
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7

this just repeats going to higher and higher intervals until I break it.

---

