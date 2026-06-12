---
title: "Application dropping broadcasted UDP packets"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by estratos on 2007-03-08
I'm running a simple application that listens for UDP broadcasted packets on a given port. My Ubuntu machine has the following network settings:

IP address = 192.168.1.17
Gateway = 192.168.1.1
Netmask = 255.255.255.0
Broadcast = 192.168.1.255

The application is correctly reading all datagrams sent to these broadcast addresses:

255.255.255.255
192.168.1.255

but it's dropping all packets sent to

192.255.255.255

(All these packets are sent by third-party applications)

Some people has told me that this is the correct behaviour of any Linux system but then, a friend says that on his Fedora machine the same app doesn't drop any packet.

Is there any parameter that I could modify in order to accept packets broadcasted to 192.255.255.255?

Thanks,

Daniel.

---

