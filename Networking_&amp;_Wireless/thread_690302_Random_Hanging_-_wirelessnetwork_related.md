---
title: "Random Hanging - wireless/network related?"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by Rob V on 2008-02-07
Hi, I'm new to Ubuntu/Linux and am trying my hardest not to uninstall and go back to XP :)


I have a dual boot install with XP.  Boot loader is grub from the Live CD for Ubuntu 7.1 Gutsy.

I have a RTL8185 wireless card, so have had to blacklist the linux drivers and use ndiswrapper with a Win2k driver.  All seems to work as I can connect under WEP - before it just hung as soon as I tried to connect.

Now however I get random hangs - from 7 mins up time to 30-40 mins uptime.

When I return I have run dmesg and the final line is always
```
wlan0: no IPv6 routers present
```

In the system logs I can also see:
```

Feb  7 15:23:36 u-bun-tu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Feb  7 15:23:36 u-bun-tu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Feb  7 15:23:36 u-bun-tu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers

```

Any ideas where to start trying to diagnose the source of the problem?

Anything I can run to check my wireless config is all as it should be (other than the fact that it works until the pc hangs!)

---

