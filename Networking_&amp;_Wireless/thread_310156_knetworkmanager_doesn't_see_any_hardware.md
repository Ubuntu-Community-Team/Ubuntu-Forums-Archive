---
title: "knetworkmanager doesn't see any hardware"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by Hrothgar on 2006-11-30
I just installed Edgy on my thinkpad a21m laptop that has an atheros based card configured as ath0. I can enable the card and surf on both wired and wireless but when I installed knetworkmanager it says it can't find any network hardware.

Any Ideas?

---

### Post by Hrothgar on 2006-12-01
I checked to see if the network-manager package installed along with knetworkmanager and adept says its there. I tried running nm-applet from a console and it says command not found

---

### Post by Hrothgar on 2006-12-01
Problem solved!

I commented out all the interfaces except loopback in /etc/network/interfaces

seems network manager will not manage anything thats already configured there

---

