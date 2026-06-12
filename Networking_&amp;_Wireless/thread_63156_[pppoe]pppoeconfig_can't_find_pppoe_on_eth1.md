---
title: "[pppoe]pppoeconfig can't find pppoe on eth1"
date: 2005-09-07
forum: Networking &amp; Wireless
---

### Post by djib on 2005-09-07
Hello,
I have installed a kubuntu recently and I can't get pppoe to work properly.

Let me explain in details :

I installed my kubuntu configuring eth1 (Ethernet) as the default networking interface.
Now I don't have the same connection as before and I need pppoe to get it work (it works ok under Gentoo on the same pc).
When I do pppoeconf, it finds eth1, but cannot find pppoe on it.
Do I have to change my /etc/network/interface config file in any way to get it working ? How do I tell kubuntu to forget about my old Ethernet connection (without pppoe) and get to the new one with pppoe.

Thanks for your help.

---

### Post by adwait on 2005-09-07
PPPoE searches for the access concentrator on the ethernet, so if it is not finding it, it might be possible that there is some problem with the connection itself. If you have a router, maybe you should set it up to work in bridge mode instead of PPPoE/PPPoA.

---

### Post by djib on 2005-09-07
[QUOTE=adwait]PPPoE searches for the access concentrator on the ethernet, so if it is not finding it, it might be possible that there is some problem with the connection itself. If you have a router, maybe you should set it up to work in bridge mode instead of PPPoE/PPPoA.[/QUOTE]
 Hello,
I have just a modem, no router. The connection works fine under Gentoo using PPPoe, so this is why I don't really understand what's happening under Kubuntu.

---

