---
title: "Need ideas: Remote (Building to Building) Wifi Connection"
date: 2015-10-06
forum: Networking &amp; Wireless
---

### Post by ozark_hillbilly on 2015-10-06
OK fellow Linux users I need some sage advice on accomplishing the following:

I want to establish an internet link in my workshop, which is approximately 300 feet from my home, for the purpose of playing music (aka streaming music source like Pandora, etc). I have not decided on whether a remote pc at the shop or an internet ready music player is the best way to go. I am open to suggestions. My shop is slightly elevated above the house and my home computer/router is located in the basement. I can establish "line of sight" from the outside southwestern corner of the basement foundation wall. It would be about 30-40 feet from this vantage point to get inside the home to the router. Another consideration is that I have a western window on the main floor of the home that is visible from the shop. Would a repeater of some sort work in this configuration? Could I make/purchase unidirectional antennas (one for each location) to achieve the connection?
Since my shop is for woodworking dust infiltration will be a concern as well. I will probably need to make some sort of filtered enclosure to protect the receiving unit/player.  

Any suggestions are appreciated.

Ed

---

### Post by TheFu on 2015-10-06
Ubuquiti AP with a highly directional antenna. If there aren't trees or other things in the way should work. They may outdoor-safe APs.

Another option is powerline networking if power comes through the same circuit breaker.

For music playback, I'd just use a smartphone with bluetooth speakers, but using Raspberry Pi ($50) running OSMC (Kodi) with a local media file collection might be easier. OSMC has a built-in web server and the kodi app for android controls it easily.  App is free.

If all the media is local to the raspberry pi; either SDHC or external USB disk, no need for networking to the house, just a $15 wifi router to handle the pi connection and allow a wifi connection for the controlling smartphone/tablet/whatever. When you do decide to make the network connection, the router can be switched to bridge mode with the WAN port connected to either a local AP in the workshop bridging to the house or powerline port.

Lots of other options too. If there is coax between the house and workshop, there are local networking options for that too. 

Powerline isn't great - expect less than 10% of the advertised speeds, if that. My 600 Mbps powerline inside the same house (early 90s construction), bridging different floors gets only 60 Mbps.  The same equipment at a pizza restaurant (early 70s construction) achieves only 40Mbps across the room.  But powerline is "stable", unlike wifi.

---

### Post by ozark_hillbilly on 2015-10-06
TheFu,

