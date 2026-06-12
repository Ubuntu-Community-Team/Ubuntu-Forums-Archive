---
title: "Wi fi issues"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by wadams on 2008-10-20
good day, I love Ubuntu, but I cannot get it to work with my atheros wifi card, I need a quick and simple fix... if thats possible.

thanks!
WAdams

---

### Post by yarn on 2008-10-20
i just got my wireless working the other day...the way that i got it to work was by enabling the restricted drivers in the repository, make sure that your driver is there and is checked and in use under system---> administration---> hardware drivers ...this fixed mine but there are also lots of different ways to get wireless working including using ndswrapper and fwcutter you can find plenty of tutorials on this if you search on google...also have you tried wicd instead of network manager..sometimes this helps a lot of people... also please post what type of router, what wireless card you are using. You can see what wireless card you are using by typing lspci in termainl. if your not sure just post the output of that.

---

### Post by wadams on 2008-10-20
in the hard ware drivers section 'support for Atheros 802.11 wireless LAN cards' is "in use" so obviously, this is not my problem.  PLEASE SOME ONE.  if i cant get this to work, I'm back on VISTA:mad:.

---

### Post by wadams on 2008-10-20
the exact model is Atheros AR5BXB63.
and it is in my Toshiba Satellite A215

---

### Post by yarn on 2008-10-20
did u try  wicd instead of the default network manager???

---

### Post by yarn on 2008-10-20
what exactly is it doing....is the network manager not seeing the wireless or is it just not connecting to a network...be specific as to what it is doing

---

### Post by wadams on 2008-10-21
It is just not seeing any wifi networks... when I'm right beside my wifi router!

---

### Post by yarn on 2008-10-21
Did you try wicd instead of the default network manager???   Mine didnt see any either but when i switched to wicd it worked...it is available in synaptip manager

---

