---
title: "DHCP for Raspberry Pi Direct Connect"
date: 2015-11-14
forum: Networking &amp; Wireless
---

### Post by jnod117 on 2015-11-14
Hello,

I'm trying to set up a dhcp server that will allow me to connect directly to a raspberry pi with ethernet. I followed a few guides, but I keep running into this same issue:

/var/log/syslog:
```
Wrote 0 leases to leases file.

No subnet declaration for eth0 (no IPv4 addresses).
** Ignoring requests on eth0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth0 is attached. **
 

Not configured to listen on any interfaces!
```

/etc/network/interfaces:
```
auto loiface lo inet loopback


auto eth0
iface eth0 inet static
    address 192.168.2.1
    netmask 255.255.255.0
```

/etc/dhcp/dhcpd.conf:
```
default-lease-time 600;max-lease-time 7200;


subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.10 192.168.2.100;
  option subnet-mask 255.255.255.0;
  option broadcast-address 192.168.2.255;
  option routers 192.168.2.1;
}
```

/etc/default/isc-dhcp-server:
```
INTERFACES="eth0"
```

Am I missing something?

Thanks.

---

### Post by TheFu on 2015-11-15
yes. On  the raspberry pi:
```

auto eth0
iface eth0 inet dhcp
```

Remove the rest of the stanza and hopefully the l0 stanza isn't screwed as posted above.

If the eth0 is for the Ubuntu server, the stanza is missing the **gateway** and DNS parts.

```
auto eth0
iface eth0 inet static
    address 192.168.2.2
    netmask 255.255.255.0
    gateway  192.168.2.1
    dns-nameservers 8.8.8.8
```

Usually the gateway is 192.168.2.1  on a network like this, but it could be any IP on the same subnet. The gateway needs to point to the real gateway, of course.

After the changes, restart the network or reboot.

---

### Post by jnod117 on 2015-11-16
It's working now, thanks!

---

