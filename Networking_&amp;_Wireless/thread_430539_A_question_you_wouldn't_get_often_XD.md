---
title: "A question you wouldn't get often XD"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by Mb0742 on 2007-05-02
I have my wireless set up nicely in Ubuntu 7.04, and I have my Xbox plugged into my Ethernet jack; now is there anyway to bridge the connections, so Live can use my wireless?

---

### Post by lassegs on 2007-05-02
We did something like this with a laptop and a router once, the laptop was connected to the internet through WLAN, and we wanted to bridge the connection to the router. 

It went ok, we sat up a dhcp server on the laptop. Look into dhcpd.

---

### Post by Mb0742 on 2007-06-05
So I finally got around to it.

I am in dhcpd and now I am in the firewall options so how do I reroute Eth0 and my wireless? (Like how do I create the rule?

---

