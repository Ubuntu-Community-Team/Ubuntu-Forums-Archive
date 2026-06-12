---
title: "Totally stumped - No option for WPA with one card, and the other card doesn't show up"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by blazemore on 2007-06-20
I have two problems.

The first is that there is no option for WPA security in Ubuntu 7.04 (AMD64) using a Ralink 2500 card (I read something about this elsewhere but it was not really made clear).

The second is that I cannot get my preferred wireless network device, the USB connecting Linksys WUSB54GS v.2.0 to be recognised at all. The power light is on, and it works in Windows, so it's not a hardware problem. The only device which shows up in the network manager thing is RA0, which I presume is the Ralink one.

I am using Ubuntu 7.04 x64 edition

---

### Post by scrooge_74 on 2007-06-20
Check[ this]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") for more information on each card

Maybe the Ralink does not support WPA in Linux check the above info, for the Linksys, I have good and bad news, since it is USB is going to give you troubles, if you look you will find a HowTo in the forum, you are going to need to use the windows drivers using ndsiwrapper if not mistaken.  I tried to get one of those USB cards from Linksys with mix results for a friend's laptop.  I made it work for a while then I was unable to get it to work again after a couple of reboots and since he was a newbee and on its way to catch a friend I had to give up.

---

