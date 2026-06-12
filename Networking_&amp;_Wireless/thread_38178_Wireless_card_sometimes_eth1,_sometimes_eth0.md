---
title: "Wireless card sometimes eth1, sometimes eth0"
date: 2005-05-30
forum: Networking &amp; Wireless
---

### Post by argotnaut on 2005-05-30
I'm using a D-Link DWL-650 on a Fujitsu P-1032 with a built-in Ethernet port.

Sometimes the wireless card appears as eth0 after booting; sometimes it shows up as eth1. I have to manually activate the device every time I boot (except the ONE time when everything magically worked!).

Also, sometimes the description shows up as "Wireless Device" and sometimes as "Ethernet Device." Either way, it _does_ work when I manually activate it.

I'm not currently using the Ethernet port, so if that's part of the problem, I don't mind deactivating that for the time being somehow.

Can anyone help a relative newbie? Let me know what other info is necessary. Thanks.

---

### Post by Alexander Kirillov on 2005-05-31
[QUOTE=argotnaut]I'm using a D-Link DWL-650 on a Fujitsu P-1032 with a built-in Ethernet port.

Sometimes the wireless card appears as eth0 after booting; sometimes it shows up as eth1. I have to manually activate the device every time I boot (except the ONE time when everything magically worked!).

Also, sometimes the description shows up as "Wireless Device" and sometimes as "Ethernet Device." Either way, it _does_ work when I manually activate it.

I'm not currently using the Ethernet port, so if that's part of the problem, I don't mind deactivating that for the time being somehow.

Can anyone help a relative newbie? Let me know what other info is necessary. Thanks.[/QUOTE]
 My guess is, it is the ethernet card that is creating difficulties: sometimes it gets detected first and assigned device eth0 (thus, wireless becomes eth1); sometimes - for reasons unknown - ethernet  is not configured, so wireless gets to be eth0. Do not know how to fix this, though.

---

