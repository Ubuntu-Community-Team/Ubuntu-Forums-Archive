---
title: "IP tables help"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by hammad1337 on 2008-10-28
I am trying this command:
```
iptables -t nat -p tcp -s 192.168.32.73 -j SNAT --to-source 192.168.32.50-192.168.32.100
```
but, I have recently discovered why it doesnt work because of this issue, mentioned in man iptables:
```
In Kernels up to 2.6.10, you can add several --to-source options. For those kernels, if you 
specify more than one source address, either via an address range or multiple --to-source 
options, a simple round-robin  (one after another in cycle) takes place between these 
addresses. Later Kernels (>= 2.6.11-rc1) don’t have the ability to NAT to multiple ranges 
anymore.
```
Is there a workaround for this, other than downgrading the kernel?
Also, if worse comes to worst, how can I downgrade the kernel, without re-installing the whole distro?
Any quick help, would be much appreciated. :)

---

