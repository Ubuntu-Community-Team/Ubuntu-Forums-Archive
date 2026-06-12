---
title: "My weird wireless driver thinks my Ubuntu is a Redhat"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by natirips on 2008-02-21
I've found this line in /var/log/messages
```
Feb 21 09:54:44 natirips-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
```I'm using Ubuntu 7.10 Gutsy Gibbon (64-bit) solely, the driver is ndiswrapper with windows 64-bit driver from the disc that came with my computer (Acer Aspire 5520G, wlan card is Atheros AR5006EG 802.11 b/g). The card used to work from time to time, but for the last few days didn't work at all (I have to use wired connection now). I even opened console to see this "/com/redhat/dhcp/wlan0", but there is nothing like "/com" in my root directory ("/"). :( Any ideas appriciated.

---

### Post by Jussi Kukkonen on 2008-02-21
/com/redhat/dhcp/wlan0 is a D-Bus path not a filesystem path -- the "/com/redhat" part is basically just a namespace to prevent accidentally using same names in multiple places. So that in itself is not a problem.

---

### Post by natirips on 2008-02-21
> **Jussi Kukkonen said:**
> /com/redhat/dhcp/wlan0 is a D-Bus path not a filesystem path -- the "/com/redhat" part is basically just a namespace to prevent accidentally using same names in multiple places. So that in itself is not a problem.I see...

---

