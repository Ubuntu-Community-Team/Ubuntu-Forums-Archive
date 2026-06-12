---
title: "network manager (nm-applet) problem"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by Entheogen on 2008-10-03
nm-applet can scan my wlan networks but when i try to connect to my home network (with wep key) it cannot get ip addresses? i tried typing wep 128 bit and 64 bit keys but it doesnt work. i can only connect with wifi-radar and key value is "s:key" ( notice s: ). i tried typing key with s: prefix in nm-applet but it doesnt work. what do you think is the problem?
i use atheros AR242x card with ndiswrapper drivers. 
(i tried madwifi, same thing happens.. actually with madwifi i cannot connect even with wifi-radar).

---

### Post by Entheogen on 2008-10-04
anyone?

---

### Post by iponeverything on 2008-10-04
Instead of using nm-manager try using the interface file

/etc/network/interface

make sure that wireless-tools are installed:

apt-get wireless-tools

then just add the stanza's the way would for a wired interface
-- man interfaces
see the additional stanza's available for encryption 
man iwconfig and
man iwpriv

google'ing around for iwpriv and wep might be a help for you as well

---

### Post by itsjareds on 2008-10-04
I would install Wicd instead.

```
sudo apt-get install wicd
```

I had problems getting my Netgear WPN111 working and it only works with Wicd -- wicd is much less controlling than nm-applet so it doesn't mess anything up.

---

### Post by Entheogen on 2008-10-04
works fine when upgraded to intrepid...

---

