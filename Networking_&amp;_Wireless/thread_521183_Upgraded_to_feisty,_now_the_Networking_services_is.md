---
title: "Upgraded to feisty, now the Networking services is causing my system to hang....."
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by BRAXS69 on 2007-08-09
hay guys, i kind of just ran into a problem i have never had before in previous Ubuntu versions. the “network service”  is making the system unresponsive. I've been using feisty for a while and this problem has came up every time I've done a fresh install (3 times). From what i can tell the running off the live cd it all works fine, but after the install and such, i set my static ip address so i connect to my router and the next reboot all of a sudden the networking services cause the system to hang taking as long a 3 minuets  to get past the login screen. then anything i try to open takes about 30-45 seconds to even to begin to load anything,  i was unsure  if this was a bug or just a miss configuration, I've been searching the past week or so trying to figure out what's going on, help would be much appreciated.

hardware specs of the machine:
Intel(R) Pentium(R) 4  2.00GHz,  512 DDR ram
and just just about everything else inside it is Intel including the network card “Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet”

this is just about the only thing that i could find as a error message
```
braxs69@braxs69-ubuntu-desktop:~$ sudo /etc/init.d/networking stop
Password:
 * Deconfiguring network interfaces...                                   [ OK ] 
braxs69@braxs69-ubuntu-desktop:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                            eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
                                                                         [ OK ]
braxs69@braxs69-ubuntu-desktop:~$ 

```

---

