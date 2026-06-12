---
title: "Statically configured IP address lost"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by jkyro on 2007-02-01
I had a really weird problem. I've got Ubuntu Dapper. 
It was installed with only one network interface, eth0. Another was added some time after the installation, it was designated eth2.

Both interfaces have static IPv4 addresses. One(eth0) has a class C private address and the other(eth2) is connected to the Internet via a bridging ADSL modem and it has a global iPv4 address.

At first, everything was fine. The next day the machine didn't respond to anything coming from the Internet. Upon a closer look it turned out that eth2 didn't have an IPv4 address at all! Instead it had a global-scope IPv6 address. The other interface eth0 was working fine. 

The only suspicious-looking thing I found was in /var/log/kern.log:
---8<----
Feb  1 16:34:47 foobar kernel: [17179840.588000] IPv6 addrconf: prefix with wrong length 96
Feb  1 16:35:55 foobar kernel: [17179908.476000] IPv6 addrconf: prefix with wrong length 48
--->8---

Thus, I tried to fix the situation by disabling IPv6 from the kernel and rebooting. After that, the network still didn't work. It turned out that the second interface had changed its name from eth2 to eth1, which was easily fixed.

So, now everything seems to be working. 

I'd just like to know what the heck is going on here? Like, 

1) Why did eth2 loose its IPv4 address? The only thing I can think of is that the ISP has a rogue IPv6 router that enables the interface to negotiate an IPv6 address for itself. Does IPv6 take precedence over IPv4 in that case?

2) What kind of logic makes disabling IPv6 change tha name of a network interface? 

I'd be really grateful for all pieces of information regarding this problem. I'd also be able to believe that disabling IPv6 has really fixed the problem.

Thanks in advance!

---

