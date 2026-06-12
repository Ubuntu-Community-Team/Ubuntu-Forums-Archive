---
title: "Wireless works in Dapper, but not in fresh install of Edgy"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by cookfromfrozen on 2006-11-22
Hi

Dapper detects my wireless card (a PCMCIA Atheros chipset) during the installation (as it scans for access points) and works fine after installation and shows up as ath0.

However, during a fresh install of Edgy (not an upgrade), it detects the card during installation and offers to scan for wireless points, but after installation, it disappears and doesn't appear in the Networking applet.

I've tried removing and reinserting the card, but Edgy just forgets about the card after installation, even though it detected it during setup.

Is there any way to somehow reinstall the madwifi drivers or somehow get it to find the card again?

I checked /etc/iftab, and it has a line for the card there like this:
```
ath0 mac XX:XX:XX:XX:XX:XX arp 1
```

Any ideas? :(

---

### Post by FrodoB on 2006-11-22
Did you use the alternate CD? If so see:

[http://www.ubuntuforums.org/showthread.php?t=304788](http://www.ubuntuforums.org/showthread.php?t=304788)

Otherwise let us know.

---

### Post by cookfromfrozen on 2006-11-22
Yes I'm using the alternate CD, thanks a lot :)

---

