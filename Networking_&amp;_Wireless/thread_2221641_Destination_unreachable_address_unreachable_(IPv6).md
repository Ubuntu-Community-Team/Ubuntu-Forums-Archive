---
title: "Destination unreachable address unreachable (IPv6)"
date: 2014-05-03
forum: Networking &amp; Wireless
---

### Post by richard51 on 2014-05-03
Could someone shed some light on why this happens...

If I try and ping6 my own labtop (*it's self*) using the IPv6 address, it says (*destination unreachable, address unreachable*), when **not** connected to the local network.

Here is my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback
iface lo inet6 loopback

# The local area network interface
auto eth0
iface eth0 inet6 static
pre-up modprobe ipv6
address fd51:xxxx:xxxx:xxxx::1/64
netmask 64
```

When not connected to the local network, ping6 fd51:xxxx:xxxx:xxxx::1 replies, (*destination unreachable, address unreachable*).

This may not seem a problem, when it's not connected to the local network, but their is security software on the laptop that uses that address to validate itself (*and to others when connected to the local network*), I have to use that ULA address, and I cannot use the labtop away from the office anymore since we moved over to IPv6.

---

### Post by ian-weisser on 2014-05-04
I think you need to talk to your LAN's administrator.

---

### Post by richard51 on 2014-05-05
> **ian-weisser said:**
> I think you need to talk to your LAN's administrator.

*He knows less than I do.*..

I actually set up a test server of my own using Ubuntu 14.04 server and IPv6 addressing to test if I could emulate this behaviour. I found that any static IPv6 addresses were ignored if there wasn't a hard link (*i.e not connected to a router or a switch*). Even though it had a static global address, it wasn't given a link local address and **radvd** wouldn't provide a default route. I added a link local address, but it wouldn't let me provide a default route (*no route to host*), whenever I tried. I still couldn't ping my own static global address (*the ULA*).

There must be a correct way to do this, otherwise, if this is by design, it sucks!

---

### Post by lisati on 2014-05-05
Is the network you are using configured for IPv6? Some routers don't handle it well by default: mine are geared more towards IPv4.

On a side note, it's sometimes easier (and more appropriate) to reserve static IP addresses on the network's router.

---

### Post by richard51 on 2014-05-05
> **lisati said:**
> Is the network you are using configured for IPv6? Some routers don't handle it well by default: mine are geared more towards IPv4.

On a side note, it's sometimes easier (and more appropriate) to reserve static IP addresses on the network's router.

The network is local and uses a switch not a router. All client laptops have static IPv6 ULA (*fd00 range*) addresses. They work fine while connected to the switch... but not when disconnected. The unique local IPv6 address (*which is set statically on each laptop*) cannot be used (*no route to host*). This is a static local address and it cannot access itself.

If I was to set a static IPv4 address on my laptop to say, 192.168.0.1, and ran ping 192.168.0.1 in the terminal (*while disconnected from any switch, router, etc*), it would still respond to the ping. So, why doesn't IPv6?

Like I said in my previous post, we have security software which relies on this, and IPv6 doesn't seem to work this way. I think it has to have a route set, but I have tried ::1, ::/0, and setting a link local address, but it always says no route to host.

---

