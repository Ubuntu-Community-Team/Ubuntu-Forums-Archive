---
title: "Iterface aliases."
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by jay019 on 2007-08-26
Hi there.

I was using interface aliases for apache virtual hosting purposes, but at boot time it hangs at the part where it is setting up network interfaces. I had an eth0, eth0:1, eth0:2 and eth0:3

What would cause the boot to hang at the configuration of network interfaces stage?

My /etc/network/interfaces file (commented out to get decent boot up times)...
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.30
netmask 255.255.255.0
gateway 192.168.0.30


# auto eth0:1
iface eth0:1 inet static
address 192.168.0.20
netmask 255.255.255.0
gateway 192.168.0.20

# auto eth0:2
iface eth0:2 inet static
address 192.168.0.21
netmask 255.255.255.0
gateway 192.168.0.21

# auto eth0:3
iface eth0:3 inet static
address 192.168.0.22
netmask 255.255.255.0
gateway 192.168.0.22

```

Is there anything wrong that needs to be changed?

Jay

---

