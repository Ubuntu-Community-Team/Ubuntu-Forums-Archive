---
title: "Wireless connection problems with RT2500"
date: 2005-04-21
forum: Networking &amp; Wireless
---

### Post by topynate on 2005-04-21
I have a rather strange problem with my wireless connection (rt2500):

While it very occasionally successfully connects to the internet, the majority of attempts fail. iwconfig shows that I can see the access point, but dhclient does not work - I get no responses, so can't get an IP address. This is with no MAC filtering, using WEP - although the problem is identical without WEP.

---

### Post by jdodson on 2005-04-21
[QUOTE=topynate]I have a rather strange problem with my wireless connection (rt2500):

While it very occasionally successfully connects to the internet, the majority of attempts fail. iwconfig shows that I can see the access point, but dhclient does not work - I get no responses, so can't get an IP address. This is with no MAC filtering, using WEP - although the problem is identical without WEP.[/QUOTE]

do you use ndiswrapper?

---

### Post by topynate on 2005-04-21
I'm using the native rt2500 driver, compiled for amd-64.

---

### Post by Yaniv on 2005-04-24
There's a guide for rt2500 on Ubuntu, including wpa support here: [http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo)

It's tested on hoary, but my guess is that it's just as good for warty

---

