---
title: "network-manager drops wireless"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by dcherryholmes on 2006-11-27
My nm-applet will display available wireless networks.  The wireless interface is up and I can connect via ifconfig up, iwconfig, and dhclient.  Network-manager can connect to the wired network just fine.  Strangely, there is nothing in /etc/network/interfaces (my first thought as to the problem).

The only thing in the logs that looks remotely related is this error, but I've had it for a long, long time:

 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

---

### Post by dcherryholmes on 2006-12-01
Nailed it.  It was a problem with wpa_supplicant.  I uninstalled wpasupplicant, which also uninstalled network-manager and.... I think this is the important bit.... dhcdbd.  Then I reinstalled network-manager, which also pulled back in wpasupplicant but not dhcdbd.  Not sure how I got that package installed in the first place, but it looks like it was the problem.

---