Were you referring to the Unifi AP [[https://store.ubnt.com/unifi/unifi-ap.html]?](https://store.ubnt.com/unifi/unifi-ap.html]?)  I see where it has an ethernet jack on it but I don't see how it would interface to an antenna. Would two of these be used? One as an *access point* (link to router) and one as a *bridge* (link to remote device - pc/internet radio)? Or is the Unifi AP built with the antenna inside?

Additionally, I have a spare Linksys WRT54G router. Could this be used as the *bridge *at the remote end?

ed

---

### Post by TheFu on 2015-10-06
Sorry - I don't recall the model. Plus if you just have wifi devices in the workshop, a 2nd AP there may not be needed.

I would try the WRT54 in the workshop - can't hurt. Tomato is nice on that model. If it doesn't work, another Unifi might be needed.

Plus - I'd get the "long range" version - [https://store.ubnt.com/unifi/unifi-ap-88.html](https://store.ubnt.com/unifi/unifi-ap-88.html)  The whole thing is THE antenna. It is directional.  I haven't used this model, but I have deployed older models for a campus. Power is over the ethernet cable, injectors are included. 1 CAT5e cable does it all.

I should point out that these devices are not "consumer friendly"- they are meant to be installed by folks with good networking knowledge.  You don't have to be an expert, but a little more than average for a home user is required.

---

### Post by coldraven on 2015-10-07
I'm not sure if a powerline adaptor would work in your situation but you can get them with built-in wifi. It would be nice if you could borrow a pair to see how it goes.
A friend just got a pair for about $80, I cannot remember the name but here is an article about a similar product.
Something must be wrong with Amazon's pricing, I just checked their site and it's marked at over $700! Similar items on eBay are about $100
[http://www.theregister.co.uk/2013/07/24/review_devolo_dlan_500_av_wireless_plus/](http://www.theregister.co.uk/2013/07/24/review_devolo_dlan_500_av_wireless_plus/)

I did a search for the range question and found this here: [http://www.smallnetbuilder.com/basics/lanwan-basics/31585-smallnetbuilders-powerline-faq](http://www.smallnetbuilder.com/basics/lanwan-basics/31585-smallnetbuilders-powerline-faq)

> **11. How far do powerline networks reach?**

 It's hard to find a good answer to this.  One thing that is a given  is that powerline networks won't work across transformers. This usually  prevents your neighbor's powerline network from connecting to yours. But  in apartment buildings there is definitely a chance of your network  reaching beyond your unit. So you should take the steps outlined in  Question 13 to ensure your network is private.
 As for distance within your home, some sources quote 300 meters, while [others say 200]("http://www.linkpro.com.tw/faq_powerline.htm#Q8-Broadband"). NETGEAR's powerline FAQ takes an area approach and quotes "5000 square feet or less".
 In general powerline networking should work in a typical home or  apartment and might even work to provide Ethernet to a separate garage  or outbuilding, if the distance isn't too far and it is on the same  electric service.



Edit: After a bit more research it seems that your woodworking tools might interfere with the adaptor. I'm presuming that you have big motor driven saws etc.

---

### Post by TheFu on 2015-10-07
Good points from coldraven!  Motors CAN interfere with powerline networking. I've never tested mine with even the vacuum running.

The Ubiquiti stuff is good if there is line-of-sight.

Amazon isn't always the "seller". Some sellers put stuff out there for 3x-1000x the price hoping to catch someone desperate.

---

### Post by tgalati4 on 2015-10-07
With 300' of CAT6 cable, a shovel, a set of crimpers and two crimps, I would simply run a clothesline.  Can-and-string communication.  You can bury it 6", you can leave it on top of the ground, you can hang it in the trees (until the squirrels chew it).  The Ethernet standard is 1000' before a boost is needed.  A pull-box of cable is about the price of a router.  You can ask around if anyone has a pair of crimpers that you can borrow.  With 1 pull-box, you can pull two strands to the workshop.  Use one for your media server and use the second as a backup or as a dedicated workshop monitor--you will find a use for it before long.

---

### Post by ozark_hillbilly on 2015-10-07
That is an option. Is CAT6 rated for direct burial?

---

### Post by tgalati4 on 2015-10-08
Oh yes, as long as it works.  It's 5 volts (really + or - 2.5 volts).  Run it under water; just don't run a shovel through it.  You could run PVC pipe as a conduit, but that's a long run.  You should get several years out of it before something eats it.  If you are concerned about longevity, there are several industrial-rated CAT6 cables from Belden, General Cable, and others.  They have tin foil shielding, thicker jacket for factory installation.  Then there are Live Show cables, rugged jackets for stage use.  I would get a good-quality cable (preferably US-made) and start digging.

Here's an example for ship use:  [http://catalogs.generalcable.com/Viewer.aspx?docid=e7177349-9484-4a40-a0a5-a4a5012b45a3#?page=82&term=CAT6](http://catalogs.generalcable.com/Viewer.aspx?docid=e7177349-9484-4a40-a0a5-a4a5012b45a3#?page=82&term=CAT6)

Do a search for Gepco, General Cable, and Belden Cat6 and you will find lots of choices.  I would not use the cheap, non-domestic cable at the local Home Depot.

---

### Post by TheFu on 2015-10-08
Fibre to remove the grounding issues?
Though I've read that lightning protection for any ethernet is basically worthless unless done like the phone company does it.

---

### Post by tgalati4 on 2015-10-08
For grounding, you simply take the tin foil shield and ground it at one end and leave the other end unconnected.  This will reduce RF pickup, and provide some lightning secondary protection.  Nothing will really protect you from a direct strike from either building.  50,000 volts will jump across any optical gap, across any UPS (that has now burned up and is covered internally with soot).

If lightning is an issue, I would put lightning rods on both buildings (2 or 4) and put 8-gauge solid copper bonding wires to 10' deep copper grounding rods, one per lighting rod.  You can interconnect them at the ground level.  For the building's electrical ground, I would put a separate grounding rod 10' away from the lightning grounds.  I would not interconnect two grounds between buildings 300' away--which is why you leave the shield unconnected at one end of a shielded cable.  If you use unshielded cable, then don't worry about it.  You really only need shielded cable if you live under power lines. And then you have other problems to worry about.

---

### Post by ozark_hillbilly on 2015-10-11
Closing thread"- decided to go with cable and conduit. Thanks for the input folks. Waiting for parts now....

---

### Post by tgalati4 on 2015-10-12
Let us know how it works and take a few pictures.  I'm sure it will help others with this type of networking issue.

---

