---
title: "[SOLVED] Firestarter - The device eth1 is not ready"
date: 2007-12-08
forum: Networking &amp; Wireless
---

### Post by Blinkiz on 2007-12-08
Have removed my eth1 network card from my computer. Now Firestarter says is can't start the firewall.
```

Failed to start firewall
The device eth1 is not ready.
Please check your network device settings and make sure internet connection is active.

```
I still have eth0 network card. Thats the one it should be firewalling. I can't find anything about eth1 in the system after the removal of the card. Reinstalling Firestarter didn't work.

ifconfig -a returns my "eth0" card and "lo".
Please advice

---

### Post by edm1 on 2007-12-08
Are there any instances of eth1 in '/etc/firestarter/configuration'?

---

### Post by Blinkiz on 2007-12-08
Yes, it did exist.
I removed the line about external interface (eth1) and now Firestarter can start the firewall.


Running the wizard within Firestarter will add eth1 interface again for some reason. Why?

---

