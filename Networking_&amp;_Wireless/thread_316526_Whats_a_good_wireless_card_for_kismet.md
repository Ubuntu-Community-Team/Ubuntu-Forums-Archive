---
title: "Whats a good wireless card for kismet"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by acidblue on 2006-12-10
I want to know whats a good pci and pcmia wireless card
for unbuntu.? for laptop and desktop pc.
What works out of the box with airsnort/kismet?
I'm currently using 5.10 but will upgrade to 6.06
just as soon my cd's arrive

---

### Post by nixternal on 2006-12-10
D-Link Air DWL-650
IEEE 802.11b Wireless LAN Adapter
H/W: J3
F/W:1.3.5

It uses the Orinoco driver and works w/o tweaking in Ubuntu.

I set the kismet.conf to use:
eth0,orinoco,orinocodriver

and Orinoco works like a charm. I have noticed I have issues with WEP/WPA, but haven't messed with it much to get it working.

I can use Kismet, Airsnort, Aircrack and all of the fun tools for War Driving. I  paid $5 at the most for the card as well. It is older, but it always works for me.

---

