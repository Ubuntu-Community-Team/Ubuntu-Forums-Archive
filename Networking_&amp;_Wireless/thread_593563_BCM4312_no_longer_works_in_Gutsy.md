---
title: "BCM4312 no longer works in Gutsy"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by uzerzero on 2007-10-27
I just recently did a fresh install of Gutsy Gibbon from Feisty Fawn (upgrade failed and fubarred my system), and when it booted up, it came up with the restricted drivers and I told it to use the nVidia drivers and to go ahead and download the firmware for my network card. After a reboot, the WiFi hardware light turned to blue (on), but turning it off would leave it at blue. Network manager shows that I have a wireless connection installed, but it won't show any networks. I tried the sticky, as that's what I used before to set up my wireless, but that just made my hardware light stay orange (off). 

The weird thing is that under Feisty, lspci would list my card as a Broadcom BCM4310 UART card. lspci under Gutsy lists the exact same card as a Broadcome BCM4312 802.11 a/b/g. 

I don't see how compatibility worked beforehand, and yet won't in a recent upgrade. If nobody else knows how to fix it, I will be downgrading to Feisty.

---

