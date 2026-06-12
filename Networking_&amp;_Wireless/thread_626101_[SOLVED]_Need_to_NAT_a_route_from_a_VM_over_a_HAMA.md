---
title: "[SOLVED] Need to NAT a route from a VM over a HAMACHI connection"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by cannontrodder on 2007-11-28
**Overview**

I'm running gutsy gibbon and hosting an XP virtual machine on it. My host is connected to my work windows machine over hamachi and I have set up forwarding on that work machine so I can actually connect to any machine on my work network by just specifying it's IP address.

I now need to set things up so my virtual machine can route traffic to the work network via the ubuntu host and over hamachi and this is where I am failing!

**Details**

Home network 10.0.0.0/24 behind a linksys gateway broadband router (ip 10.0.0.1)
Work network 192.168.0.0/24 which I am connected to via a hamachi tunnel

Home machine set to static 10.0.0.4 address with 10.0.0.1 as default gateway.

I have created a network bridge (br0) which has this 10.0.0.4 address assigned to it and both my ethernet NIC (eth1) and my virtualbox virtual adapter vbox0 are bridged to it.

The result is that my VM gets it's own address on my LAN in the 10.0.0.0/24 range and I can ping from my host to my VMs ip and vice-versa, I can also access the web on both fine as they both have my router as their default gateway.

This is my routing table on the host:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 br0
192.168.0.0     workpc          255.255.255.0   UG    0      0        0 ham0 ****
5.0.0.0         *               255.0.0.0       U     0      0        0 ham0
default         10.0.0.1        0.0.0.0         UG    0      0        0 br0
```

NOTE: I added the 192.168.0.0 route and 'workpc' is the hamachi ip that is assigned to my work machine in the 5.0.0.0 range.

I can now ping any machine on my work's network from my host, as I enabled ip forwarding on my work XP machine and the above route is set. So far so good. I now need to be able to talk to this network from within my VM.

I've enabled forwarding (the command 'sysctl net.ipv4.ip_forward' shows me that 'net.ipv4.ip_forward = 1') and if I set the default gateway on my VM to be my host pcs address of 10.0.0.4, I can actually ping ip addresses on the Internet (bbc news etc) from within my virtual machine.

[COLOR="DarkGreen"]It just won't ping machines on the work network despite me being able to do it on my host and despite my host NATing perfectly through to the Internet.[/COLOR]

Any ideas what I need to do to get this to work???

---

### Post by cannontrodder on 2007-11-29
I'm thinking I may need to set up some sort of iptables route. Is there a way I can check or trace where packets are actually going? If I knew that, I could redirect them, I suppose?

---

### Post by cannontrodder on 2007-11-29
I think I'm talking to myself here! ;)

I always post the answer to my own questions if I find them, it may help some other lost soul....

```


HAMNIC="ham0" #name of interface that controls vpn tunnel
WORKNET="192.168.0.0/24" #definition of work network
VIRTUALNIC="vbox0" #name of virtual interface that VM connects to (must be set in virtualbox settings)

sudo iptables -t nat -A POSTROUTING -o $HAMNIC -d $WORKNET -j MASQUERADE
sudo iptables -A FORWARD -i $VIRTUALNIC -o $HAMNIC -d $WORKNET -j ACCEPT
```

---

