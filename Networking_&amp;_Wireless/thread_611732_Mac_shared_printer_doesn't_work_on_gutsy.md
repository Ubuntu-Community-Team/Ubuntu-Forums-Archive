---
title: "Mac shared printer doesn't work on gutsy"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by clconway on 2007-11-13
I have a shared printer connected to a Mac by USB. Under feisty, I was able to see it and print to it: it showed up as a network printer automatically using zeroconf. Since I upgraded to gutsy, I can't see it anymore. I *can* see all kinds of other zeroconf services (e.g., iTunes sharing, SSH capability) using the Service Discovery Applet. I'm not even able to access it directly by using the hostname or IP address of the computer it is connected to. The *only* thing that has changed, so far as I can tell, is the upgrade to gutsy. Did the zeroconf sub-system change? Do I need to add/remove some packages to set things right?

---

### Post by clconway on 2007-11-17
This problem was caused by Firestarter. This hadn't occurred to me, because I had a working avahi/zeroconf installation on feisty (including the right Firestarter settings), but following the firewall configuration settings on this page fixed everything:

[https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)

---

