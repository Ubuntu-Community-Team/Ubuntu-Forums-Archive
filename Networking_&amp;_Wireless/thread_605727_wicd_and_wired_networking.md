---
title: "wicd and wired networking"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by dcherryholmes on 2007-11-07
I switched over to wicd a few days ago, due to problems with network-manager.  It is working pretty well, but I can not get it to pick up an IP address off my wired network.  If I ifconfig down the wireless interface and dhclient the wired interface everything works fine, so I think it's a problem with wicd.  Any suggestions?

---

### Post by imdano on 2007-11-07
Is the wired interface name in wicd preferences correct?  What version of wicd are you using?

---

### Post by dcherryholmes on 2007-11-09
Wired interface is eth0, which is correct.  I'm using version 1.3.1

---

### Post by Seisen on 2007-11-09
Post what comes up in ```
/etc/network/interfaces
```.

---

