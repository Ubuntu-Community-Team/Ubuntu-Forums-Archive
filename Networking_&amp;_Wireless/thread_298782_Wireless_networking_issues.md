---
title: "Wireless networking issues"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by Yeuclid on 2006-11-13
From what I've been seeing in the last week or so in these forums it appears that Ubuntu has major problems in wireless network support. I am not alone in have great difficulty in making sense of what works and what doesn't in wireless networking. What is now taken for granted in XP to set up a very simple wireless network turns into a huge obstacle course in Ubuntu.

I am trying to use a USB wireless adapter, no security, nothing fancy. However Ubuntu just cannot seem to get the thing up and running. I am using NDISWRAPPER, since the built in Prism drivers do nothing.

Occasionally I get the Wireless extensions to kick in, and it has worked for a short time, then freezes, recovering sometimes when I remove and re-insert the adapter into the USB port, maybe that forces a rescan or whatever.

Is there any mileage in installing the latest NDISWRAPPER (1.28) or should I just admit defeat. 

It's a great pity, as I had such high hopes, but it seems that campared to XP, wireless networking is just too brittle and full of holes in Ubuntu. Are there any plans to improve this area, I would think that it's an essential requirement now.

---

### Post by Yeuclid on 2006-11-13
I take it all back.

Wireless works great on Ubuntu. I removed all references to NDISWRAPPER, reinstalled WLAN-NG, enabled the Prism2 drivers, installed WIFI-Radar, and it all burst into life.

NDISWRAPPER integration may need a bit of a health warning !!!!

This is on the latest 6.10 version, with a very cheap USB 802.11b adapter.

So far, so good.

---

