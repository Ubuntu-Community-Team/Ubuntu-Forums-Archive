---
title: "Problematic NIS configuration on a laptop"
date: 2014-02-20
forum: Networking &amp; Wireless
---

### Post by noorez on 2014-02-20
Ubuntu 13.10

Here is my situation:

My work laptop uses a NIS configuration. While directly connected directly to the work network, NIS is able to bind to the server without issue (unless of course the server is down...). 

However, while away from work, I cannot directly connect to NIS. My laptop takes forever to boot up (if I switch to tty2 I can stop the autofs and ypbind service). ypbind will only work when I attach my laptop to the VPN making those NIS servers accessible.

After some googling, I tried setting YPBIND_MAXWAIT in /etc/environment but this did not appear to take effect. Is there anything else I can do (such as /etc/nsswitch.conf) to prevent NIS from waiting forever to bind?

---

