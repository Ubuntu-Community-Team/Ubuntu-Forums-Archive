---
title: "How do I get my wireless cards to work?"
date: 2005-06-01
forum: Networking &amp; Wireless
---

### Post by TomSawyer on 2005-06-01
What steps do I need to take to get my wireless cards working under Ubuntu? 

I have two:  WaveLAN Silver and Proxim Orinoco Gold card

The live disk got the Wave LAN Silver up and running without me having to do anything.  Once I did the install, everything went to hell and nothing worked. 

I run cardctl and whatever and it shows the card it there and I show modules have been loaded for the wireless card, but nothing...I have no idea...I never have been able to get these cards to work under Linux, nor have I ever gotten the help either...

  ](*,)

---

### Post by jkndrkn on 2005-06-02
Try this link:

[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

---

### Post by TomSawyer on 2005-06-03
[QUOTE=jkndrkn]Try this link:

[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)[/QUOTE]


Believe it or not, that worked. 

BUT, once I rebooted, for some reason the card was attached to ath0, but now wants to put it on wlan0, and I can't get it to work again...not sure what has happened...

---

