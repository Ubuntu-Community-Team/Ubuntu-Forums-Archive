---
title: "bcm4319 card not working with Network Manager"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by rfdeshon on 2006-08-27
Hi, I had my network card (bcm4319) working with ndiswrapper and Network Manager. I switched to using fwcutter-bcm43xx version and it caused Network Manager to stop working with wireless. It would detect wireless networks and try to connect to them but it would never work. I got rid of the fwcutter files and went back to ndiswrapper. Network Manager still does the same thing (though the wireless card does work through System|Administration|Network). When trying to use Network Manager it prints an error in /var/log/messages saying that dhcdbd could not find a handler or something to that effect. I was wondering if anyone else has had that problem and knows how to fix it as I like using NetworkManager and nm-applet.

from /var/log/messages:
```
Aug 27 01:40:02 localhost kernel: [17186637.980000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 27 01:40:09 localhost gconfd (root-12139): GConf server is not in use, shutting down.
Aug 27 01:40:09 localhost gconfd (root-12139): Exiting
Aug 27 01:40:39 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Aug 27 01:41:48 localhost kernel: [17186744.184000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

