---
title: "Possible to have both ethernet ports active on different IP ranges?"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by YorYor on 2008-05-09
Very simple problem, but apparently the solution isn't so simple (at least to me).

1. Server sits in a datacentre.
2. Currently one interface (eth0) is bridged in order to allow vmware images to access the internet, example IP: 192.168.0.69/28.
3. I intend to have the other interface (eth1) activated in order to allow SSH access only, example IP: 192.168.1.6/29.
4. The problem is, when both active, I can't ping the server from the outside world. From the server, I can ping the gateways and the gateways do respond.

The moment I activate eth1, the connections break.
Tried: Setting metric 200 in the interfaces file but doesn't seem to get respected (ifconfig still shows metric 1)
Tried: Setting "ipconfig eth1 192.168.1.6 netmask 255.255.255.255 up" and still no joy

Q: Is what I plan to do achievable at all?
Q: Is the cause a standard conflict due to multiple paths to the same end node, or is it due to router/switch?

Would appreciate if anyone could give me some pointers, thanks!

---

### Post by Iowan on 2008-05-09
I'm probably off base (again) - bedtime here...
I presume you meant **ifconfig**, and the netmask (255.255.255.255) seems a little tight. 

You set up address, etc., in **/etc/network/interfaces** file?

---

### Post by YorYor on 2008-05-09
Yup, that was a typo.
Yup, everything was set up.

/etc/network/interfaces
```

brctl addbr br0
auto br0
iface br0 inet static
        address 192.168.0.69
        netmask 255.255.255.240
        network 192.168.0.0
        broadcast 192.168.0.79
        gateway 192.168.0.65
        dns-nameservers 192.168.0.66
bridge_ports eth0

auto eth1
iface eth1 inet static
        address 192.168.1.6
        netmask 255.255.255.248
        network 192.168.1.0
        broadcast 192.168.1.7
        metric 200
        gateway 192.168.1.1
        dns-nameservers 192.168.0.66

```

The 255.255.255.255 was just trying things out... kinda like a i-don't-care-just-try-it attempt. ;p

---

### Post by helgman on 2008-05-10
From the look of your setup you are using two gateways, that might confuse the system. The problem might simply be in how your system build it's routing table and what path (interface) it chooses to send packages.

Have a look at (or post) *route -n*, there might be a clue there.

Regards,
Helgman

---

### Post by YorYor on 2008-05-10
helgman,

What should I look out for, and what should I change in order not to confuse the system?
I want all outgoing packets originating from the system to go via eth0, but any replies that was directed at eth1 to leave via eth1.
So eth0 would be the default route, while eth1 should primarily only respond when talked to (e.g. ping or ssh).

---

### Post by helgman on 2008-05-10
There are two things involved here ... unfortunately.

First we have the entering package, and then we have the exiting package. The entering package arrives at one of the interfaces and is transported to the correct application/service. There it's processed and then sent back "down" to the interface (yes, this is really simplified) where the destination of the packaged is matched against the routing table and sent out one of the interfaces.

Now ... when you check your routing table you might find something like this (not exactly this but something similar):
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

This table is what the system checks for knowing where to send the package. If the packaged is destined for an address in the 192.168.0.0/24 network then it goes out eth0 and if it's for 192.168.1.0/24 then eth1. Simple enough. But what if it's heading for 10.0.0.0/8? There is no exact match in the table ... so it looks for a default. And, lo and behold, it has two! I've not researched how Linux (or Ubuntu) goes about when it has to use the default route and there is two of them, but that might be where your problem is.

To solve the problem you have to look through your (network) design. For example, is eth1 also connected to an network that is connected to the Internet and do you need to use eth1 for Internet access? Do eth1 need to communicate outside the network it's attached to? If not ... eth1 has no use for a default gateway (comment out the gateway statement in the interfaces file).

If eth1 has to communicate outside it's network but only with networks that you, then you could add routs to these networks and have them exit by eth1. This is not the "nicest" solution, but it's a solution.

I don't know if it's possible to "bind" sessions to specific interfaces, that is, if the session is initiated on eth1 then it stays there. My guess is that it is, I just don't know how. I've never investigated that "problem", but is that really what you need?

Regards,
Helgman

---

### Post by YorYor on 2008-05-11
Thanks Helgman,

Perhaps that is my problem. I'll give it a shot sometime soon.
Thanks for taking the time to explain!

Roy

---

