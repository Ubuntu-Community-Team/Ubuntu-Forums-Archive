---
title: "Internet stopped working Ubuntu 12.04.3 LTS"
date: 2013-12-03
forum: Networking &amp; Wireless
---

### Post by trobro on 2013-12-03
[Similar]("http://ubuntuforums.org/showthread.php?t=2191475&p=12865206#post12865206") problem for me. I'm on Ubuntu 12.04.3 LTS, and after the 3.2.0-57 kernel upgrade this morning I could no longer connect to the internet.

The problem seems to be DHCP related. I get an IP address, but no default gateway. If I manually run dhclient, I get the gateway too. I'm not using the network manager, instead an /etc/network/interfaces like this:

```

auto lo
iface lo inet loopback
# The primary network interface
auto eth0
    iface eth0 inet dhcp
    dns-nameservers 8.8.8.8

auto eth1
    iface eth1 inet static
    address 192.168.0.1
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
    gateway 192.168.0.1

```

So for now I guess I'll just run dhclient eth0 at startup.

---

### Post by trobro on 2013-12-03
In order to debug the problem, I ran ```
sudo ifdown eth0
``` and then ```
sudo ifup --verbose eth0
```. It turns out that ifup is calling dhclient like this:

```

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp/dhclient.eth0.leases -1 eth0

```

That doesn't give me a gateway. I tried calling it manually, still didn't get a gateway. But if I remove the first parameter it works:

```

dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp/dhclient.eth0.leases -1 eth0

```

So the problem, at least for me, seems to be that ifup is calling dhclient in the wrong way. I tried calling dhclient at reboot via cron, but then it doesn't give me a gateway. Only works if I call dhclient manually. So for now I'll have to avoid remote reboots...

---

### Post by Iowan on 2013-12-04
Moved to new thread.
Old one here:

[http://ubuntuforums.org/showthread.php?t=2191475&p=12865206#post12865206](http://ubuntuforums.org/showthread.php?t=2191475&p=12865206#post12865206)

---

### Post by trobro on 2013-12-11
Found the real problem now. The gateway I specified for eth1 was blocking the gateway from eth0-dhcp, since they would have the same metric (100). That's why I did get my dhcp-gateway when I called dhclient without specifying any metric.

I've been running Ubuntu 10.04 for years on this server but recently upgraded to 12.04, maybe that's why the problem surfaced. Commenting out the gateway in /etc/network/interfaces was the real solution for my problem, now I can reboot without losing internet.

```

auto eth0
    iface eth0 inet dhcp
    dns-nameservers 8.8.8.8

auto eth1
    iface eth1 inet static
    address 192.168.0.1
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
#    gateway 192.168.0.1 

```

---

