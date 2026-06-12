---
title: "Please interpret these ifconfig lines"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by weedwacker on 2009-07-06
When I type "ifconfig" and get the result I find these two addresses:
[INDENT]**HWaddr 00:0e:0c:76:b6:49**[/INDENT]
[INDENT]**inet6 addr: fe80::20e:cff:fe76:b649/64**[/INDENT]
Is anyone able to interpret what this means?  Does this have anything to do with the DNS information?

---

### Post by yeats on 2009-07-06
> HWaddr 00:0e:0c:76:b6:49

This is your network adapter's MAC address, which is a unique number that identifies your computer on a network.

> inet6 addr: fe80::20e:cff:fe76:b649/64


IPv6 is a reimplementation of Internet Protocol that adds a fifth and sixth group of numbers to IPs.  See this:

[http://en.wikipedia.org/wiki/IPv6](http://en.wikipedia.org/wiki/IPv6)

> Is anyone able to interpret what this means? Does this have anything to do with the DNS information? 

No, your DNS information will be in /etc/resolv.conf.

---

### Post by ibutho on 2009-07-06
The hardware address is the MAC address of your network interface card. The inet6 address is the IPV6 address of your network interface card.

---

### Post by weedwacker on 2009-07-06
Wow!

Thanks for the quick replies.  This is exactly what I needed to know.

---

