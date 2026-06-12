---
title: "Cannot see router, router cannot see ubuntu machine"
date: 2005-08-10
forum: Networking &amp; Wireless
---

### Post by wildbillnj1975 on 2005-08-10
[FONT=Courier New]Just installed ubuntu on a clean machine.  Connecting to a router which connects to DSL modem.

All hosts have static IP address.

Windows machines see router and internet fine.

Ubuntu machine cannot see the router, and the router cannot see it (cannot ping it from the windows machine, anyway).

When I set up the system it had a bad NIC, which I replaced with a new one (a Netgear ethernet model).

I've tried setting up /etc/hosts, /etc/resolv.conf, yadda yadda but no luck.  Can't figure out what might still be broken.

# route -n
Destination   Gateway      Genmask        Flags  Metric  Ref  Use  iface
192.168.1.0   0.0.0.0      255.255.255.0  U      0       0    0    eth0
0.0.0.0       192.168.1.1  0.0.0.0        UG     0       0    0    eth0

On the ubuntu machine (which I have named "ubuntu") these work:

ping ubuntu
ping 192.168.1.99
ping localhost
ping 127.0.0.1

This does not work:

ping 192.168.1.1
ping 192.168.1.10   (my windows PC)

Something simple must be missing...please help!

[/FONT]

---

### Post by blind0wl on 2005-08-11
What does ```
ifconfig eth0
```
say?

And can you post your /etc/network/interfaces?

---

### Post by wildbillnj1975 on 2005-08-11
Well, I got that fixed.

Turned out to be a cabling issue  ](*,) 

The wire is buried in a wall, and somewhere along the line had a nail driven through it.  I swapped it with a 50-foot cable running across the carpet and it worked fine.  Now I hust have to open up the wall and replace the damaged line.

Hmm...which do I enjoy more, tweaking my system or tearing apart my house?   :?

---

