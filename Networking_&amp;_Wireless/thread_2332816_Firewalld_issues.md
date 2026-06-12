---
title: "Firewalld issues"
date: 2016-08-04
forum: Networking &amp; Wireless
---

### Post by justin25012 on 2016-08-04
Hi there,

I'm trying to set some whitelisting on my Firewalld setup.
I have port 22, 53, 10000 and 10010-10100 open on the "public" firewall group which is linked to nic1

The problem is, i want port 22 and 10000 to be accessible by 1 IP and 2 IP ranges
Port 53 must be world wide open.
Port 10010-10100 must be accessible only between system1 and system2. So one accessible by two IP's

Any idea how i can set this up? I'm using IPv6 and IPv4, so an example for both would be perfect if possible.
Running on Ubuntu 16.04 LTS

---

