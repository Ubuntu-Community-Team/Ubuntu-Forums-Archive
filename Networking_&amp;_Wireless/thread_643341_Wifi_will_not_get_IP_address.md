---
title: "Wifi will not get IP address"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by shafer_darkstar on 2007-12-17
I have looked at several threads and none have helped solve my problem.  I have an Atheros wireless card on a Toshiba Satellite P25-S507.  I previously had wireless working under a previous version of Ubuntu, but since upgrading to Gutsy I can't get it to work.  Since the restricted drivers didn't work I've tried installing madwifi myself, and that hasn't worked either.  I currently can see routers to connect to, but when my computer attempts to get an ip it never works for the wireless.  The output looks like this.
 sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 11105
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:90:96:59:d9:2a
Sending on   LPF/ath0/00:90:96:59:d9:2a
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any help would be much appreciated.

---

