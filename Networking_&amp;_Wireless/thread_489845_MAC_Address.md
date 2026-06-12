---
title: "MAC Address"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by milkolate on 2007-07-01
How do I find out the MAC Address of my WLAN card?

---

### Post by reacocard on 2007-07-01
> **milkolate said:**
> How do I find out the MAC Address of my WLAN card?

```
ifconfig
```

The 'HWaddr' bit is what you're looking for.

I think the network applet also shows it in 'connection information', but only for the currently active connection.

---

