---
title: "Xubuntu Wireless Neworking--Almost there"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by rellis3 on 2008-06-06
Hi...

I have loaded Xubuntu on a Compaq Presario 2100. I have consulted the latest community documentation on getting the wireless connection working. Tried using the b43-legacy driver, but my device appears to be rev 02, and that did not work. So I downloaded ndisgtk and the appropriate Windows drivers, and put the .inf and .sys files in their own folder. Fired up ndisgtk and configured ndiswrapper with that. When in Terminal I use "ndiswrapper -l", the response is as expected, that the driver is loaded and the device present (ID all matches--1434;4320 (rev 02)).

iwconfig shows wlan0, but a ping goes nowhere--only unknown hosts. Pinging the router responds that the network is unavailable. I have disabled eth0, as suggested in the documentation. I really don't know what to try next. Any ideas where to look, or what I might profitably try?

Thanks in advance.

Raney Ellis

---

