---
title: "lUbuntu keeps asking for wireless password (12.04)"
date: 2013-11-30
forum: Networking &amp; Wireless
---

### Post by mr_si on 2013-11-30
As per the title .... when my laptop comes out of hibernation, when it loses the signal... it's very annoying.

I'm on 12.04. It was KUbuntu until last week when I installed the L desktop (K worked fine, if rather slowly on my old machine)

Thanks

---

### Post by ipet on 2013-11-30
I had that problem few times but I am not sure why it happens.
I guess that problem is with wifi drivers.

What I was doing to fix this bring down the wlan0(or what interface it is) and then up again.

```
ifconfig wlan0 down
ifconfig wlan0 up
```

---

### Post by Bucky Ball on 2013-11-30
*Thread moved to **Networking & Wireless**.*

---

### Post by julungpujut on 2013-12-01
problem is your wi-fi signal... [COLOR=#000000]I had that problem if my wi-fi signal only one bar, and if signal is 2 bar my wireless autoconnect without problem...[/COLOR]

---

### Post by Bucky Ball on 2013-12-02
> **julungpujut said:**
> problem is your wi-fi signal... 

Yes, there isn't one after hibernation so this is obvious. The problem is actually that the connection doesn't exist when the computer comes out of hibernation. OP says nothing about weak signal. Appears the wireless is working fine before hibernation.

---

### Post by mr_si on 2014-01-20
This seems to be OK now (via some update???). I did do some research and found a thread (don't ask me for a link) that suggested it was to do with my security settings, seeing as how I have automatic logon and no password lock on wake from hibernate - ie it deliberately prevented me from accessing network resources until I had provided some credentials. Doesn't quite explain how it's now not doing that though?

---

