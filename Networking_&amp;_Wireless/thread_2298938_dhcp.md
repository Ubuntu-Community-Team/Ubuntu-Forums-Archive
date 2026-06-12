---
title: "dhcp"
date: 2015-10-14
forum: Networking &amp; Wireless
---

### Post by leonard7 on 2015-10-14
Can Ubuntu Server "latest edition" use dhcp to acquire a ip address from a router and can Ubuntu Server use dhcp to issue IP address to client computers?  eth0 is connected to router and eth1 is connected to client computers through a simple switch.

---

### Post by SeijiSensei on 2015-10-14
Yes, and yes, though you'll probably want to use a static IP on eth1. Presumably it will become the default gateway for the clients on the inside network.

Once it's installed, edit /etc/default/isc-dhcp-server to read
```
INTERFACES="eth1"
```
which tells the server to bind to that interface.

---

### Post by leonard7 on 2015-10-14
Thanks for the pointer. I will make note of this step.

---

