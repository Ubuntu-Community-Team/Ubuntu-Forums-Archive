---
title: "Quick Question on TCP and HTTP/HTTPS/Squid"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by Elif Tymes on 2007-03-13
Is there a way that I can write a kernel extension that monitors tcp traffic on specific protocols, I.E. all traffic through http/https would get logged.

Alternatively, is there a way I can push all http traffic through a squid server on a local machine?

I.E. all http traffic goes through localhost:8080? As opposed to an external proxy server?

---

### Post by Frosty Cold Drink on 2007-03-13
For monitoring traffic, a kernel extension is overkill. All you need to do is set up tcpdump or some other packet sniffing program to monitor and dump data. If you do this, you are going to want to use some intermediaries perhaps, since running packets sniffers as root unattented has been known to be risky. Just make sure you do *not* put the interface into promiscuous mode, as its not necessary.

If you want to see the content of the HTTPS streams, well, then you would have to fudge around a bit.

For forcing through Squid, what you are thinking of is a transparent proxy/bridge. It works by setting up a proxy server (like Squid) on a box with 2 NICs. The host bridges connections from one NIC to the other, but passes connections through the proxy. When done correctly, no one needs to know about the proxy, and no configuration of clients is necessary! You just sit the sucker somewhere.

This tutorial should get you started: [http://freshmeat.net/articles/view/1433/](http://freshmeat.net/articles/view/1433/)

---

