---
title: "Network Manager not working when changing MTU setting"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by Donnw on 2007-10-23
I need to change my mtu setting to make my broadband work.  I have edited my /etc/network/interfaces file with the following as described in another post

auto eth1
iface eth1 inet dhcp
pre-up /sbin/ifconfig $IFACE mtu 1458

this changes the mtu settings on start  but the network manager no longer seems to work.  There is only a monitor icon visible and no wireless networks visible or a signal strength indication.  This problem applies to my laptop wireless connection.  using the same approach on my desktop computer which is connected directly to router there is no problem connecting to the internet.

can anyone help?

---

