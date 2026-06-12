---
title: "Managing network profiles via Terminal"
date: 2013-10-28
forum: Networking &amp; Wireless
---

### Post by rafiqcombrinck on 2013-10-28
Hi All

As the topic says, is there a way of doing this?

I have multiple Eth0 profiles that I use on a daily bases and it would be nice to be able to switch between them using the terminal.

Thanks.

---

### Post by ian-weisser on 2013-10-28
See the 'mapping' section of man interfaces.

Some examples are at /usr/share/doc/ifupdown/examples/network-interfaces.gz

---

### Post by rafiqcombrinck on 2013-10-29
I found this to be more than enough for my needs (for now) ... sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0

Thanks :D

---

