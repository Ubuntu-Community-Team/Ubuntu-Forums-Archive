---
title: "Ubuntu work as a router or DHCP server?"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by Sunnz on 2007-04-14
Here's one modem, 2 computers - one running Ubuntu, one running Windows.

There are no network hub.

And here's my plan:

Modem <-> Ubuntu  <-> Windows.

The modem and Windows machine has only one port, and Ubuntu has 2 network port.

So, I am wondering if Ubuntu can act as a DHCP Server, issuing an IP to the Windows machine?

Can the Windows machine set up to get an IP from Ubuntu's DHCP Server on?

So essentially, turning this:

Modem <-> Ubuntu  <-> Windows.

Into this:

Internet <-> DHCP Server  <-> DHCP Client.

Thanks.

---

### Post by Austin_KW on 2007-04-15
install firestarter the simple GUI to the ubuntu firewall & iptables

sudo apt-get install firestarter

then run firestarter (system->administration->firestarter) and use the wizzard to share your internet connection, selecting enable dhcp on local network

---

