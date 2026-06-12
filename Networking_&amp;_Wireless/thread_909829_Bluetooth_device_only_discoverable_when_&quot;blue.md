---
title: "Bluetooth device only discoverable when &quot;bluetooth&quot; service stopped"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by Limnologist on 2008-09-03
I have a bluetooth gps device, and it is only discoverable when the bluetooth service (/etc/init.d/bluetooth) is stopped. No idea why as of right now, but it's really really annoying.

Does anyone know why that might be?

---

### Post by Limnologist on 2008-09-03
Ok, nevermind, the default pin option in /etc/bluetooth/hcid.conf was set to 1234 which was somehow screwing up discovery.

Sigh.

---

