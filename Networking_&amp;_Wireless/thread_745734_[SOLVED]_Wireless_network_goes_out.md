---
title: "[SOLVED] Wireless network goes out"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by ChrisMP1 on 2008-04-04
I have an Atheros AR5006EG wireless card. I am using ndiswrapper for it, because the ath_pci module doesn't like the card. The problem is that the whole wireless system will randomly go down (about twice a week). I can clear it up by rmmod'ing ndiswrapper, then clearing out /etc/network/interfaces, setting up the GNOME network manager for static IP, and then changing it to 'roaming mode' (Yes, I actually need to do that). Is there a newer version of ath_pci that works better? (I don't know what package it's a part of.) Or is there a way to make this stop?

---

### Post by ChrisMP1 on 2008-04-05
Correction: I figured out the package (madwifi), found out that my card is really an AR5007EG, found a patch, and compiled madwifi. No problems now.

---

