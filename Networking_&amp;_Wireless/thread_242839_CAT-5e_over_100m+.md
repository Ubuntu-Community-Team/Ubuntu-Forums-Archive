---
title: "CAT-5e over 100m+"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by schurtek on 2006-08-24
I am setting up a network in a building... problem is that one office is in the building next door. We have explored the wireless option... it is not an option. We need to run a cable from the one building to the other, via the walk way that joins the two buildings. Luckily the distance is only 70m, but what I want to know is, what happens when it is say... 170m? or 700m? What then? What viable and affordable route is there to go, other than TOS which requires very very very expensive tools. I have seen two possible solutions: but don't know what they are called, who makes them, and where to get them. 

1. The first was using a constant current data modem. It converts the digital signal into a different format. One that utilises current as the constant, ths allowing increadibly long distances to be obtained. This solution required a modem on each end of the transmission wire.

2. Power Over Ethernet Boosters. This one started with a small box that plugged into the mains. And had Ethernet In and Ethernet out. It put a 48V DC signal on top of the Ethernet Signal. Every 90m a booster is installed that is powered by the 48V DC. Only worked over a few hundred meters, and then required another power supply unit.

Any ideas?

---

### Post by N6546R on 2006-08-24
The restriction on segment length is mainly about timing and the length of a minimum-size (512 byte) frame with regard to collision detection. Attenuation is a concern as well. If you are going switch-to-switch on the long span, attenuation will be reduced, and collision detection shouldn't be too much of an issue with point-to-point connections through the switch.

Perry

---

### Post by netztier on 2006-08-24
> **schurtek said:**
> We have explored the wireless option... it is not an option. 

What performance requirements do you have? Do you need gigabit level speeds? Are a few megabits enough?

What cancels the Wireless Option? Is there a lot of "electrical noise" between the buildings? Security concerns? 

You could use two modern WLAN access-points (e.g. ZyXEL G-570S)that can be configured into "bridging mode" and two directional antennas. With each a router in a point-to-point configuration at each end, you can make sure (by way of limiting the broadcast domain, maybe even adding a few access-lists) that only traffic that really has to will use that link. 

Such a setup (without the routers) would cost around 350€ around here (2 APs, 2 patch antennas, a bit of coaxial cabling etc). 

With a proper enrcyption setup (WPA, WPA2) or even better a site-to-site VPN tunnel between the routers, there's no way to eavesdrop on the link. Allright, a denial-of-service attack is still possible by jamming the link with "noise" (an unshielded microwave oven can wreak havoc on a wireless link).

> Luckily the distance is only 70m, but what I want to know is, what happens when it is say... 170m? 

170m probably won't work at 100Mbps, but might if you downclock the devices to 10Mbps. If you happen to have a place where you have a power outlet somewhere along the path, you could add a switch right there and make the whole thing work for 200m in total.

> or 700m? What then?

No way you're going to make this work with one stretch of Cat5-or-better, not if you want full 100Mbps or Gigabit.

You might consider LRE (Long Range Ethernet), but this requires special end devices that are going to cost you more than a wireless bridging solution as described above.

> What viable and affordable route is there to go, other than TOS which requires very very very expensive tools. 

TOS? That is optical fibre, is it? I see no other true solution than that. Are we talking about a business solution here, or just two people trying to connect their LANs to share Internet access?

> 1. The first was using a constant current data modem. 

What data rates are you going to see there? I bet they'll be lower than wireless with directional antennas or even a downgraded 10Mbps ethernet link.

> 2. Power Over Ethernet Boosters. 

Nah. You need PoE-enabled Switches or PoE-Injectors at one end of the link, which will again cost money.


One disadvantage of a copper-based link has gone unmentioned: Sensitivity to electromagnetic and -static fields, potential differences between the buildings (and substantial electrical currents that will flow between the buildings - on your copper wires!) that can fry your equipment with ease during a normal summer storm.

That's why i suggest: Go wireless or go fibre. Switches with fibre ports GBIC slots have become affordable in the last 2 years.

Just my 2cents.

kind regards

Marc

---

### Post by oliverb on 2006-08-24
IMO go with fibre if your job depends on it, or possibly 5GHz wireless. Otherwise for a hobbyist lash-up I'd go with daisy chained switches if it's practical otherwise regular 2.4GHz wireless.

For site to site communications within the same town I've read that one option is to lease a "dry copper" circuit from the teleco and get a pair of SDSL (Not ADSL) routers, one for each end. Some makes will work back to back over a private circuit, I don't know if all will.

---

### Post by schurtek on 2006-08-25
I am needing 100mbps. Wireless not an option... security. If you have two panels UniDirectional Narrow Beams. It is easy to hack in by simply placing a rubber duck near one (in the beaam of course)... snorting the signal... then identifying the mac address of the receiving panel as well as WEP codes and all... (not that hard to get). Then you need a wireless adapter that can easily be reprogrammed (most on the market will work) Reprogram the mac address and you are on your way... first isolate the receiving panel with a sheet of steel.

The buildings are in the same complex... I have been supplied a steel trunking to use... the trunking is specifically there for lans and the stretch I am using is empty except for 20 meters at the one end, has two lan cables...

> **netztier said:**
> What performance requirements do you have? Do you need gigabit level speeds? Are a few megabits enough?

