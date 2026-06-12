---
title: "ask for help on wireless problem"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by peteron on 2008-06-05
mine is thinkpad t61, with integrated intel wireless. Ubuntu Hardy Heron, latest kernel. 

everytime I started the system, I have to restart the network and then it begins to work. Can someone help me out on this problem?


* Reconfiguring network interfaces...          
There is already a pid file /var/run/dhclient.ath0.pid with pid 6042
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:**:**:**:**:**
Sending on   LPF/ath0/00:**:**:**:**:**
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 7.7.7.7 port 67
There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:**:**:**:**:**
Sending on   LPF/ath0/00:**:**:**:**:**
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPOFFER of 128.61.22.242 from 7.7.7.7
DHCPREQUEST of 128.61.22.242 on ath0 to 255.255.255.255 port 67
DHCPACK of 128.61.22.242 from 7.7.7.7
bound to 128.61.22.242 -- renewal in 703 seconds.

---

### Post by Vadi on 2008-06-05
Does Network Manager not automatically connect?

---

### Post by peteron on 2008-06-05
> **Vadi said:**
> Does Network Manager not automatically connect?

yea, i think the network doesnot connect automatically, when the system is started

---

