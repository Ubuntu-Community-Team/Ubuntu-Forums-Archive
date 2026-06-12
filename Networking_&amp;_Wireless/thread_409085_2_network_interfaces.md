---
title: "2 network interfaces"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by TheStriker on 2007-04-14
Hi!

I have a problem with Kubuntu 6.10 Edgy.

I have 2 network cards. One of them is connected to local network (DHCP), and other one is for ADSL (DHCP). And the problem is that they're not working together.......:(

If I'm switching on ADSL - local network is unreachable, etc.

How can I make both of them work in the same time??? Any suggestions?

Thanx.

---

### Post by felker2 on 2007-04-14
A possible cause is that on both networks / NICs the same IP-address-range is used. 

For example, if on both networks 192.168.1.x is used and both network cards are activated, Linux can't decide to which destination traffic for a host like 192.168.1.10 must be sent.

If this is the case, the solution is changing the IP-address-range on one of the networks.

---

### Post by TheStriker on 2007-04-14
> **felker2 said:**
> A possible cause is that on both networks / NICs the same IP-address-range is used. 

For example, if on both networks 192.168.1.x is used and both network cards are activated, Linux can't decide to which destination traffic for a host like 192.168.1.10 must be sent.

If this is the case, the solution is changing the IP-address-range on one of the networks.

Thanks. But I'm sure that it's not that.

My first interface using 10.*.*.* range, and ADSL interface have 195.*.*.* .

I think that's a problem in DNS. Cuz ADSL is rewriting DNS server's addresses of first interface.

How can I set static DNS's for first interface and keep DHCP detected DNS's for second?

---

