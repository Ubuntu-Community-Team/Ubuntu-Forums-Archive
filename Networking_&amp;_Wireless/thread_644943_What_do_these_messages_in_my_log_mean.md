---
title: "What do these messages in my log mean?"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by jamesey on 2007-12-19
Occasionally my network sputters and acts really weird. I finally decided to log it, but I have no idea what these messages mean. Over this particular 3 minute period, my connection dropped, reconnected for a little bit, then dropped some more. 

I have Gutsy, and never experienced anything like this on Feisty. My Gutsy install is fresh. I connect via roaming mode. jamesey is my computers name

```

Dec 18 19:01:23 jamesey kernel: [47416.812000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 18 19:01:24 jamesey kernel: [47417.924000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 18 19:02:25 jamesey dhcdbd: Unrequested down ?:3
Dec 18 19:02:25 jamesey kernel: [47478.964000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 18 19:02:28 jamesey kernel: [47481.388000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 18 19:02:33 jamesey kernel: [47487.044000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 18 19:02:34 jamesey kernel: [47487.712000] wlan0: duplicate address detected!
Dec 18 19:02:34 jamesey kernel: [47487.712000] wlan0: duplicate address detected!
Dec 18 19:02:45 jamesey dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Dec 18 19:02:45 jamesey dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Dec 18 19:02:45 jamesey dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Dec 18 19:02:45 jamesey dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Dec 18 19:02:46 jamesey kernel: [47499.812000] wlan0: duplicate address detected!
Dec 18 19:02:46 jamesey kernel: [47499.812000] wlan0: duplicate address detected!
```

---

### Post by glasswalkerny on 2007-12-19
> ```

Dec 18 19:02:34 jamesey kernel: [47487.712000] wlan0: duplicate address detected!
Dec 18 19:02:34 jamesey kernel: [47487.712000] wlan0: duplicate address detected!
Dec 18 19:02:46 jamesey kernel: [47499.812000] wlan0: duplicate address detected!
Dec 18 19:02:46 jamesey kernel: [47499.812000] wlan0: duplicate address detected!
```

these entries here indicate that a machine with the same IP address that your wireless card was given came online.. this will nock both computers off the network until one or the other shut down.. 
This leads to a few questions...

1 do you have any other computers on your network? 
2 is your wireless router secured? WAP/WPA? is it broadcasting it's ssid?


the fact that your network performance tanks when these errors come up will continue to happen until the offending machine is located/eliminated

---

### Post by jamesey on 2007-12-20
My machine is the only one on the network. I checked the router logs and only my machine is connecting.

---

