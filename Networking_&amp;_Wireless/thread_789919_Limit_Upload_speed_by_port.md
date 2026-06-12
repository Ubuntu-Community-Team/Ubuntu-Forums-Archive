---
title: "Limit Upload speed by port"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by t3hi3x on 2008-05-11
So...I have a Linux server that I have an FTP server on. The problem is, anytime someone wants to pull from the FTP, they saturate my upload speed. This causes little packets like DNS requests and other things to not make it out in a timely manner, killing my internet connection.

How do I limit the speed for just ftp (or any other service) for ONLY upload speed using iptables?

---

### Post by nixscripter on 2008-05-11
Unfortunately, I don't know of anything that uses iptables. The most coherent set of instructions I can find uses squid:

[http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html)

Hope this helps...

---

### Post by .rdg on 2008-05-11
Limiting the speed with iptables is not the best idea I guess. I would recommend limiting the network speed with the ftp server configuration - it should be available (in vsftpd it is with anon_max_rate and local_max_rate).

---

