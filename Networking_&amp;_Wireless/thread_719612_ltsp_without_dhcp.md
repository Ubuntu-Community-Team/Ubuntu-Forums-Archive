---
title: "ltsp without dhcp?"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by stephan0h on 2008-03-09
Hi Group,

I'm just wondering if it's possible to set up an ltsp-server without a dhcp-server. What if my ltsp-server has a fixed IP as well as my ltsp-client? (for a start I'll have only one client) The client could have knowledge of the server's IP so there should be no necessity for a dhcp-server running. Am I correct in this assumption? And if yes: how would I go about to setup this?

Thanks,
Stephan

---

### Post by lloyd_b on 2008-03-09
> **stephan0h said:**
> Hi Group,

I'm just wondering if it's possible to set up an ltsp-server without a dhcp-server. What if my ltsp-server has a fixed IP as well as my ltsp-client? (for a start I'll have only one client) The client could have knowledge of the server's IP so there should be no necessity for a dhcp-server running. Am I correct in this assumption? And if yes: how would I go about to setup this?

Thanks,
Stephan

Any linux machine can be configured with a "static" (fixed) IP address.

To set it up during the installation, just "cancel" when it tries to set up the network via DHCP, and then select "Manual Configuration", and provide the necessary info (IP address, Netmask, Gateway).

To change an existing machine to a static IP, edit the file "/etc/network/interfaces", and change the lines (assuming interface "eth0"):
```
auto eth0
iface eth0 inet dhcp
```
to
```
auto eth0
iface eth0 inet static
     address xxx.xxx.xxx.xxx
     netmask xxx.xxx.xxx.xxx
     gateway xxx.xxx.xxx.xxx
```
(putting in the real addresses for the x's)

and then in a terminal window:
```
sudo /etc/init.d/networking restart
```
(rebooting will also work, but it isn't really necessary).

Lloyd B.

---

