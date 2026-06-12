---
title: "iptables - multiple internal interfaces and one external interface"
date: 2015-07-14
forum: Networking &amp; Wireless
---

### Post by zhao01 on 2015-07-14
I'm using Ubuntu 14.04.2. I got eth0, eth1, eth2, eth3, eth4, and wlan0 on one machine. Among these interfaces, only eth0 is external. I want to masquerade eth1, eth2, eth3, eth4, and wlan0 with eth0. One thing should be mentioned is that these internal interfaces are not always online. However, when an internal interface becomes online, I hope it can work with eth0 immediately.

I tried to use iptables to achieve this, but failed. When I use

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

, **only the first online internal interface can work (no matter what it is). The second one cannot access the Internet.**
[B]
I also tried many FORWARD schemes, but still cannot make it work.[/B] Could anyone help me solve this problem?

BTW, eth0 has an "external" IP: 192.168.1.118. It is an internal IP but is assigned by my college and can access the Internet.
eth1 has an internal IP: 192.168.101.1, with a machine A 192.168.101.2 (assigned by DHCP) connecting to it.
eth2 has an internal IP: 192.168.102.1, with a machine B 192.168.102.2 (assigned by DHCP) connecting to it.
eth3 has an internal IP: 192.168.103.1, with a machine C 192.168.103.2 (assigned by DHCP) connecting to it.
eth4 has an internal IP: 192.168.104.1, with a machine D 192.168.104.2 (assigned by DHCP) connecting to it.
wlan0 has an internal IP: 192.168.0.1, with two smartphone E and F connecting to it.
Basically I wish to make machine A, B, C, D and smartphone E, F accessible to the Internet.

Many thanks.

---

### Post by Sandesh_Giri on 2015-07-14
Can this be of some help?

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by zhao01 on 2015-07-14
> **Sandesh_Giri said:**
> Can this be of some help?

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

The iptables way described in this article seems only work with one internal interface.

---

### Post by SeijiSensei on 2015-07-14
See if SNAT works better than MASQUERADE.

```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 192.168.1.118
```

---

### Post by zhao01 on 2015-07-14
> **SeijiSensei said:**
> See if SNAT works better than MASQUERADE.

```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 192.168.1.118
```

I tried but found that it does not help.

---

### Post by zhao01 on 2015-07-19
I solved the problem. The thing is that when you manually set IP addresses for multiple "Wired"s found in "System Settings -> Network", you should leave their gateways empty (namely, 0.0.0.0).

---

