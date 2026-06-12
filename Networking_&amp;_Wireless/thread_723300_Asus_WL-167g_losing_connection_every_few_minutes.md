---
title: "Asus WL-167g losing connection every few minutes"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by clueless on 2008-03-13
Hello to everybody!

Yesterday I bought an ASUS WL-167g USB WiFi adaptor and I am experiencing a weird problem: after I plugged it in the USB port the adaptor was recognized immediately on Hardy. I connected to my router (Fonera router) via KNetworkManager) and the internet connection worked for only a couple of minutes. After that it would seem still to be connected to the internet but I couldn't open any page or ping google.

So I decided to make a clean install of Gutsy but nothing changed. The situation remains the same. Every couple of minutes I have to right-click on the KNetworkManager icon and reselect the same network where I am connected to restart the connection.

I know it's not a problem of the router or the adsl modem because the internet connection works fine when I use my laptop's wifi connection to the same router.

Any thoughts?

---

### Post by clueless on 2008-03-15
An update to anyone having the same problems: I found out that following this guide
[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)
replacing the driver with ndiswrapper+windows driver solves the problem. But I am not sure if this is the right solution, seeing how these chipsets are supposed to be very linux friendly:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

You can also read this, although it hasn't worked for me:
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)

---

