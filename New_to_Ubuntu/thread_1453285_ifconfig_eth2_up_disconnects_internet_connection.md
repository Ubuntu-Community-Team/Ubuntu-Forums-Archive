---
title: "ifconfig eth2 up disconnects internet connection"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by schoel on 2010-04-13
Hello,

I am using two network cards (one in a USB-dongle) and whenever I bring the USB network interface up, all programs stop having internet connection. My internet connection is on the other card.

How can I prevent this from happening?

Best regards,
Schoel

---

### Post by schoel on 2010-04-13
Turned out I had two default gateways, both my internet connection gateway and the lan gateway were set as default. I removed the one to the LAN and it worked. How can I make this permanent? So I don't have to redo it whenever I reboot.

---

