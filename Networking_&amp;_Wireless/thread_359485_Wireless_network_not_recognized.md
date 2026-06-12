---
title: "Wireless network not recognized"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by mich_michidelimacinaok on 2007-02-12
Netgear wireless card
Ubuntu 6.06 Dapper

I've configured the ath0 device (the card) and it recognizes the wireless network and shows a signal strength, but when I open firefox, I get a "Network not found" message.

How to fix this?

Thx

---

### Post by hawksbill on 2007-02-12
You should at least post your ifconfig status. go to a terminal and type "ifconfig". This is the basic status on your network interfaces.

As well are you using a wep key from your access point?
Can you ping the access point? If so you may need to set up DNS servers manually.

These are a few common issues when setting up a wireless network.

---

