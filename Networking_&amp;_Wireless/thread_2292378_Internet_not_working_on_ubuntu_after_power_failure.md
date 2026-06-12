---
title: "Internet not working on ubuntu after power failure"
date: 2015-08-27
forum: Networking &amp; Wireless
---

### Post by Excuse_Me on 2015-08-27
After a power failure in my home I started up my computers again. Internet is working fine on my mac and windows PC but my server running ubuntu 14.04 refuse to connect no matter how many time I restart or reset the router. I also have one more computer running mint and it has the same problem as the Ubuntu computer - no internet! Has been working fine for months but after the power failure they refuse to connect to internet, anyone have an idea what could be wrong??

---

### Post by TheFu on 2015-08-27
Since you say "server" I'll ask server specific questions.

Please post:
/etc/network/interfaces
ifconfig
route
sudo lshw -C network

If you are using a desktop, I cannot help. Networking there is completely different and I disable network manager for a number of personal reasons.

Of course, a power spike can fuse connections in wires, cables, switch ports.  I've seen this.  Swap the ports around on the router, switches, cables and test again to exclude any hardware that you can.

---

