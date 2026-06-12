---
title: "Disable WiFi interface on boot 18.04"
date: 2018-07-22
forum: Networking &amp; Wireless
---

### Post by kev0153 on 2018-07-22
I have a 18.04 headless server that I’d like to disable the WiFi interface on boot.  Using ifconfig wlp2s0 down will take it down but I’d like to disable on every boot.  Researching it a bit shows I need to use netplan but can find not references on the exact netplan structure.

Thanks for any help

---

### Post by praseodym on 2018-07-22
Why not blacklisting the driver?

---

### Post by chili555 on 2018-07-22
> **kev0153 said:**
> I have a 18.04 headless server that I’d like to disable the WiFi interface on boot.  Using ifconfig wlp2s0 down will take it down but I’d like to disable on every boot.  Researching it a bit shows I need to use netplan but can find not references on the exact netplan structure.

Thanks for any helpWhat does your netplan file look like now?```
cat /etc/netplan/*.yaml
```

---

### Post by kev0153 on 2018-07-23
> **praseodym said:**
> Why not blacklisting the driver?

This is what I ended up doing.  Thanks for the tip.

---

