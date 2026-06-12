---
title: "Bcm43xx Problems with Restricted Drivers Installation"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by shhmiggly on 2008-04-15
Here is the relevant /var/log/messages output:

Apr 15 10:24:48 lappy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Apr 15 10:25:56 lappy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Apr 15 10:28:48 lappy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Apr 15 10:30:07 lappy kernel: [  668.176000] NET: Registered protocol family 10
Apr 15 10:30:07 lappy kernel: [  668.180000] lo: Disabled Privacy Extensions
Apr 15 10:30:07 lappy kernel: [  668.180000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 15 10:30:07 lappy kernel: [  668.180000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 15 10:30:14 lappy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Apr 15 10:30:15 lappy kernel: [  675.944000] ADDRCONF(NETDEV_UP): eth1: link is not ready
/eth1

Basically ADDRCONF(NETDEV_UP):eth1 is the problem. I think there is a naming conflict somewhere that is causing the problem, but I haven't been able to find it.

Any Help is Appreciated.

---

### Post by shhmiggly on 2008-04-16
I know wireless is a big problem with Linux, but can this be solved?

---

### Post by uberlube on 2008-04-16
Try the howto in my sig and let me know if it helps :)

---

