---
title: "working nearly out of the box, almost"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by drumkitcat on 2007-03-08
Hi Everyone,

Hopefully this will help others with a similar setup!

AFter a couple weeks of messing with my Toshiba Laptop with built in Atheros wireless card, and using the built in wired ethernet card for various updates, etc... and reading countless posts here in the wireless forum, I managed to get it to work!!! and here's how:
(running Ubuntu Edgy 6.1)
1.  For anyone using the Atheros card yes it's true you can do this without using ndiswrapper, although some people have been successful going the ndiswrapper route...

2. For me, here's what I installed :  madwifi and ALL restricted modules using the Synaptic Package Manager.

3. I also installed Wifi-Radar - this little baby is a lifesaver!  It turned out to be the only application that would connect my wireless laptop to my home network.  Huge kudos to Wifi-Radar I highly recommend it!

4.  Network Manager - I also installed this along with all related files using Synaptic Package Manager.  It's handy for switching between wired connection and wireless, although it will forget about your wireless if it isn't working properly.. AND  please also note:  see note 5.

5.  Right now, I'm using Wifi-Radar connected to my home Netgear wireless router and I'm able to enter this email using Ubuntu Edgy 6.1 from my Toshiba Satellite A40 laptop with Atheros AR5112 wireless card.  Here's what else is happening:
5.1 currently my Network Manager thinks there is no wireless connection!! it says "no network found" - well f*** that, Wifi-Radar clearly has my back on this one!  So remember people, Network Manager ain't the end-all be-all of connections.. it does work fine for a wired connection, but in my case anyway, it's flakey for switching to wireless.

Thanks for everyone's help!! I had totally reformatted my Toshiba laptop to TOTALLY expunge Windows XP Home.. and now I'm 100% pure Ubuntu!! Long live Linux!!!

---

### Post by teaker1s on 2007-03-09
:popcorn:

---

