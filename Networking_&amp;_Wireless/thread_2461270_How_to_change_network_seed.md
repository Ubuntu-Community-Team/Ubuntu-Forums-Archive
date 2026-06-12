---
title: "How to change network seed"
date: 2021-04-27
forum: Networking &amp; Wireless
---

### Post by merken667 on 2021-04-27
Hello Ubuntu Users,

I tried to search the network on how to reduce the speed limit of my NIC but no luck. For ex. from 100Mb/s to 10 or less if possible. I found out I could do this with *ethtool*, but I wish not to install additional tools if I already have *IP* tool which should be more advanced then the predecessor *ifconfig*. 

Any idea how to do it with the advanced tool like *IP*?

I thought something like: ip link set enp2s0 .... but nothing seems to solve my issue. I ask you for help here. 

thx

---

### Post by scorp123 on 2021-04-27
Sorry but why would you want to do that? If I remember right Ethernet has auto-negotiate capabilities and e.g. a device communicating at 1 Gbit/s will automatically lower its speed if another device on the same network requires that. In other words: Yes, a modern 1 Gbit/s Ethernet device can still stalk to an ancient 10 Mbit/s Ethernet device if need be.

What issue you are you trying to solve? :-k

---

### Post by merken667 on 2021-04-27
@scorp123, for testing purposes

---

### Post by scorp123 on 2021-04-27
> **merken667 said:**
> @scorp123, for testing purposes

To simulate e.g. a dial-up network or something like that? I'd use something like "wondershaper" for such a task.

[https://vitux.com/how-to-limit-network-bandwidth-in-ubuntu/]("https://vitux.com/how-to-limit-network-bandwidth-in-ubuntu/")

---

