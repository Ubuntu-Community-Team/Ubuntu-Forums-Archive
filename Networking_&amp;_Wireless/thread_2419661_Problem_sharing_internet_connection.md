---
title: "Problem sharing internet connection"
date: 2019-05-24
forum: Networking &amp; Wireless
---

### Post by norrin.radd on 2019-05-24
Hi,

I'm trying to share my internet connection (ppp) to some devices. The problem seems to be the lack of DNS. If I type an IP address in a browser, it can reach a website. apps like Instagram and WhatsApp are working fine.

I didn't try to install dnsmaq to avoid conflict with systemd-resolved.

My setup is the following:

Internet <  (ppp0) > Xubuntu 18.04 < (eth1) > Dell PowerConnect 2816 > Wireless router

The configuration on the eth1 interface was made using nm-connection-editor and it is just a static IP (192.168.0.2/24) and the option **Shared to Other Computers** (IPv4 tab).

The wireless router configuration:
IP: 192.168.0.8
Subnet: 255.255.255.0
Gateway: 192.168.0.2
DNS: 192.168.0.2

Any hints?

Thanks.

---

### Post by Tadaen_Sylvermane on 2019-05-24
Don't mean to state the obvious. Why doesn't the internet go straight to the router, then out from there to the devices? Would instantly solve or prevent all kinds of issues. Is what routers are designed to do.

---

### Post by norrin.radd on 2019-06-03
Hi,

Thank you for the suggestion, but I would like to manage the connection with Ubuntu.I am planning to implement some specific routes to my server, firewall rules and some vnstat monitoring.

---

### Post by kurt18947 on 2019-06-03
My initial response was like that of Tadaen_Sylvermane. If you want more capability than you get from a consumer router do you know about the *WRT 3rd party router firmware? Are there are functions that are either included or can be added to accomplish what you wish? I use DD-WRT but haven't implemented any of the advanced functions. OpenWRT seems like it has more options but I'm not knowledgeable enough to have have an informed opinion.

---

