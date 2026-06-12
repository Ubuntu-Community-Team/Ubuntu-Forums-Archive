---
title: "Disable dhcp-requested IP address and use static"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by fortran01 on 2006-11-29
Initially, I used a static IP address. But I reconfigured it using the
System > Networking gui in Xubuntu to connect to a DHCP-enabled router.

When I returned to my office, I tried to configure it back to my static IP address. Unfortunately, there's some moron who installed a DHCP server. I can  get back to my old static IP address using the /etc/network/interfaces file:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 10.32.2.222
netmask 255.255.128.0
gateway 10.32.0.1
```

Then, I restart the network using /etc/init.d/networking restart

But after some time it fetches an IP address from some DHCP server in the network. As far as I know, my network interface requested this IP address from the DHCP server.

So, how do I disable the dhcp requesting so I can stay in my static IP address?

Thanks for any help.

---

