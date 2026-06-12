---
title: "[SOLVED] Bonding + DHCP"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by Kromey on 2008-07-19
I'm setting up an Ubuntu-based file server, and for high availability I want to bond the two NICs. This is straightforward enough:

/etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc
sbp2
fuse
bonding mode=balance-alb miimon=100
```

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Bonding interface
auto bond0
iface bond0 inet static
address 10.12.0.50
netmask 255.0.0.0
gateway 10.12.0.1
post-up ifenslave bond0 eth0 eth1
pre-down ifenslave -d bond0 eth0 eth1
```

(Mucho mucho thanks to tcpip4lyfe for [providing an excellent bonding how-to]("http://ubuntuforums.org/showthread.php?t=785471")!)

This works well enough. The trouble is, I don't want static IP assignment. For purposes of keeping everything centrally managed, I maintain a separate DHCP server; I want my bonded interface to get a DHCP lease on boot. Unfortunately, simply changing the relevant iface line above to dhcp (and, of course, removing the fixed-assignment lines) doesn't work - the interface comes up just fine, but it doesn't get a DHCP lease. Manually starting dhclient3 after boot works - I get a lease immediately. I notice that doing this results in two instances of dhclient3 running:

>ps aux | grep dhcp
```
dhcp      4440  0.0  0.0  15108   964 ?        Ss   16:42   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.bond0.pid -lf /var/lib/dhcp3/dhclient.bond0.leases bond0
dhcp      4918  0.0  0.0  15112   768 ?        Ss   16:45   0:00 dhclient3 bond0
```

The first instance is apparently what's started during boot up, and it fails to get a lease. The second is my manual attempt to start DHCP.

Does anyone know of a way that my bond0 interface can get its DHCP lease automatically on boot-up? Is there some specific sequence that needs to happen? This seems like it should be something so simple, but I've been banging my head against this problem all day! :confused:

---

### Post by Kromey on 2008-07-20
I managed to figure it out. For anyone else who might find themselves needing this, the configuration is the same as above; all that is needed is to change the iface configuration type to "manual" and then add a post-up command after the network adapters are slaved to fetch the DHCP lease. Turns out the issue was the bonding adapter trying to get a DHCP lease before it had a physical adapter to send the request on.

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Bonding interface
auto bond0
iface bond0 inet manual
  post-up ifenslave bond0 eth0 eth1
  post-up dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.bond0.pid -lf /var/lib/dhcp3/dhclient.bond0.leases bond0
  pre-down ifenslave -d bond0 eth0 eth1
```

There probably should be a pre-down to release the DHCP lease, but this seems to work well enough, especially since this server happens to have a fixed DHCP lease.

---

### Post by rsh2000 on 2010-12-15
Thanks a lot :)
Your post helped me after 3 years !

---

### Post by matt_garman on 2011-03-21
This post also helped me tremendously.  Although, I had to tweak the bond0 stanza in /etc/network/interfaces a bit for my Ubuntu server 10.4LTS install.  I hope this can be helpful to others:

```

auto bond0
iface bond0 inet manual
    up ifconfig bond0 up
    up ifenslave bond0 eth0 eth1
    up dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.bond0.pid -lf /var/lib/dhcp3/dhclient.bond0.leases bond0
    down ifenslave -d bond0 eth0 eth1

```

---

