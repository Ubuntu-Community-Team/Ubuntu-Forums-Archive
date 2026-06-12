---
title: "How to disable the use of an IP address?"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by voipfc on 2007-03-22
How do you disable a single IP address on an adapter?

I have a block of 5 IP addresses assigned to my server. I am trying VMWare and I have assigned one of the IPs to the VM. When it starts it gives an error message: Error some other host uses IP address xxxx..

How can the use of that particular IP address be disabled in the host server. Even when I disable it in /etc/network/interfaces it still shows up.

---

### Post by Mr. C. on 2007-03-22
Can you explain what you mean by 5 IPs "assigned to my server" ?

An Ethernet card typically has one IP address.  The fact that your ISP or whatever allows you to use up to 5 is not a factor.

Show your /etc/network/interfaces file please, as well as output from:

ifconfig -a

MrC

---

