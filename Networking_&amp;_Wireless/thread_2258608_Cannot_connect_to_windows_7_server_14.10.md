---
title: "Cannot connect to windows 7 server 14.10"
date: 2014-12-29
forum: Networking &amp; Wireless
---

### Post by marti3 on 2014-12-29
Wired connection, fresh install, no other S/W added, sometimes works, but lately not at all. I get as far as workgroup then it  times out. Is there some way to make this more reliable? Do I need to install 3rd party net S/W?

---

### Post by TheFu on 2014-12-29
Can machine-A ping machine-B and vice versa?
Fix that first. Normally setting both up with static IPs and modifying the /etc/hosts file is desired.  

[http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) has another way to handle this ip-to-hostname resolution with DHCP. That is better for portable devices and may be good enough for "servers" - though I much, much, much prefer for servers to have static IPs.

---

