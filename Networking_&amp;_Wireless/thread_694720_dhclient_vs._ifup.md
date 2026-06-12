---
title: "dhclient vs. ifup"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by jurino on 2008-02-12
Hi

I have dual boot Windows and Ubuntu Gutsy and network configured by DHCP. The problem is that normally the IP address leased in WinXP is different as the one leased in Linux. So I have added "send dhcp-client-identifier 1:0:0f:fe:47:45:9a;" in my dhclient.conf to solve this.

The problem is that after boot I will obtain that Ubuntu address, not that Windows one. However, when I run "dhclient", it gets the Windows one. It looks like ifup script does not use dhclient.conf at all. Is it normal? Does someone know how can I change this behaviour?

Thanks

```

# dhclient
There is already a pid file /var/run/dhclient.pid with pid 7815
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0f:fe:47:45:9a
Sending on   LPF/eth0/00:0f:fe:47:45:9a
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.202.2
 * Reloading /etc/samba/smb.conf...
   ...done.
bound to 192.168.202.117 -- renewal in 3425 seconds.


# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 7710
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0f:fe:47:45:9a
Sending on   LPF/eth0/00:0f:fe:47:45:9a
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.202.2 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0f:fe:47:45:9a
Sending on   LPF/eth0/00:0f:fe:47:45:9a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.202.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.202.2
bound to 192.168.202.109 -- renewal in 3315 seconds.
```

---

