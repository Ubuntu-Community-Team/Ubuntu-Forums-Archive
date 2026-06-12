---
title: "Default adapter for Internet connection"
date: 2014-09-02
forum: Networking &amp; Wireless
---

### Post by Denco1 on 2014-09-02
I would like to ask, how can I solve my situation. We use this laptop with (X)Ubuntu 14.04 at work. At certain situations, we need to be connected to the Internet through 3G USB Modem and at the same time, connected through ethernet (without the Internet) to access devices. The problem is, that system is looking for the Internet on ethernet. 3G USB modem works, Internet works, but when I plug in ethernet, 3G Internet stops working.


Is there anyway to tell Ubuntu to look for the Internet on this 3G USB modem when it's connected and also let me work with other devices connected through ethernet at the same time?

Thanks

---

### Post by varunendra on 2014-09-05
If you never want Ethernet to be used for internet, only for accessing local devices, then -

In Network Manager > "Edit Connections" > "Wired" tab > double-click your Ethernet connection to edit it > "IPv4" tab (if that is what you use) > "Routes" button > check both checkboxes that say "Ignore automatically obtained routes" and "Use this connection only for resources on its network"


If you only occasionally want what you described -
```
sudo route del default
```
before connecting your 3G modem, or if it is already connected, then in addition to above you may have to -
```
sudo route add default gw <gateway of your 3G modem>
```
You can see the gateway of your modem in "Network Manager menu > Connection Information", or the output of "nm-tool" command.

---

