---
title: "Help on Wireless-Compay V2000-Broadcom-ndiswrapper"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by inatarun on 2007-06-01
I have installed ndiswrapper and driver 
the wireless light is on and i am able to see all the networks but iam unable to connect to them..

this is the log message i get on  tail /var/log/messages

Jun  1 00:47:19 tarun-laptop gconfd (root-5543): GConf server is not in use, shutting down.
Jun  1 00:47:19 tarun-laptop gconfd (root-5543): Exiting
Jun  1 00:48:24 tarun-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun  1 00:48:24 tarun-laptop kernel: [  327.425017] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun  1 00:49:06 tarun-laptop kernel: [  347.397826] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun  1 00:49:06 tarun-laptop kernel: [  347.398489] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun  1 00:49:24 tarun-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun  1 00:49:28 tarun-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun  1 00:49:28 tarun-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun  1 00:49:28 tarun-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers


Please i need some help..

Tarun

---

