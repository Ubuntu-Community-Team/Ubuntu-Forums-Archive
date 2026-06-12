---
title: "WiFi Card not seen"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by yellerKat on 2006-08-19
I've been trying to get WPA up (with no success) and have now totally borked the WiFi.

Ubuntu 6.06 had a problem with the built-in wireless: 
(Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01));

but could see the Linksys WPC54g pcmcia card:
(Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)).

What can I delete/run/install to return to the original set-up?

---

### Post by yellerKat on 2006-08-29
Well I got it going the old way - ndiswrapper/wpasupplicant - network-manager-gnome didn't work for me!

Connection is a bit flaky perhaps but at least it *works* - most of the time!

---

