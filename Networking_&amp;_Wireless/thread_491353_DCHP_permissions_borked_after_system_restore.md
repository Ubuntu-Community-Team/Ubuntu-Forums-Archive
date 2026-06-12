---
title: "DCHP permissions borked after system restore"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by hugmenot on 2007-07-03
I had to roll back my system from an earlier backup and some permissions were mangled in the process. For example "/" was set to 700 so only root could execute anything. I fixed that and wrong permissions in other places like /var, /var/lib that prevented my system largely from functioning.

Now one thing remains and I don&#8217;t know which permission it is that is denied. I basically cannot use dhcp anymore:

```
$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Listening on LPF/eth1/00:04:23:8d:54:01
Sending on   LPF/eth1/00:04:23:8d:54:01
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFBRDADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCADDRT: Operation not permitted
<Ctrl-C>
```

---

### Post by BroadArrow on 2007-10-27
I have the same issue after my upgrade to Gutsy got interrupted. Did you find a solution in the end?

---

### Post by hugmenot on 2007-10-27
Good question! I did find a way out after an insane amount of googling, and I&#8217;m sure it was something really not obvious. But I can&#8217;t recall what it was. I&#8217;m really sorry.

---

### Post by hugmenot on 2007-10-27
My hunch is, it was a simple wrongly set file permission.

---

### Post by Evadido on 2007-11-03
Reinstalling packages dhcp3-client and dhcp3-common worked for me :)

---

