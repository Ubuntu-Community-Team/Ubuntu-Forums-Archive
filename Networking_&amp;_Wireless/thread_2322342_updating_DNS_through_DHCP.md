---
title: "updating DNS through DHCP"
date: 2016-04-27
forum: Networking &amp; Wireless
---

### Post by christopher_lee2 on 2016-04-27
I am running several Ubuntu 14.04 servers, and they request DHCP leases from a Windows DHCP server.  If I run "dhclient -r;dhclient" they successfully send their hostname to my Windows DNS server (authentication is currently disabled), and I can reach them from my network.

However, I've noticed that on reboot, they successfully request an IP address, but they do not update their DNS entry.  Similarly, it seems like the DNS entry is occasionally lost, perhaps when the DHCP lease expires and is renewed.

Is there another mechanism that Ubuntu uses to refresh its DHCP lease that bypasses dhclient?  (I do not have Network Manager installed, or any of the desktop for that matter.)

/etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp

```

/etc/dhcp/dhclient.conf:
```

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;


#send host-name "andare.fugue.com";
send host-name = gethostname();
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    dhcp6.name-servers, dhcp6.domain-search,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers,
    dhcp6.fqdn, dhcp6.sntp-servers;

```

---

