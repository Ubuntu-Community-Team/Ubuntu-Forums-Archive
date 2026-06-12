---
title: "VMware and wireshark"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by peterx14 on 2007-08-01
Hi,

I am having a problem accessing files on Ubuntu via VMware (Windows 2000 guest). Specifically, I can access files no problem in pretty much anything *except* Paint Shop Pro 7.

Anyway, I thought I'd try to see what the problem might be by using Wireshark to capture the network traffic but I can't! I'm running Wireshark as root and I have tried *all* the network interfaces (eth0, vmnet1, vmnet8, any, lo), but it doesn't capture any network-share traffic.

Wireshark *does* capture http traffic from Firefox in both Ubuntu and under Windows in VMware, but not local traffic between the two.

Any ideas?

Peter.

---

