---
title: "Duplicate MAC adress on Network cards"
date: 2020-03-18
forum: Networking &amp; Wireless
---

### Post by fenyxiakk on 2020-03-18
Hey, i have problem with network cards manager.

enp2s0    Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:fa  ( LOCAL )
enp3s0    Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:fa

When i try use both of them, i can't connect with devices in one network of them ( LOCAL )

---

### Post by TheFu on 2020-03-18
And ?

The physcal ethernet links have just a few requirements.  Having unique HW MACs when on the same physical network is one of those mandates. That's how ethernet works.

---

### Post by fenyxiakk on 2020-03-19
But thats non unique? Both are the same.

---

### Post by TheFu on 2020-03-19
> **fenyxiakk said:**
> But thats non unique? Both are the same.

Unless they are using the exact same CAT5e port, they must have unique MACs.

The output from this would be helpful:
```
sudo lshw -C network
```
Please use code tags, like I have, so the output posted here is readable.

---

