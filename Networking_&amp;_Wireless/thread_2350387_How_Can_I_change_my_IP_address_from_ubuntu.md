---
title: "How Can I change my IP address from ubuntu?"
date: 2017-01-24
forum: Networking &amp; Wireless
---

### Post by ziyapathan01 on 2017-01-24
Hi 

I am using 14.04 LTS and want to change my IP address for some temporary time.


Is there any tool or trick for changing IP address?

---

### Post by TheFu on 2017-01-24
Welcome to the forums.

[https://help.ubuntu.com/stable/ubuntu-help/net.html](https://help.ubuntu.com/stable/ubuntu-help/net.html) exactly how it is done depends on which version of ubuntu you are running, whether the network administrator is using dhcp or not, if there is a router to the internet or not and whether it is a wifi or wired connection. The changed IP needs to *fit* into the network layout. Can't just pick one at random.

For example, it usually is NOT possible to change the WAN IP due to necessary restrictions by the provider. The only way to effectively change it is by using an external VPN, if that is the situation.

If you want to change from 192.168.1.100 to 192.168.1.101 (or something similar), that probably isn't a big deal.

---

### Post by slickymaster on 2017-01-24
*Thread moved to **Networking & Wireless**.*

---

### Post by ajgreeny on 2017-01-24
Which IP do you want to change, the local one from your router or the wide area one from your ISP?

The first is relatively easy to do in a variety of ways, but I don't think you can change the WAN IP yourself, that is not in your control as far as I'm aware, though if you switch off your router completely, removing all power to it for a while you may see that the WAN IP has changed slightly from its previous setting.

---

