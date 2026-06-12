---
title: "Bridging"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by bigbadbrad on 2008-11-20
Hey everyone. My question is can I bridge two connection in ubuntu? I have a xbox 360 in my room but the router I have for it can't pick up our wlan but my laptop can. I just want to bridge my wlan and my lan so I can play xbox live unti l one of oure tvs gets fixed.

---

### Post by bigbadbrad on 2008-11-20
Anyone?

---

### Post by adaptr on 2008-11-20
Strictly speaking, this is not "bridging" as it is known in Linux/Unix.
You probably want one device to bridge two networks, but that is not the same thing.
Simply enable routing on the device by running
> echo "1" > /proc/sys/net/ipv4/ipforward
and then add routes to the other side of the device on all connected devices you wish to route.

---

### Post by bigbadbrad on 2008-11-20
Ok I think I understand, I'll give it a try.

> bash: /proc/sys/net/ipv4/ipforward: No such file or directory


This is what I get.

---

### Post by adaptr on 2008-11-20
> **bigbadbrad said:**
> Ok I think I understand, I'll give it a try.
This is what I get.
Sorry, that should have been
```
echo "1" > /proc/sys/net/ipv4/ip_forward
```

You might want to google for "linux routing tutorial" or something along those lines.

[www.tldp.org ]("http://www.tldp.org")has a few good examples.

---

### Post by bigbadbrad on 2008-11-20
Thanks again, I flash my router with DD-WRT and thats giving me a problem. I'll try this in the morning.

---

