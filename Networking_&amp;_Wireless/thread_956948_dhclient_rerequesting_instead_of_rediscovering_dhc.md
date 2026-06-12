---
title: "dhclient rerequesting instead of rediscovering dhcp!"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by Badmaster on 2008-10-23
Oct 24 01:23:01 mahostname dhclient: DHCPREQUEST of <null address> on eth_inet to xx.xx.0.1 port 67
Oct 24 01:23:40 mahostname last message repeated 3 times
Oct 24 01:24:32 mahostname last message repeated 4 times
Oct 24 01:24:50 mahostname dhclient: DHCPREQUEST of <null address> on eth_inet to xx.xx.0.1 port 67

and goes on and on and my inet connection is down for like 2mins or so, unless I do /etc/init.d/networking restart which will release and rediscover the dhcp server

any way to configure the dhclient.conf to make it automatically release the ip and get a new one once the lease runs out instead of dhcprequesting till it times out or something?

thanks in advance.

---

### Post by mlapaglia on 2008-10-23
I haven't messed around with dhclient that much, but doesn't <null device> mean something is wrong with your configuration?

it should be saying "DHCPREQUEST 192.168.1.5 on eth0 tp 255.255.255.0 port 67" or something like that?

---

### Post by Badmaster on 2008-10-24
> **mlapaglia said:**
> I haven't messed around with dhclient that much, but doesn't <null device> mean something is wrong with your configuration?

it should be saying "DHCPREQUEST 192.168.1.5 on eth0 tp 255.255.255.0 port 67" or something like that?

everyone seems to be having this problem with this isp...

I simply need the dhclient to release and discover once this happens asap...

maybe i'll have a look at the source later, unless someone knows a config option for this.

---

