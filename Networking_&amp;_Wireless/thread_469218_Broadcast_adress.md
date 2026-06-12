---
title: "Broadcast adress"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by Stefaan on 2007-06-09
I'm connect wrless
ip = 192.168.1.100
Bcast: 192.168.1.255

Can somebody explain what the broadcast is?

Thx in advance

---

### Post by spd106 on 2007-06-09
The broadcast address is a special address on ip based networks. It should not be used as a host address as this will conflict with some network protocols. Netbios is an example of a protocol that uses the broadcast address. All packets send to the broadcast address are read by all hosts on that network, additionally the those packets are limited to the local network and will not be forwarded by a router.

The broadcast address is calculated from the network address and the subnet mask (netmask). So most cases where a class C netmask is being used (255.255.255.0), the broadcast address uses the first three octets and adds 255 for the forth.
e.g

192.168.1.100 and
255.255.255.0

gives

192.168.1.255

If you want more detail, I suggest you find a book about TCP/IP. It's fairly tricky to grasp at first, but after a while it usually sinks in. Understanding the binary behind it helps a lot.

You shouldn't need to specify the broadcast address most of the time, it's usually calculated for you. The only time it really needs to be checked is if you have a weird classless subnet mask, i.e. 255.255.254.0 or 255.255.255.248. These are rare outside of ISPs or large organisations.

Sorry if this post has droned on a bit.

---

