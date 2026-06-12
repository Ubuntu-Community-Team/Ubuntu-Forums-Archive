---
title: "Possible to have my 360 connect through my PC?"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by NinjaEX on 2007-12-25
Hey all.

I don't know the technical term for it, but would it be possible to have my 360 hooked up to my PC (running Gutsy), and be able to get online with my 360 via my PC's wireless connection?  My router is in a totally different spot in the house, and not even my 50 ft. ethernet cable can reach.  I know there was a way to do this in XP, since I used to do it with the original Xbox, but I'm clueless if Ubuntu can do it.  Thnaks in advance.

---

### Post by spd106 on 2007-12-25
Yep, you want Internet Connection Sharing.
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

It's probably going to be easiest to set with [Firestarter]("https://help.ubuntu.com/community/Firestarter"). Make sure you get dnsmasq and dhcp3 as well.

The only thing you need to think about is setting a static IP address for for the wired connection.

---

### Post by AmericanYellow on 2007-12-25
Yes, you can share your PC's internet connection with your 360 as I do. You need to install the user interface for the Ubuntus's firewall, Firestarter. You can go to "Add/Remove" and search Firestarter. Once you install it, run the wizard and enable Connection Sharing. Once enabled connect your 360 via Ethernet and you should be able to get online to 360 Live. :guitar: Guitar Hero!!

Just to let you know. The last time I installed FireStarter, Ubuntu didnt want to boot anymore. Checking the forums, it seems it hasnt happened to anyone else but me. If it does happen, likely won't, remove  it through recovery.

---

### Post by NinjaEX on 2007-12-25
Hm...
I tried firestarter, and it doesn't recognize any of my wireless devices, apparently...not even my PCI card.

(At the moment, I'm connecting via a Belkin USB wireless connector thing, do I need to do anything special for that?)

---

