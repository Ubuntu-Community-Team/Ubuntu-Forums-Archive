---
title: "DHCP + Alternative Static Gateway"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by aussieklutz on 2008-07-31
I am in the situation where the default gateway provided by my accommodation is incorrect and I need to set my own gateway. 

My /etc/network/interfaces looks like this:
```
auto eth0
iface eth0 inet dhcp
gateway 10.216.144.2
```

This is doing nothing. I am currently running the following script manually each startup.

```
#!/bin/bash
route del default
route add -host 10.216.144.2 dev eth0
route add default gw 10.216.144.2
```

Is there anyway to make the script automatic at boottime without a cron job or to get my interface config working properly?

---

### Post by Iowan on 2008-08-01
I'll check my Ubuntu box when I get home.  Until then, check options in **/etc/dhcp3/dhclient.conf**.

---

