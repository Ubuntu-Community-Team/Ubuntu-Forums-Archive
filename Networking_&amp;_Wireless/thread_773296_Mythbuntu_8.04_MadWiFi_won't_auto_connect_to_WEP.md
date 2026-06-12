---
title: "Mythbuntu 8.04 MadWiFi won't auto connect to WEP"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by thoraxe on 2008-04-28
So, I can't seem to get my WDA-2320 to auto connect when the system boots up.  I am able to manually diddle around with the wireless settings using iwconfig/iwprivs to get it to connect.  If I reboot the machine, no dice.

Here's the interfaces file:

```
iface ath0 inet dhcp
wireless-essid FESTIVENET
wireless-key mykey open
```

If I manually iwconfig/iwprivs using the key and authmode2 and specify my AP and ESSID and everything it will connect and I can successfully run dhclient.  Using the built-in network settings manager with XFCE (remember, MythBuntu) the wireless card will not connect either in ascii or hex mode.

I'm open to suggestions :(

---

