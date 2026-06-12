---
title: "Network adaptor no longer founs6"
date: 2019-03-18
forum: Networking &amp; Wireless
---

### Post by jdkcarlson on 2019-03-18
Hi again, I am a person with an Acer Aspire R5-471T laptop and an often uncooperative Qualcomm Atheros QCA6174 wireless network adapter, now running Ubuntu 18.04. 

I had been using the internet normally for a few months, but as of yesterday it stopped working yesterday, and the control panel says no wireless adapter is detected. Often this is solved by rebooting once or twice, but not this time. 

lspci shows nothing like "network adaptor" or "Ethernet adaptor," and `dmesg | grep - ath` is returning nothing. More worryingly, I checked to see if the wireless worked in the small Windows partition I keep for troubleshooting, and it doesn't seem to be visible there, either. It actually says there's some unidentified USB device with a problem, which I'm worried could be my wireless card.

What can I do about this?

---

### Post by jeremy31 on 2019-03-18
I would take it apart, remove the wifi card and reinsert it.  Hope it was just a bad connection in the socket

---

