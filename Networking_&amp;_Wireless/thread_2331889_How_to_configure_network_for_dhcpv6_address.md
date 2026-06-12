---
title: "How to configure network for dhcpv6 address"
date: 2016-07-26
forum: Networking &amp; Wireless
---

### Post by eclay on 2016-07-26
Hello,  I'm having trouble getting ubuntu 16.04 server to request/get a dhcpv6 provided IP address when the networking.service restarts or the server reboots.  I'm able to manually run dhclient -6 and get a dhcpv6 provided IP address.  Under normal operation I just get a autoconfigured/peer probed IP address that is based on the subet and mac of the server.  This is my network configuration.

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto ens6
iface ens6 inet dhcp
iface ens6 inet6 dhcp

```

I've attempted to change any system setting with ipv6 and autoconf in it to 0 but that doesn't seem to change how this system attempts to get an ipv6 address.

```
defaults (leaving out lo interface)
net.ipv6.conf.all.autoconf = 1
net.ipv6.conf.default.autoconf = 1
net.ipv6.conf.ens6.autoconf = 1

new settings
sysctl -w net.ipv6.conf.all.autoconf=0
sysctl -w net.ipv6.conf.default.autoconf=0
sysctl -w net.ipv6.conf.ens6.autoconf=0

```
after systemctl restart networking.service I still get a autoconfigured IPv6 address not one provided by the dhcpv6 server.

Any idea how to make this system request a dhcpv6 provided IP instead of doing the autoconfig thing?

---

### Post by wildmanne39 on 2016-07-26
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by eclay on 2016-07-27
Looking at this a bit closer I find that with the /etc/network/interfaces file setup as follows

```
auto ens6
iface ens6 inet dhcp
iface ens6 inet6 dhcp

ifconfig ens6 down
ifup -v ens6

```

returns the following
```
Configuring interface ens6=ens6 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/ifenslave
+ [ inet = meta ]
+ IF_BOND_SLAVES=
+ [  ]
+ [  ]
+ [ -z  ]
+ exit
run-parts: executing /etc/network/if-pre-up.d/vlan

/sbin/dhclient -1 -v -pf /run/dhclient.ens6.pid -lf /var/lib/dhcp/dhclient.ens6.leases -I -df /var/lib/dhcp/dhclient6.ens6.leases ens6
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/ens6/00:1a:4a:bc:39:18
Sending on   LPF/ens6/00:1a:4a:bc:39:18
Sending on   Socket/fallback
DHCPREQUEST of 10.0.0.201 on ens6 to 255.255.255.255 port 67 (xid=0x4fcce6e0)
DHCPACK of 10.0.0.20.201 from 10.0.0.1
RTNETLINK answers: File exists
bound to 10.0.0.201 -- renewal in 20203 seconds.
/bin/run-parts --exit-on-error --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ifenslave
+ [ inet = meta ]
+ [  ]
run-parts: executing /etc/network/if-up.d/ip
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/upstart
Configuring interface ens6=ens6 (inet6)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/ifenslave
+ [ inet6 = meta ]
+ IF_BOND_SLAVES=
+ [  ]
+ [  ]
+ [ -z  ]
+ exit
run-parts: executing /etc/network/if-pre-up.d/vlan
/sbin/modprobe -q net-pf-10 > /dev/null 2>&1 || true # ignore failure.
/sbin/sysctl -q -e -w net.ipv6.conf.ens6.accept_ra=1

/bin/ip link set dev ens6  up
/lib/ifupdown/wait-for-ll6.sh
/sbin/dhclient -1 -6 -pf /run/dhclient6.ens6.pid -lf /var/lib/dhcp/dhclient6.ens6.leases -I -df /var/lib/dhcp/dhclient.ens6.leases ens6
Failed to bring up ens6.
```

Which gives me a link local ipv6 address and a autoconfigured ipv6 address.  I was under the impressing that "iface ens6 inet6 dhcp" was supposed to force getting the ipv6 address from dhcp not autoconfig.  I'm able to get a an IPv6 address via dhcp using the dhclient executing it manually and on a CentOS system.  So I believe the network/dhcpd6 server is configured properly.

What else should I look at here?

---

### Post by eclay on 2016-08-04
Just thought I would update this thread with what I've found thus far.

If I add a "pre-up sleep 10" to the interfaces file and reboot the system it gets a dhcp6 provided address along with an autocofiguration ipv6 address.  This doesn't seem to be the way it should work.
```
iface ens6 inet6 dhcp
 pre-up sleep 10
```

The other problem is that when I get a dhcpv6 address dhclient isn't sending the hostname/fqdn to the dhcpv6 server so it can do a dynamic dns update.  So I commented out the original send line in dhclient.conf and added a send fqdn.fqdn.
```
#send host-name = gethostname();
send fqdn.fqdn "eclaytest.slc.westdc.net";
```

---

### Post by eclay on 2016-08-04
I should also mention that dhclient is providing the fqdn to dhcpv4 and that's working just fine.

---

### Post by eclay on 2016-08-05
It looks like there is a fix applied to debian that hasn't made it's way to ubuntu as of today.

[https://anonscm.debian.org/cgit/collab-maint/ifupdown.git/commit/?id=bfca5654959d27603eb50747d9998b92f1d7eb41](https://anonscm.debian.org/cgit/collab-maint/ifupdown.git/commit/?id=bfca5654959d27603eb50747d9998b92f1d7eb41)

This removed the need for the following in interfaces file.
```
pre-up sleep 10
```

To fix the not sending the hostname/fqdn to the dhcp server I added the following to the dhclient.conf.
```
send host-name = "servername";
# for ipv6 /dhcpdv6
send fqdn.fqdn "servername.domain.com";
send fqdn.encoded on;
send fqdn.server-update on;
```

Substitute servername with the actual hostname.

---

