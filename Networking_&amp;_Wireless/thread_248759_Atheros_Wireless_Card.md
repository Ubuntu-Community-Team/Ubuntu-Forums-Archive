---
title: "Atheros Wireless Card"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by Orien Wu on 2006-09-01
I have an Airlink SuperG Wireless Adapter (Atheros Communications, Inc. AR5212 802.11abg NIC) on my current Linux system with FC5. I'm interested in switching to Ubuntu (desktop or server edition). Is my wireless card supported or do I have to manually get drivers for it?

Thank you.

[edit] Sorry, I should have posted this in the Wireless support section.

---

### Post by NetworkGuy on 2006-09-01
I did a quick search of the Wiki
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
and came up with your AR5212 card but there was a footnote in getting in to work with Dapper (6.06)

> DAPPER: Nearly works out-of-the-box, but had to add "wireless-rate 11M" to /etc/network/interfaces + reboot or two. BREEZY: Works out of the box with breezy. Works well, even with WEP. (Note: Some G520 may use acx100 instead.) HOARY: Rev. B of this card will not work out-of-the-box with Hoary--the madwifi drivers that shipped with Hoary are too old. An updated linux-restricted-modules* package is available  here Note that this package is not officially supported. Some users have reported problems with WPA in the forums.

Hope this helps

---

### Post by Orien Wu on 2006-09-01
Great! Thank you for your help. I'm curious though. Does Dapper only support network speeds up to 11mb/s as shown by "wireless-rate 11M"? Or is that not related?

---

### Post by NetworkGuy on 2006-09-01
No, I use a 54Mbps card in my Dapper  (ACX111 chipset)  No speed issues there.

---

### Post by Orien Wu on 2006-09-01
Okay, that sounds good. On the wiki page, that footnote is for a D-Link card. I assume that as long as the chipset is the same, it should work still? (Since I have an Airlink one...)

---

### Post by NetworkGuy on 2006-09-01
The chipset is the important part of the card as the drivers are written for the chipsets

---

### Post by Orien Wu on 2006-09-01
That's what I thought. I'm installing Ubuntu desktop at the moment. Wish me luck! :)

---

### Post by Orien Wu on 2006-09-01
Thanks for your help. My wireless card worked right out of the box without any configuration. Just needed to select my network. :)

---

### Post by dreyguy on 2006-09-17
Hey Orien Wu, I'm just wondering if you are on an open access, WEP, or WPA network. I just bought a wireless card exactly like yours and I am hoping WPA will work out of the box, but my gut feeling is WPA will not work without some tweeking.

---

