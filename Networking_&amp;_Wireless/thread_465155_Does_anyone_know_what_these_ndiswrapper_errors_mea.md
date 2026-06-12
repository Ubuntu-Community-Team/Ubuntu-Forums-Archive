---
title: "Does anyone know what these ndiswrapper errors mean?"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by jzerocsk on 2007-06-05
I think I'm very close to getting the wireless card working on my laptop.  When I try to connect, here is the errors in the log file:
```
Jun  5 13:21:20 peasantry-lx dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun  5 13:21:20 peasantry-lx kernel: [  569.840000] ndiswrapper (iw_set_ap_address:629): setting AP mac address failed (C00000BB)
Jun  5 13:22:20 peasantry-lx kernel: [  629.896000] ndiswrapper (iw_set_ap_address:629): setting AP mac address failed (C00000BB)
Jun  5 13:23:20 peasantry-lx kernel: [  689.188000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Does anyone know what this means?

---

### Post by jzerocsk on 2007-06-05
Any suggestions before I toss linux back into the "Not ready for prime time" bin for another couple of years?

---

### Post by kevdog on 2007-06-05
Are you using ubuntu or red hat??

---

### Post by jzerocsk on 2007-06-06
Ubuntu Feisty Fawn.  

I tried searching on variations of that first error and didn't find a whole lot.  I think when the dhcdbd package was ported to debian/ubuntu the maintainer must have forgotten to update something.  There is a bug report about it a dhcdbd but the person that reported it claims no ill effects on his (wired) connection.  My wired connection works fine.  I may try upgrading dhcdbd to the latest version, but in my gut I don't think it's the cause of the problem.

---

### Post by jzerocsk on 2007-06-07
One last bump before I toss it in the bin.
Thanks!

---

