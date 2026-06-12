---
title: "How do I disable Firewall?"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by Haz13r on 2007-07-07
I noticed recently that my computer has a Firewall.  On Azureus sometimes the files get messed up or just dont download and stop at a certain point.  How do i Disable this firewall?

---

### Post by hanzomon4 on 2007-07-07
Unless you blocked something, and you would know if you did, iptables(linux firewall) shouldn't be giving you crap. Do you connect to the internet through a router? It maybe that you need to forward some ports on that end.

---

### Post by Haz13r on 2007-07-07
Yea, i use a Lynksys Router.  Im sure i didnt block Azureus, and how do i forward ports?

---

### Post by ugm6hr on 2007-07-07
> **Haz13r said:**
> Yea, i use a Lynksys Router.  Im sure i didnt block Azureus, and how do i forward ports?
Look for your router here:
[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

Obviously, you need to identify the correct port (which will be listed in the Preferences of Azureus).

Personally, I found Azureus behaved in unexpected ways, and switched to KTorrent (which has a working UPnP plugin).

It is worth checking that iptables isn't blocking anything too - since I've been led to believe that the default is that all incoming traffic is blocked.  Install Firestarter (from Synaptic), then run Azureus / KTorrent and look for "events" with Firestarter running.

EDIT:
To run Firestarter, select it in the System menu after installing it. It shrinks to the system panel when closed, but changes icon at any event.

---

