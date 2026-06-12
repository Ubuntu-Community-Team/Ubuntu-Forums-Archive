---
title: "one interface and two networks?"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by rubbrduck on 2007-01-04
Hi there everybody,

I need to be connected to two different segments of the local network (some sort of big company).

My ip address belongs to the 10.7.*.* range of the network, but I also need to communicate with machines residing on the 10.0.*.* range (vmware virtual servers and stuff).

Now I know this has to do with the route command but I've been combing my brain for days now to no avail. I also looked into the possibility of using interface alias (e.g. eth0:0 eth0:1 etc. but I learnt that on modern kernels this has fallen out of style)

So the question is: how do I, from the network range 10.7.0.0, gain the ability to connect also to the 10.0.0.0 range using a single network interface, without losing the possibility of external access (to Internet, for example) through the default gw?

Thanks for your attention :-)

---

### Post by darrenm on 2007-01-04
Easy. Alias it:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 172.16.103.230
netmask 255.255.0.0
gateway 172.16.1.99

auto eth0:1
iface eth0:1 inet static
address 10.10.0.23
netmask 255.255.255.0

```

---

### Post by rubbrduck on 2007-01-05
> **darrenm said:**
> Easy. Alias it:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


```

Care to exemplify practically?

Here's the situation:

eth0 (dhcp) 10.7.25.167 connects to 10.7.* network and accesses externally through 10.7.25.250 gw.

eth0:1 (static) e.g. 10.0.0.80 connects to 10.0.* network through 10.0.0.1 gw

how do I route packets bound to the 10.0.* network through the single eth0 interface?

Here's what I've tried:

excerpt /etc/network/interfaces

```
iface eth0 inet dhcp

iface eth0:1 inet static
address 10.0.0.80
netmask 255.255.255.0
```

```
rubbrduck@rubbrduck-laptop:~$ sudo route add -net 10.0.0.0 netmask 255.255.255.0 gw 10.0.0.1 dev eth0
rubbrduck@rubbrduck-laptop:~$ sudo ifconfig eth0:1 up
SIOCSIFFLAGS: Impossibile assegnare l'indirizzo richiesto

```

The SIOCSIFFLAGS error is: Impossible to assign the requested address.

What is wrong with my logic? ](*,)

---

### Post by darrenm on 2007-01-05
> **rubbrduck said:**
> Care to exemplify practically?

Here's the situation:

eth0 (dhcp) 10.7.25.167 connects to 10.7.* network and accesses externally through 10.7.25.250 gw.

eth0:1 (static) e.g. 10.0.0.80 connects to 10.0.* network through 10.0.0.1 gw

how do I route packets bound to the 10.0.* network through the single eth0 interface?

Here's what I've tried:

excerpt /etc/network/interfaces

```
iface eth0 inet dhcp

iface eth0:1 inet static
address 10.0.0.80
netmask 255.255.255.0
```

```
rubbrduck@rubbrduck-laptop:~$ sudo route add -net 10.0.0.0 netmask 255.255.255.0 gw 10.0.0.1 dev eth0
rubbrduck@rubbrduck-laptop:~$ sudo ifconfig eth0:1 up
SIOCSIFFLAGS: Impossibile assegnare l'indirizzo richiesto

```

The SIOCSIFFLAGS error is: Impossible to assign the requested address.

What is wrong with my logic? ](*,)

You can't add a route to a network you are already on. The kernel can't route traffic and not route traffic at the same time ;)

You need to know the specific subnets you are going to route to, otherwise it will be trying to route back to your own subnet as that is part of 10.0.0.0 as well.

Then you add routes to them. E.g. if you have subnets of 10.0.100.0 and 10.0.101.0 that you need to route to...

```
iface eth0:1 inet static
address 10.0.0.80
netmask 255.255.255.0

route add -net 10.0.100.0/24 gw 10.0.0.1 dev eth0:1
route add -net 10.0.101.0/24 gw 10.0.0.1 dev eth0:1
```

edit: or ```
 route add -net 10.0.100.0/24 gw 10.1 dev eth0:1
route add -net 10.0.101.0/24 gw 10.1 dev eth0:1
``` works too ;)

---

