---
title: "Ethernet cable not working on 14.04 fresh install"
date: 2016-07-14
forum: Networking &amp; Wireless
---

### Post by trevahkt on 2016-07-14
I feel like this subject has been hashed and rehashed a million times on these forums so let me apologize. I tried delving into some other threads but couldn't get anything solid.

So basically my Ethernet seems to be undetected by my new Ubuntu 14.04.

---

### Post by oldrocker99 on 2016-07-15
Please post the output of```

lspci
``` so we can see what your hardware is.

Your problem **could** be that you're using 14.04, which has an older kernel, 3.19. 16.04 uses 4.4.0, which may well have the drivers for your mobo's Ethernet hardware.

---

### Post by DuckHook on 2016-07-15
Welcome to the forums, trevahkt

*Thread moved to **Networking & Wireless** as forum more suited to your issue.*

---

