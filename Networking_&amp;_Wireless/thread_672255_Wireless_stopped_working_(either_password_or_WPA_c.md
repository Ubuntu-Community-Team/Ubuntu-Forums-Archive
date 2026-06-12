---
title: "Wireless stopped working (either password or WPA change is the reason)"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by SnowPunk98 on 2008-01-19
Using gutsy, fully updated, everything had been working. I changed my password and I think this messed up Gnome Keyring since the passwords did not match to input the WPA key.

Also during this time I was making changes to my WPA configuration on my router. At this point my router is configured exactly the same as it was before (same SSID, WPA key, etc) so this should not be an issue.

When I log in, I can see different wireless networks but when I try and connect to mine it looks like it tries just for maybe 1 second then goes back to the 2 computer icon with a red x in it.

Below are two error messages I pulled out of the system log, not sure what they mean yet.

> dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason

kernel: [  208.428000] ADDRCONF(NETDEV_UP): eth1: link is not ready

---

### Post by SnowPunk98 on 2008-01-22
bump

---

### Post by SnowPunk98 on 2008-01-23
I changed my password back to what it was, restored a copy of my keyring file, before anything was changed and things are back and working.

I would still like to change my password though, how do I go about doing this without breaking my wireless?

---

