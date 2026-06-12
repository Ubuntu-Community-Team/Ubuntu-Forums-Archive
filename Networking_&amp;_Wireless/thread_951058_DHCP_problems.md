---
title: "DHCP problems"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by tabbe2 on 2008-10-17
I got two different Wifi-routers I can connect to. One with WPA encryption and one open. The open one, I can connect to, but internet doesn't work.
The WPA-router I can connect to 25% of the times I try, but the internet doesn't work.

When I check /var/log/messages I get this:
Oct 17 09:33:35 tabbe-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason

Using Ndiswrapper (before, I never succeeded to connect), my wificard is Linksys Wireless-G PCI Adapter WMP54G.

---

### Post by superprash2003 on 2008-10-18
does it work well with static ip?

---

### Post by tabbe2 on 2008-10-20
I can't use other than dhcp, it gets wierd with my ISP. 

Tried so many things now, getting angry.

---

### Post by tabbe2 on 2008-10-26
Still not working.


So now what? Stay with windows?

---

