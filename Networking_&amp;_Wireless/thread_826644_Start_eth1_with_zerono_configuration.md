---
title: "Start eth1 with zero/no configuration"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by dowxx on 2008-06-12
Hi

I search the Ubuntu forums and I Google but found nothing that can help me resolve my issue.

I have a Ubuntu server 7.10 and 2 network cards installed. I use this server only as a host for virtual servers (WMware).

My */etc/network/interfaces* listing:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 193.231.100.130 193.231.100.134
```

I use a virtual router wich uses my *eth0* for LAN and *eth1* for WAN

When i boot my Ubuntu host i have to manualy enable *eth1* for it to be available in my virtual router (*sudo ifconfig eth1 up*)

All I ask is how can I enable *eth1* at Ubuntu startup?

---

### Post by komputes on 2008-06-12
I think you just need to add a line for eth1 in /etc/network/interfaces.

---

### Post by dowxx on 2008-06-12
I was searching the internet in hope of finding the answer and I found the term *promisc* and search the Ubuntu forums for that. I came across a thread that explained accurately what I had to do.

[http://ubuntuforums.org/showthread.php?t=472856](http://ubuntuforums.org/showthread.php?t=472856)

[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

As komputes sugested I added the following to my *interfaces*:

```
# The secondary network interface
auto eth1
iface eth1 inet manual
        up ifconfig $IFACE 0.0.0.0 up
        up ip link set $IFACE promisc on
        down ip link set $IFACE promisc off
        down ifconfig $IFACE down
```

Works like a charm :)

---

