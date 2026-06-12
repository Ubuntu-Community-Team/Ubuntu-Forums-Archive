---
title: "Where can I find my gateway and name servers?"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by commodore on 2006-12-28
I have a DHCP and I want to create a static IP but I don't know my gateway address! It's very easy with windows - ipconfig /all but ifconfig gives me all kind of useless ****. Where can I find my gateway and maybe also name servers?

---

### Post by po0f on 2006-12-28
commodore,

I don't know about gateways, but name servers are in /etc/resolv.conf:
```
[FONT="Courier New"]$ cat /etc/resolv.conf[/FONT]
```

---

### Post by bapoumba on 2006-12-28
How do you connect to internet ? If this your own private network, gateway should be your own router IP. If on another type of network, just ask the network admins, they should give you the IP.

In any case, DNS are in /etc/resolv.conf as po0f said, and the rest in /etc/network/interfaces.

```
~ $ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# interface ethernet univ [COLOR="Red"]<-- my work settings, eth0 with static IP[/COLOR]
iface eth0 inet static
address XXX.XXX.XXX.XXX
netmask XXX.XXX.XXX.XXX
gateway XXX.XXX.XXX.XXX
auto eth0

# interface wifi maison [COLOR="Red"]<-- my home settings, wifi with DHCP[/COLOR]
iface ra0 inet dhcp
wireless-essid XXX
wireless-key XXX
auto ra0

```

```
~ $ cat /etc/resolv.conf
nameserver XXX.XXX.XXX.XXX

```

---

### Post by commodore on 2006-12-28
Thanks people.

---

### Post by amo-ej1 on 2006-12-28
> 
edb@rogue:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


route -n (-n for showing ip's instead of dns names) shows you the routing table, and in this case 192.168.1.1 would be my default gw (destination 0.0.0.0 with mask 0.0.0.0).

---

### Post by MrHorus on 2006-12-28
> **commodore said:**
> I have a DHCP and I want to create a static IP but I don't know my gateway address! 

I'm curious, what are you ultimatly trying to achieve?

I ask as a static IP is something you are generally given, not something you create.

If your ISP is running DHCP then you won't be able to have a static IP unless you specifically ask them for one and even then, many ISPs will charge for this or flat-out refuse.

---

