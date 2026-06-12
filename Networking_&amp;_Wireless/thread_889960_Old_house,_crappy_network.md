---
title: "Old house, crappy network"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by le_vainqueur on 2008-08-14
This is not Ubuntu related, but hopefully that's okay.  I will first admit that I am a newbie when it comes to networking, but I am hoping to learn in the process of solving my current frustrations.  I don't know all of the proper terminology, so sorry for any confusion that I may incite. 

**The House**
I live in a coop house next to a college campus.  Over the past few decades people have been moving in and out with high frequency, and no one has ever really taken care of the house network largely because most people there are not too knowledgeable about computers.  As a result, there are many ethernet cables which seem to go to nowhere.  

Currently, there is cable internet.  The modem, router, and hub are on the 2nd floor.  The wireless signal is not strong enough to get all the way to the basement.  People living on the 2nd and 3rd floors have routed ethernet cables to their rooms by drilling through walls and floors.  This does not seem to be a very good option to get internet to the basement since it would require several hundred feet, and there are no vents to go through since the house is so old.

From my deduction and tracing cables it seems as though there used to be a computer network throughout the house which was centralized in the basement.  Many of the rooms have ethernet ports along the wals which all seem to trace back to a "hub" (probably the wrong term) which is in the a room in the basement.  I'm not sure where the internet would have come into this device, though -- I'll keep looking.  There is no internet signal in any of these ports, and it seems as though the entire network is useless.

**The Goal**
I would ultimately like to get wired internet into the basement for my Xbox 360, and get wireless to other locations in the house where the signal is not strong enough to get online efficiently if at all.  What is ultimately important is sharing an internet connection, not networking a bunch of computers.  I'm not sure if that matters, but I thought I should clarify what the purpose is.

**Ideas**
I've been serching the web a bit about possible solutions.  One idea I had was to use multiple routers in order to have wireless at several points in the house.  I would run into the problem of having a wired connection to the basement again, but at least it would be an improvement.  It seems from my reading that this may not be a very good solution, however.

Another option would be to purchase/rent a second cable modem.  Since there is a working coaxial cable in the basement for the TV, having a modem in the basement would definitely solve the basement issues, and hooking up a wireless router to that modem would solve the wireless issues in the house.  This approach seems ideal, but some web research suggests that I might have to pay the internet provider for two subscriptions which might eliminate this as a viable option.

The third option I have thought of would be to rerout some of the existing network cables from the old network to the router on the 2nd floor.  Since this network goes throughout the house (including the basement) it might be possible to find a cable long enough which has already taken all of the necessary twists and turns to get upstairs.  Tracing the cable would be difficult, but not impossible.  This solution seems is definitely not elegant, but might be possible.

The fourth option is to suck it up get a new cable (who knows how long), and rout it to the basement.  I know that the cables all go outside -- does this require a special cable? 

**In conclusion**
I would greatly appreciate any criticism, advice, guidance or literature that could help.  I hope to learn a bit about networking in the process.  If there is information that I have not provided, please let me know.

---

### Post by Iowan on 2008-08-14
Sounds like an involved project... a signal tracer would help sort out which ethernet cables are which. The next question would be: how good are the cables (ie. are they Cat5 or better)? The idea of a (coaxial) cable splitter (like a "T" connection - not a sharp knife...) comes to mind, but one must be cautious to avoid degrading the signal.  "Hub" might be an accurate term - especially if the system is very old.

---

### Post by bab1 on 2008-08-14
What an interesting project.  There are some considerations.  The cabling is limited to 100 meters (300 ft.) by Ethernet standards.  So you should be able to run that length in a house backbone arraignment.  If indeed the item you call a hub is indeed a hub, then make it a doorstop!  It will be 10Mbs only and all the the network traffic is on a common wire.  Replace it with a switch.  This will bump you up to 100Mbs and the traffic is separated.  As far as the actual cable is concerned; inside wiring is more important than outside.  The inside type is called Plenum Type.  This name comes from its usage in plenum cambers inside buildings.  It is chemically designed to be non toxic in fire situations.  See the EIA/TIA spec's [[COLOR="Red"]here[/COLOR]]("http://www.showmecables.com/Cat-6-Plenum-Cable-CMP.html")

---

### Post by le_vainqueur on 2008-08-15
> how good are the cables (ie. are they Cat5 or better)
I was wondering about this. How do you determine this?

> cabling is limited to 100 meters (300 ft.)
Out of curiosity...why is that?

> If indeed the item you call a hub is indeed a hub
I am going to post a picture tonight or tomorrow to avoid confusion.  It looks ancient, so I'm guessing it will give everyone a feeling for the type of network that was in place.

> As far as the actual cable is concerned; inside wiring is more important than outside
So, you mean there is variation on the inner and outer portion of the cable?  What I was trying to say in my post was that all of the cables in the existing network physically travel outside of house in order to get from the the basement to the 2nd floor.  There is a bundle of 10 or so that travel up the side of the house.  Does this influence cable selection?

**Another thought**
Suppose I am able to get one new ethernet cable from the router on the 2nd floor down to the basement.  Would I be able to attach a router in the basement in order to "boost" the wireless signal?  This would essentially daisy-chain two wireless routers to the cable modem.

