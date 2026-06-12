---
title: "Xubuntu wireless configuration ...... how?"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by moonshinerat on 2007-04-23
For the first time I had a Linux installation that recognised at install my Dell 1390 wireless. However, that now doesn't seem important to Xubuntu because I can't get it configured.

The wireless light does not show on my Dell 640m but I did manage to get the laptop to recognise that wireless is available because going into System: Network: it offers both wireless and wired connections. I have typed in my SSID and my WEP key and ticked Enable My Connection. The main network settings page shows a picture of a transmitter with red radio waves. It also names my SSID and dhcp type connection.

When I go to Firefox it just keeps saying Looking For google.co.uk then page not found. If I plug my cabled ethernet back in it works as does the wireless on XP, Vista and Fedora.

I cannot even find any kind of device manager in Xubuntu or Wireless scanning function to see if the card is configured properly and find any available networks.

Where do I start to solve this problem and more importantly, anyone know how I can finish?

Thanks guys....

---

### Post by spd106 on 2007-04-24
It's highly likely that you have a Broadcom based wifi card. I believe most Dell 13xx cards have them. This means that you will need to either install the bcm43xx firmware or use ndiswrapper with your windows driver. There are multiple guides to doing either of these methods in this forum. I can't honestly say which is the best, it depends a lot on your wifi card.

This wiki page is highly regarded [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

---

