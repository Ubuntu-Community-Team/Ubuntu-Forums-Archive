---
title: "Route keeps disapearing/adding static route"
date: 2020-02-10
forum: Networking &amp; Wireless
---

### Post by joe297 on 2020-02-10
Hi,

Before I start I will say I am not well schooled in Ubuntu and spend the majority of my time using Windows devices, this is something I am working on rectifying though! I am encountering a bit of a strange issue. I am running a virtual machine on VMware. The operating system is Ubuntu 18.0.4. When I do a ```
ip route
``` I get the following output.

```
default via 192.168.19.1 dev ens160 proto static
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown
192.168.0.0/20 dev br-4b2ad03c78f9 proto kernel scope link src 192.168.0.1
192.168.19.0/24 dev ens160 proto kernel scope link src 192.168.19.113
```

First of all I don't understand why or where the 192.168.0.0/20 route is coming from. This route is causing me issues. It is forcing me to manually add a route in order to get the box to communicate with the 192.168.0.3/24 subnet. If I do the following it routes fine to the 192.168.3.0/24 subnet which is as expected.

```
 sudo ip route add 192.168.0.3/24 via 192.168.19.1 dev ens160
```

However every couple of weeks this route disappears and I have to go back into the box to add it again. 

So I guess the questions I have from encountering this situation is the following:
1. How do I add the route to keep it persistent?
2. How can I find out why or where the 192.168.0.0/20 route is coming from?

Any help or pointers on this would be greatly appreciated. 

Kind regards, Joe.

---

