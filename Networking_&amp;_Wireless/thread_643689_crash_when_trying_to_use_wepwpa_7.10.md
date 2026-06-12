---
title: "crash when trying to use wep/wpa 7.10"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by GriZzlEnLS on 2007-12-18
When trying to connect to my wireless (using WEP or WPA) my laptop crashes. I'm using the RealTek 8185L wlan. Wired connection seems to work fine. In vista it works just fine. Anyone please help!!!

---

### Post by GriZzlEnLS on 2007-12-18
Anyone have any ideas?

---

### Post by mous3 on 2007-12-26
Initially I thought it was the wireless card problem. But now it seems like happy connecting to unsecured network, but crash when attempt to connect to secured network. Anyone have any answer to this kinda problem?

---

### Post by kevdog on 2007-12-26
Try connecting from the command line.  Your chipset with linux is a real pain. What driver are you using? See instructions about connecting from the command line in my signature.

---

### Post by mous3 on 2008-01-19
Yo buddy,

I tried typing all those code you showed there through WEP connection.
But once I reach == sudo iwconfig <interface> essid "ESSID_IN_QUOTES" ==

It replies:
Error for wireless request "Set ESSID" (8B1A):
        SET failed on device eth0; Operation not supported.

I type the lshw -C network and got the logical name eth0
but eth0 as interface doesn't work. So I randomly tried wlan0 and it responded!

But same as GUI interface, it crashes and causes the blink again once I reach sudo dhclient wlan0
the terminal listened and send on LPF then send on Socket/Fallback and crashed.

Any idea what went wrong?

---

### Post by kevdog on 2008-01-20
Call me a snob, but I don't usually respond to "Yo buddy".  Sorry I can't help you.

---

### Post by mous3 on 2008-01-20
Sorry bout d buddy thing if you're offended by it. Jz wanna say thanks for the guidance. :) Cheers~

---

