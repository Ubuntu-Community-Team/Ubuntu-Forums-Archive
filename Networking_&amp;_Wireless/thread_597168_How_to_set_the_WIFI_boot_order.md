---
title: "How to set the WIFI boot order?"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by c0reyf on 2007-10-30
Is there a way you can set it so Ubuntu looks for network A before B somewhere in the configuration. I'm using Gusty, any help is greatly appreciated.

---

### Post by spd106 on 2007-10-30
I'm afraid you can't really set the order very easily. Network Manager will connect to the last network that you connected to, that's currently available. It doesn't always work perfectly due to problems with some drivers.

If you want to set a preference order then you can do this with wpa_supplicant, but that means you will have to edit a text file and you will lose the roaming mode benefits to Network Manager and nm-applet.

---

### Post by c0reyf on 2007-10-30
OK thanks for the information. Cheers:)

---

