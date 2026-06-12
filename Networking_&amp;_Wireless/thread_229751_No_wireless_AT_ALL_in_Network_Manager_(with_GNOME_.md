---
title: "No wireless AT ALL in Network Manager (with GNOME Front End)"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by cheway on 2006-08-04
I posted this in the beginners section, but realised I should have posted it here first (sorry).


I've installed network-manager (with network-manager-gnome) as I want to be able to switch between various wireless networks with ease, and also to utilise WPA encryption.

It's all installed, with the GNOME front end, and it's in the notification area - however, it cannot see any wireless networks whatsoever, even with wireless encryption disabled. (It seems to do it's stuff fine when I plug an ethernet cable in though).

Any help would be appreciated, the lack of WPA has been doing my melon in for days now.

---

### Post by sawjew on 2006-08-05
I had the same problem and fixed it by opening my /etc/network/interfaces file and commenting out all network connections there.

All that should be in /etc/network/interfaces when using network manager is;
```
auto lo
iface lo inet loopback
```

Network manager won't recognise anything that is listed in the interfaces file.

try that

---

### Post by cheway on 2006-08-05
I tried that, and it was just the ticket - I can't thank you enough, that's been doing my head in for days.

---

### Post by blegs38552 on 2008-04-13
Tried this. No interfaces are listed. Only the usual first 2 lines.

---

