---
title: "what is this warning?"
date: 2023-05-09
forum: Networking &amp; Wireless
---

### Post by bjlockie on 2023-05-09
This is in my dmesg.
Everything works fine but what does it mean?

warning: `kdeconnectd' uses wireless extensions which will stop working for Wi-Fi 7 hardware; use nl80211

---

### Post by chili555 on 2023-05-09
It appears to be a bug that's being worked on. 

Possibly helpful: [https://lore.kernel.org/netdev/20230224135933.94104aeda1a0.Ie771c6a66d7d6c3cf67da5f3b0c66cea66fd514c@changeid/T/](https://lore.kernel.org/netdev/20230224135933.94104aeda1a0.Ie771c6a66d7d6c3cf67da5f3b0c66cea66fd514c@changeid/T/)

I suspect it will be fixed long before either of us has a WiFi 7 router *and* a wireless device that is also WiFi 7 capable. I believe you may safely ignore the message.

[https://www.tp-link.com/us/wifi7/](https://www.tp-link.com/us/wifi7/)

---

