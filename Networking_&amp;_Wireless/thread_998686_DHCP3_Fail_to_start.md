---
title: "DHCP3 Fail to start"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by 1binary0 on 2008-12-01
Hello all :)

I'm currently trying to configure a DHCP using Ubuntu Server for school work. I've configured the /etc/dhcp3/dhcpd.conf file and the /etc/defaults/dhcp3-server with help from the example file and the official support page.

However when i try to start the server - the start process fails.

/etc/dhcp3/dhcpd.conf (I've excluded all # lines)
```


ddns-update-style none;

option domain-name "gotham.net";
option domain-name-servers 10.14.12.91, 10.0.0.104;

default-lease-time 600;
max-lease-time 7200;

log-facility local7;

subnet 192.168.200.0 netmask 255.255.255.0 {
range 192.168.200.100 192.168.200.150;
option routers 10.14.12.91, 10.0.0.104;
}

```

/etc/defaults/dhcp3-server
```

INTERFACES="eth1"

```

Any ideas as to where I'm going wrong?

---

### Post by Iowan on 2008-12-01
I'm not using the log-facility option - so dunno if that can cause problems...
I wonder if the routers and domain-name-servers will work (being in a different subnet).You could try "commenting" them out.

---