What cancels the Wireless Option? Is there a lot of "electrical noise" between the buildings? Security concerns? 

You could use two modern WLAN access-points (e.g. ZyXEL G-570S)that can be configured into "bridging mode" and two directional antennas. With each a router in a point-to-point configuration at each end, you can make sure (by way of limiting the broadcast domain, maybe even adding a few access-lists) that only traffic that really has to will use that link. 

Such a setup (without the routers) would cost around 350€ around here (2 APs, 2 patch antennas, a bit of coaxial cabling etc). 

With a proper enrcyption setup (WPA, WPA2) or even better a site-to-site VPN tunnel between the routers, there's no way to eavesdrop on the link. Allright, a denial-of-service attack is still possible by jamming the link with "noise" (an unshielded microwave oven can wreak havoc on a wireless link).



170m probably won't work at 100Mbps, but might if you downclock the devices to 10Mbps. If you happen to have a place where you have a power outlet somewhere along the path, you could add a switch right there and make the whole thing work for 200m in total.



No way you're going to make this work with one stretch of Cat5-or-better, not if you want full 100Mbps or Gigabit.

You might consider LRE (Long Range Ethernet), but this requires special end devices that are going to cost you more than a wireless bridging solution as described above.



TOS? That is optical fibre, is it? I see no other true solution than that. Are we talking about a business solution here, or just two people trying to connect their LANs to share Internet access?



What data rates are you going to see there? I bet they'll be lower than wireless with directional antennas or even a downgraded 10Mbps ethernet link.



Nah. You need PoE-enabled Switches or PoE-Injectors at one end of the link, which will again cost money.


One disadvantage of a copper-based link has gone unmentioned: Sensitivity to electromagnetic and -static fields, potential differences between the buildings (and substantial electrical currents that will flow between the buildings - on your copper wires!) that can fry your equipment with ease during a normal summer storm.

That's why i suggest: Go wireless or go fibre. Switches with fibre ports GBIC slots have become affordable in the last 2 years.

Just my 2cents.

kind regards

Marc

---

### Post by schurtek on 2006-08-25
The problem with fibre here in South Africa... is that the tools to make up cables cost more than a Dual Head XEONII Server.

Our local telco quoted us over ZAR1000 per end for the leased line. That's nearly US$200 per side... and that's monthly... They want ZAR5000 to install... and we still have to get our own modems...

> **oliverb said:**
> IMO go with fibre if your job depends on it, or possibly 5GHz wireless. Otherwise for a hobbyist lash-up I'd go with daisy chained switches if it's practical otherwise regular 2.4GHz wireless.

For site to site communications within the same town I've read that one option is to lease a "dry copper" circuit from the teleco and get a pair of SDSL (Not ADSL) routers, one for each end. Some makes will work back to back over a private circuit, I don't know if all will.

---

### Post by tturrisi on 2006-08-25
use coax cable...up to 500 meters.

---

### Post by oliverb on 2006-08-25
Or if you can wear the reduced data rate use ethernet range extenders at either end of your over-length cat5e cable.

I tried googling "ethernet extender" and got things like:

[http://www.patton.com/products/pe_products.asp?category=146](http://www.patton.com/products/pe_products.asp?category=146)

[http://www.rad-direct.com/App-Ethernet-extender-copper.htm](http://www.rad-direct.com/App-Ethernet-extender-copper.htm)

---

### Post by netztier on 2006-08-25
> **schurtek said:**
> It is easy to hack in by simply placing a rubber duck near one (in the beaam of course)... snorting the signal... then identifying the mac address of the receiving panel as well as WEP codes and all... (not that hard to get). Then you need a wireless adapter that can easily be reprogrammed (most on the market will work) Reprogram the mac address and you are on your way... first isolate the receiving panel with a sheet of steel. 

If one uses easy-crackable WEP128, it only takes a few minutes, yes. WPA and WPA2 are different - and currently unbroken as far as I know. That's why you might consider running a VPN Tunnel across it - let em hack /this/. Intrusion and eavesdropping issues can be addressed with proper encryption and authentication. DoS issues are a different matter of course - make physical access to the antenna difficult, then.

But if you actually *need* 100Mbit/s (so this is akin towards extending the LAN backbone to the other buildig, right?), WLAN is not quite what you'll need.

>  I have been supplied a steel trunking to use... the trunking is specifically there for lans and the stretch I am using is empty except for 20 meters at the one end, has two lan cables...

My english fails me here.. what do you mean by "steel trunking" -is that kind of a cable duct or "pipe" to put cable in? So what is stopping you from running your own stretch of fibre cable in there? No need for expensive single mode fibre, multimode will do. If you actually *are* in the most comfortable of situations to have a prepared path/duct to run your very own cable in, then do nothing short of fibre!

And if you run a 12x cable and have the installing company put in a patch panel at each end, other divisions of your company might be happy too if they can extend serial links and similar things (for example linking two PBXs) across a spare fibre pair.

Of course, equipment to install fibre does not come cheap. 

That is why we don't do it ourselves here (we have several km of fibre cabling in the building) - most companies that do large-scale Cat5 installations also offer fibre services, and will deliver quality assured products and protocols etc - and they have the tools and measuring equipment they need.


kind regards

Marc

---

