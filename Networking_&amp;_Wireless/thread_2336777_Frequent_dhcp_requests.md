---
title: "Frequent dhcp requests?"
date: 2016-09-11
forum: Networking &amp; Wireless
---

### Post by eezacque on 2016-09-11
I noticed that my network connection is disrupted every 30 mins or so, and it seems like this event is accompanied by the following log fragment:

Sep 11 14:05:04 behemoth dhclient: DHCPREQUEST of 192.168.178.15 on wlan0 to 192.168.178.1 port 67 (xid=0x114a6d1d)
Sep 11 14:05:05 behemoth dhclient: DHCPACK of 192.168.178.15 from 192.168.178.1
Sep 11 14:05:05 behemoth NetworkManager[983]: <info>    address 192.168.178.15
Sep 11 14:05:05 behemoth NetworkManager[983]: <info>    plen 24 (255.255.255.0)
Sep 11 14:05:05 behemoth NetworkManager[983]: <info>    gateway 192.168.178.1
Sep 11 14:05:05 behemoth NetworkManager[983]: <info>    server identifier 192.168.178.1
Sep 11 14:05:05 behemoth NetworkManager[983]: <info>    lease time 3600
Sep 11 14:05:05 behemoth NetworkManager[983]: <info>    nameserver '89.101.251.228'
Sep 11 14:05:05 behemoth NetworkManager[983]: <info>    nameserver '89.101.251.229'
Sep 11 14:05:05 behemoth NetworkManager[983]: <info>    domain name 'dynamic.ziggo.nl'
Sep 11 14:05:05 behemoth NetworkManager[983]: <info>  (wlan0): DHCPv4 state changed bound -> bound
Sep 11 14:05:05 behemoth dbus[987]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Sep 11 14:05:05 behemoth systemd[1]: Starting Network Manager Script Dispatcher Service...
Sep 11 14:05:05 behemoth dhclient: bound to 192.168.178.15 -- renewal in 1562 seconds.
Sep 11 14:05:05 behemoth dbus[987]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep 11 14:05:05 behemoth systemd[1]: Started Network Manager Script Dispatcher Service.
Sep 11 14:05:05 behemoth nm-dispatcher: Dispatching action 'dhcp4-change' for wlan0

Any clue on what is going on here?

---

### Post by newbie-user on 2016-09-13
All that stuff is your computer getting network information from the DHCP server at 192.168.178.1. It shouldn't be disruptive, though. You could set your DHCP lease time for longer than 30 minutes. That would help.

---

### Post by eezacque on 2016-09-15
What puzzles me is how the Network Manager mentions "NetworkManager[983]: <info>    lease time 3600"  while dhclient logs "dhclient: bound to 192.168.178.15 -- renewal in 1562 seconds" I explicitly set a lease time of 3600 in dhclient.conf. I guess this is the place where the lease time is set?

---

### Post by SeijiSensei on 2016-09-15
No, it can also be set on the DHCP server side.  I use very long lease times, often 30 days or longer.  Unless you have more devices than available IP addresses, there is no reason to have short leases.  Thirty minutes is way too short.

---

### Post by eezacque on 2016-09-15
> **SeijiSensei said:**
> No, it can also be set on the DHCP server side.  I use very long lease times, often 30 days or longer.  Unless you have more devices than available IP addresses, there is no reason to have short leases.  Thirty minutes is way too short.

My server is set to a lease time of 3600s.

---

### Post by SeijiSensei on 2016-09-15
OK, so make it a lot longer like 86400 seconds.  Then the lease will be renewed once a day.

---

### Post by eezacque on 2016-09-15
> **SeijiSensei said:**
> OK, so make it a lot longer like 86400 seconds.  Then the lease will be renewed once a day.

Will do. Anyways, I'm still interested in learning the difference between the two lease times mentioned above. Thanks for your help...

---

### Post by SeijiSensei on 2016-09-15
Which "two lease times?"  The one on the server and the one in dhclient?  I don't see any value in using dhclient for this purpose.  Just set the lease time on the server to whatever you want and let it control everything.

From reading "man dhclient.conf" it looks like you can set a lease time there that overrides the server though probably only if the requested time is shorter than the server default.

---

### Post by eezacque on 2016-09-15
> **SeijiSensei said:**
> Which "two lease times?"  The one on the server and the one in dhclient?

I'd like to understand "dhclient: bound to 192.168.178.15 -- renewal in 1562 seconds", the 1562s doesn't make sense...

---

### Post by Keith_Helms on 2016-09-15
> **eezacque said:**
> I'd like to understand "dhclient: bound to 192.168.178.15 -- renewal in 1562 seconds", the 1562s doesn't make sense...

I also see weird times like that.   When connected to the hotspot on my android tablet they are usually smaller numbers like your 1562.   I'm currently connected to my router and I see "renewal in 33730 seconds" and "renewal in 41393 seconds" in the syslog.   Beats me where those numbers come from.

---

### Post by SeijiSensei on 2016-09-15
Isn't it just the difference between the current time and the time the lease was last renewed?

---

### Post by Keith_Helms on 2016-09-15
> **SeijiSensei said:**
> Isn't it just the difference between the current time and the time the lease was last renewed?

That's probably what it is.  It's just listing the remaining lease time in a group of status messages.

On my hotspot, I also see messages like "state bound->unbound" and such which seem to indicate a new lease is being obtained.  I also have problems with the hotspot where traffic stops and I have to reconnect to it (even though it still shows connected) in order to get traffic going again.  But that's another problem.

---

### Post by eezacque on 2016-09-16
> **Keith_Helms said:**
> That's probably what it is.  It's just listing the remaining lease time in a group of status messages.

This 1562s is logged right after the new lease, so the question remains why the lease wasn't renewed after the configured 3600s...

---

