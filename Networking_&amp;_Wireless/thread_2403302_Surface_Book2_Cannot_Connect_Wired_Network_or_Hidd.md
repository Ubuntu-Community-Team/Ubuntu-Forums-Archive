---
title: "Surface Book2: Cannot Connect Wired Network or Hidden Network"
date: 2018-10-09
forum: Networking &amp; Wireless
---

### Post by hijiy on 2018-10-09
First, I tried to connect wired network.
Ubuntu shows "connected", but browser cannot connect Google by proxy error.
I checked proxy config. And it is correct.
"dmesg" shows many "Tx status -71".
So I think the reason why I cannot connect wired network is this messeage.

Second, I tried to connect corporate wifi network.
It is hidden wifi network.
I could connect the network when I used kernel 4.15.0-36-generic.
But I cannot connect when I use kernel 4.18.11-surface-linux-surface.
"dmesg" shows "successfully disconnected reason code 3".

PC : Surface Book2 + Surface Dock
OS :Ubuntu 16.04

Thank you in advance

---