---

### Post by Iowan on 2008-08-15
Cables *should* have rating printed every foot or so along the cable.

Signals degrade over distance.  Noise creeps in.  You can "buffer" the signal with switches, hubs, or other "repeaters", but there are limits to how many can be inserted (some introduce delays).

If it's REALLY ancient, it could be a completely different technology (token ring, etc).

The variation is in the outer jacket material.  There may be some that are more UV resistant for outside use, but Plenum Type is designed to share air ducts. Then there's the "standard" PVC jacket that us cheapo's... uh, economy minded individuals... use.

---

### Post by bab1 on 2008-08-15
Iowan said it best.  One thing about the hub; not all hubs are repeaters.  The basic hub does not boost the signal.  If the cable is "twisted pair" ie: cat 5 then it doesn't mater what protocol used to be run on it.  I believe what Iowan was trying to get at was that you make sure what type of cable you have.  There used to be cable as big around as a garden hose used for networking and then there is coax also.

Edit:  With a switch or a router in between you can easily span 500 feet.  I don't see the need for a router in the basement either.  Routers are for connecting two different networks together.  You only have one (the house).

Edit2: When I spoke of outside vs the inside I was indeed referring to where you run the cable.  If you run cabling inside the house the house it should be of the Plenum type.  The insulation becomes toxic in a fire with the  ordinary type.  It is marked on the outside as iowan indicated.  It's a little bit more money, but hey, what are your lungs worth these days?

---

### Post by le_vainqueur on 2008-08-17
> I don't see the need for a router in the basement
My reason for using a router in the basement wouldn't be to extend a cable, so I don't think I need to worry about the "repeater" issue.  The motivation for putting the second router would be to effectively extend the range of the wireless network. Would this cause any complications?

Here is a picture of what I have been referring to as a "hub"

[IMG]http://img99.imageshack.us/img99/4926/dsc00184sz8.jpg[/IMG]

---

### Post by bab1 on 2008-08-17
Nope, not a hub as far as networking is concerned.  That is just the wiring closet.  A hub is a device in the network.  Where in the picture is the line from the ISP?  Is it the big grey connector on the middle punchdown block? Where is the router; is it just to the right?  Is there a patch bay?  What is just to the front of the 3 punchdown blocks?    It's been a million years since I have done any of this kind of work. Sorry for all the questions, I'm looking for where you can insert the needed devices.

Edit:  You do NOT need a router to extend the wireless.  You need a wireless extender also called an access point (AP). You can use a simple $20 switch and connect the AP into that.  You could then have wired and wireless there.  You only need 1 router for the entire house.

Edit2:  I just went over your first post.  It seems to me that if you can get one active line from the cable modem connected INTO one of those ports in the wall you might have enough signal at those punchdown blocks somewhere. The blue wires are going to the ports on the walls you mentioned. I would get an Ethernet tracing tool.  You can get both visual and audible testers.  Then I would CAREFULLY eliminate all that is not needed.  The patch bay may in a sense be where the cable modem is.   You might see if you can con a CS student into helping you out.

---

### Post by cariboo on 2008-08-17
Actually I use an old smc barricade as a wireless extender out in my garage. I ran a cable from my router here in the house to the smc changed the static router ip address to dhcp and now I have 100% signal strength, where as trying to connect to my router in the house was hit or miss, depending on the weather. If it was clear and cold I'd get about 50% if it was snowing maybe 20% (we get 8 months of winter and 4 months of tough sledding :)).

Jim

---

### Post by bab1 on 2008-08-17
So, you just use the original net to get to the smc and have a second net  for the wirless.  That works.  I was trying to get him the option of both wired and wireless   I have friends in Edmonton and I know cold.  That's why I live at the beach in socal.  :D

---

### Post by le_vainqueur on 2008-08-26
Thanks for the continued help!

I haven't had the time to look into a complete solution, but I have successfully extended my wireless network using a spare wireless router I had lying around using [this guide]("http://kbserver.netgear.com/kb_web_files/n101496.asp").

I still hope to get either a new cable to the basement or plug into the old line somehow.  I will have to look at the existing cables to determine if I can use them or if I will have to start from scratch.

---

### Post by mips on 2008-08-26
> **le_vainqueur said:**
> 
Here is a picture of what I have been referring to as a "hub"

What a mess. Thats not a 'hub' as such.

If you have the time I would suggest buzzing all those cables out, marking them, and indicating them on a floorplan of some sorts. You should be able to trace the existing basement cables to another location, if they don't go all the way to the 2nd floor maybe you can patch them on all of the other floors. This would be a good start.

Next terminate the cables on a proper patch panel & connect the patch panel to a switch with patch cords.

Check to see for a free point on each floor then connect a wireless AP to them so you have wireless on each floor.

This suggestion uses your existing infrastructure.

Do you guys have money avaible to spend on this? If you do you might want to consider starting from scratch. Put one switch on each floor and connect an AP to each switch. Run cables to the rooms only on that level of the house. Interconnect the different floors with the switch uplink ports (these are genrally 1G or 10GB).

---

