---
title: "iproute2: problem with multiple gateway"
date: 2017-10-19
forum: Networking &amp; Wireless
---

### Post by dyndyn2 on 2017-10-19
Hi all,

My problem: the default route overrides all other routes.
I do have an ubuntu router with 4 nics and 2 gateway for internet

# ip route show> 
default via X.X.X.X dev eth0
X.X.X.0/24 dev eth0 proto kernel scope link src X.X.X.X
Y.Y.Y.0/24 dev eth3 proto kernel scope link src Y.Y.Y.Y
192.168.45.0/24 dev eth1 proto kernel scope link src 192.168.45.254
192.168.69.0/24 dev eth2 proto kernel scope link src 192.168.69.254

# ip route show table MYTABLE
> 
default via Y.Y.Y.Y dev eth3
192.168.45.0 via 192.168.45.254 dev eth1
192.168.69.0 via 192.168.69.254 dev eth2

# ip rule list
> 
0:      from all lookup local
32765:  from 192.168.69.206 lookup MYTABLE
32766:  from all lookup main
32767:  from all lookup default

On host 192.168.69.206 I do have a default gw 192.168.69.254.
To go on internet it works correctly, iproutes send traffic to gw Y.Y.Y.Y.
But I cannot reach subnet 192.168.45.0, it still goes on Y.Y.Y.Y instead 192.168.45.254.
To reach 192.168.69.0 is of course ok since it is the connected interface

So default route Y.Y.Y.Y overrides all subnets routes wich is not what I want.

Any idea would be welcome to solve this !
Thank you.

---

### Post by SeijiSensei on 2017-10-19
You're making this more complicated than it needs to be.  You shouldn't need any special routing tables for this at all.

First, I assume that the 192.168.45.0/24 subnet has a router of its own, call it 192.168.45.1.  On that router you need to add a static route for 192.168.69.0/24 via the IP address assigned to eth3.  Then traffic for 192.168.69.0/24 will be sent to the eth3 interface.

On the box in question, all you need is an explicit route to 192.168.45.0/24 like this:

```
sudo ip route add 192.168.45.0/24 via 192.168.45.1
```

You also need to make sure that packet forwarding is enabled in /etc/sysctl.conf.  Ubuntu, like most distributions, disables forwarding of packets across interfaces by default as a security measure.

---

