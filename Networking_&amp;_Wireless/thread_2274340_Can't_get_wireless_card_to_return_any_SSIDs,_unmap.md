---
title: "Can't get wireless card to return any SSIDs, unmapped wifi kill button"
date: 2015-04-19
forum: Networking &amp; Wireless
---

### Post by Riklaunim on 2015-04-19
I'm trying Xubuntu on HP ELITEBOOK 725 G2 and I can't make WiFi card to return any SSIDs. The problem isn't rather with the WiFi card itself as I've tested also another miniPCIe card that do works on Linux with the same result. Bluetooth works (from the same card), while WiFi in network manager just has "disconnected" and no WiFi network available.

What I've noticed that the custom wifi kill button is unrecognized when pressed ("unknown key pressed" in dmesg). When pressed the device goes off/on but maybe something on the OS side needs to know about this too (needs the correct key mapping)?  rfkill list says noting is blocked.

---

### Post by Riklaunim on 2015-04-19
Adding **intremap=off** to boot args solves the problem.

---

