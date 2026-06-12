---
title: "Automatic Connection to Multiple Essids"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by Hase on 2006-10-01
I have tried NetworkManager and don't care for it.  It requires that I manually tell it what network to connect to as well as asks for the keyring password every boot.  Is there no way to write an /etc/network/interfaces script that tells the system to connect to any network, *but if* that network's essid is X the key is Y, if the essid is A the key is B, etc.?
Using Network Monitor, it just changes the entry to whatever it neds to be at the time.  I'm trying to make it as easy and user friendly as possible for non-linux users.
```

iface ath0 inet dhcp
wireless-essid hatbox
wireless-key XXXXXXXXXX

```

---

### Post by NetworkGuy on 2006-10-01
Look into wifi-radar.  It might just do what you are looking for.   I can't get it working for my card so I can't give you a definitive answer.

---

