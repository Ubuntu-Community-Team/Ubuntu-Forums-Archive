---
title: "2 Ethernet Cards in Server"
date: 2014-01-22
forum: Networking &amp; Wireless
---

### Post by charles6 on 2014-01-22
Hi guys,

I have 2 Ethernet cards in my server and there is only 1 connected at a time and I would like to have the secondary active in case I need it I can switch the cable from the first one to the second one for troubleshooting.

When I setup the interfaces file and restarted the network, the second card wouldn't work, I would get a RTNETLINK error and only 1 card was active even after a reboot.  Any suggestions why that would happen?

I had setup the following in my /etc/network/interfaces file:

```
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.0.100
    netmask 255.255.255.0
    broadcast 192.168.0.255
    gateway 192.168.0.1
    dns-nameservers 192.168.0.1
    
auto eth1
iface eth1 inet static
    address 192.168.0.101
    netmask 255.255.255.0
    broadcast 192.168.0.255
    gateway 192.168.0.1
```

---

### Post by Iowan on 2014-01-22
There may be some ways around it, but having two interfaces in the same subnet is probably the issue.
(Having the broadcast addresses outside the subnet probably doesn't help.)

---

### Post by charles6 on 2014-01-22
> **Iowan said:**
> There may be some ways around it, but having two interfaces in the same subnet is probably the issue.
(Having the broadcast addresses outside the subnet probably doesn't help.)

yeah the broadcast address was my bad sorry, I copy and pasted from the wrong source, it was actually 192.168.0.255 when I was having the issue.

---

### Post by Iowan on 2014-01-22
Although it doesn't solve your eventual goal, try moving the 2nd interface to a different subnet.

---

