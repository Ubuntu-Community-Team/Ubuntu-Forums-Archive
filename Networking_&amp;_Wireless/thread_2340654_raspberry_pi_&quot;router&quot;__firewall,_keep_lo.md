---
title: "raspberry pi &quot;router&quot; / firewall, keep loosing public connection"
date: 2016-10-20
forum: Networking &amp; Wireless
---

### Post by Drenriza on 2016-10-20
Hi all

I have configured a RaspberryPi V1 to be a super simple "router" and firewall (shorewall) as test.

It all works as expected, execpt that every 10 minutes or so the connectivity from the LAN to the WAN just dies and i need to shutdown the
public interface and restore it
```
ifdown eth0
ifup eth0
```

So far i am tailing /var/log/syslog but havnt seen anything interesting yet, anyone with some advice as to where i should look?

I dont think its because the Raspberry is over worked, since its always responsive for ssh and local pings.
its only the public route that "dies".

EDIT.
Just before the connection died (again) syslog printed
```

Oct 20 20:17:21 firewall01 dhcpcd[760]: eth0: deleting default route via X
Oct 20 20:17:37 firewall01 dhcpcd[760]: eth0: Router Advertisement from X
Oct 20 20:17:37 firewall01 dhcpcd[760]: eth0: adding default route via X

```

Than in my routing table i get placed a link scope address.
```

169.254.0.0/16 dev eth1  proto kernel  scope link  src 169.254.240.49  metric 203

```

As i understand the 169.254.0.0/16 address  appear when the DHCP offer is to slow to get to the client after the DHCP request has been made.
I have tried to get rid of this behavior by changing

from
AVAHI_DAEMON_DETECT_LOCAL=1
to
AVAHI_DAEMON_DETECT_LOCAL=0

apparently didnt help.

Thanks on advance
Kind regards

---

