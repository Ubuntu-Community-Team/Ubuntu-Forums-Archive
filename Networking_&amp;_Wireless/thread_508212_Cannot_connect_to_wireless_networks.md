---
title: "Cannot connect to wireless networks"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by harjasis on 2007-07-23
Hi,

I cannot see any wireless networks in network manager.
If I enter/ create a wireless network name to which I'm able to connect in windows, it tries to connect to it. i could see a whirlpool like animation on the top-right corner but no success.

Please suggest how to proceed.

My laptop is HP dv5000 series AMD turion64 technology with Broadcom wireless card inside (Broadcom BCM4311).

I don't have any wired connection. The wireless networks I'm trying to connect in ubuntu are unsecured connections.

---

### Post by aliyanage on 2007-07-24
did you already check whether you can see the wirless card interface?
check out by opening a terminal and typing following command:

```
ifconfig
```

you should get all your network interfaces listed with ip addresses. eth1 usually stands for the wireless interface...

regards
aliyanage

---

