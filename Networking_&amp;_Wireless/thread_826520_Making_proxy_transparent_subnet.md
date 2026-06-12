---
title: "Making proxy transparent subnet"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by chewearn on 2008-06-12
Background:
In my work place, main internet access requires going by a proxy.  For normal work related tasks, using company's IT approved PCs, this is no problem.

However, as part work tasks, we have to occasionally connect devices to the internet, e.g. media server, gadgets, etc (there is a separate network without proxy, but this is located at an inconvenient place, so I will rule this solution for the moment.)

Instead, I am currently using a PC as NAT to a local subnet.  Inside the subnet, it is possible to connect various devices without interfering with the corporate network.  Unfortunately, devices that needs to connect to the internet still have to be given a proxy access.

Question:
Is there anyway to set-up a intermediary machine, where:
1. The machine is give proxy access
2. it does the NAT from corporate network to the subnet
3. it transparently "add proxy permission" to the traffic in the subnet, such that the devices in the subnet don't have to be aware of the proxy

Thanks for any input.

---

