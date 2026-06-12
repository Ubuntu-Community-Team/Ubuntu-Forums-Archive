---
title: "XP style Internet connection sharing in ubuntu?"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by Drate on 2007-03-27
I would like to do XP style internet connection sharing in Ubuntu... how can I do this?

I have one wireless connenction to the internet, I have a small lan connected via my wired ethernet card.  How do I share my wireless connection?

---

### Post by scrooge_74 on 2007-03-27
What do you mean with XP style? Low security, lots of spyware and other stuff?  :lolflag:  that cannot be done.

You want to make your computer work like a router is it?  You need to enable both cards, but telling the system only one receives its IP from the DHCP server of your provider, the other one you give a static IP so the other PCs in your lan can refer to i as theur gateway.  Any firewall program like Firestarter needs to know which one is for the inside and which one connects to the internet.


I had a similar setup in the past but never got a DHCP server working for my lan, all PCs had to had an static IP in order to connect to the internet through my "server/router".  Any case maybe this [link]("http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm") will be helpfull

---

### Post by sdowney717 on 2007-03-27
firestarter will work fine for you, once its configured.
you have to set it to allow broadcast traffic. and some other settings.

---

### Post by Drate on 2007-03-30
Thank yall, btw... it works great now... still would like to do it DHCP style, but just having it working at all is really cool!  We can figure the DHCP bit out later.

---

