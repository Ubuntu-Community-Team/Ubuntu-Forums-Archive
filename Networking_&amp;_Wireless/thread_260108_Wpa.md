---
title: "Wpa"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by Almor on 2006-09-18
I can connect to a network with WEP & hidden SSID fine using System > Administration > Networking and entering the information.  I can also connect fine using wired.

I read the HOW TO on getting WPA to work at: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29)
and followed the directions.  I installed network-manager-gnome and rebooted and network manager loaded fine.  But when I click it, it tells me "No Network Devices Have Been Found".  I know the device works fine because I can connect using WEP so how can I get network manager to detect my wireless card or is there a different wireless manager I can try.

If it matters my laptop is a Toshiba A100-SK4 with a built in Intel wireless card(I would have to boot back into windows to give you the exact model).

Thanks.

---

### Post by sjieke on 2006-09-19
Network manager ignores the devices that are configured in /etc/network/interfaces. To let network manager manage them you should comment them out. The /etc/network/interfaces file should look similar like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# auto eth1

# iface eth1 inet dhcp

```

More info can also be found on the wiki: [https://help.ubuntu.com/community/WifiDocs/NetworkManager]("https://help.ubuntu.com/community/WifiDocs/NetworkManager")

---

