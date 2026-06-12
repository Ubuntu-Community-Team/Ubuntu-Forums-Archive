---
title: "Wired and Wireless simultaneously"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by alanfolsom on 2014-05-06
I am probably missing something obvious here, sorry.

I have a recent Acer desktop running Ubuntu 12.10.  It is connected via wire to our network, and is configured to have a static IP address (192.168.0.25).  I usually remote desktop to it from another computer.  

Without disturbing that wired connection, I would like to enable the wireless so I can use Wireshark to troubleshoot some Wifi development we are doing.  Is this possible?

ifconfig shows only the eth0 connection and local, no wlan.  Network tools shows both the eth0 and the wireless connection, but the wlan is listed as inactive.  If I go into the Network utility and try to enable the wlan, I immediately lose connection over wired interface.

How do I configure both ports to be active if I can?

Thanks

---

### Post by lukeiamyourfather on 2014-05-06
Both can be active but it makes the network connection a little more complicated. The default behavior is to have only one active at a time because otherwise you'd have to setup default paths for different hosts and such which Ubuntu has no way of figuring that part out automatically.

---

