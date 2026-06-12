---
title: "Setup and home network from scratch with wireless and wired."
date: 2021-01-11
forum: Networking &amp; Wireless
---

### Post by hairy one on 2021-01-11
Hi all,
Wanting to do a proper job of installing a network at home.
Requirements:-
Needs to be wired and wireless.
I want to setup static as I will add a server for entertainment and backups.
The setup will need to be upgradable, due to us being on ASDL (Australia) at the moment and NBN possibly coming in the future sometime (government talk), is there a setup that the router is "linked" in? maybe Mobile phone integration because yes the system load at time grinds the internet grid to the www (world wide wait) 62nd in world ranking we are!!!

We are in a two story house but the main level is where the is wireless required the most as the wife now works from home.

I will be building the server later date.

There is no plans just after ideas, resources and for direction from knowledgeable people and build from there.

Regards,
Hairy.

---

### Post by TheFu on 2021-01-11
A few thoughts:

[LIST]
[*]wired is always better. avoid wifi whenever possible.
[*]Don't worry about CAT6 cables unless you just want to waste money. Use CAT5e when wiring the house. These have double the capacity needed for GigE everywhere for 500ft distances. If you plan to support 10G for your core network devices, some systems are shipping today with 2.5G NICs, CAT5e is fine for short distances, but don't trust me. Do your own homework. If you need to connect to an external building, run conduit and coax so you can use MoAC networking.
[*]Wifi shouldn't be trusted. Keep it outside your wired, trusted, networking.  Put the kid's computers, gaming systems and media streaming devices and guests on that subnet.
[*]Keep the wifi AP as a separate device from the router.  Ubiquiti makes a great line of near-enterprise WifiAPs that are cheap and don't get confused with more than 5 client devices. Plus, they use PoE which makes deploying an AP where you need it really, really, easy. No need to worry about a power-socket or running a power extension to the location.
[*]Plan on having 2-3 subnets. That means you need a router that supports this capability.
[*]Ignore more "consumer" routers.  You want a router that will last 10+ yrs, be maintained by the vendor (or easy for you to maintain), which leaves you with about 3 options.  Microtik, Ubiquiti, or some sort of home-built router running OPNSense or pfSense.  The first 2 are SW+HW and have a great track record for maintaining their router firmware. They make it easy.  The OPNSense method is more DIY and extremely flexible. All require learning some router terms and ideas.  The Microtik is the most user friendly. Beware, Microtik still sells 10/100 base-tx routers. You don't want that. Read the details in the descriptions.  I have an APU2 running OPNSense.  The APU2 is a little under powered for 1Gbps WAN connections (can only get about 650Mbps in my testing), which isn't a problem for me - 25/5Mbps connection currently.  I can get a 1Gbps/1Gbps connection, for a price, these days, just need to handle some infrastructure changes to move there. There are APU3 models, but I haven't kept up with those.
[*]If you want to connect into a cellular data ISP, that is almost always a different router or at least a different modem. There are 4G and 5G routers made which do that for around US$150-US$300.  If you keep your router separate from the modem (DSL/DOCSIS/4G), then it will have a single WAN port connection into the modem and swapping the modem won't be THAT big of a deal, but it will be an extra device to be managed, patched, and powered. Having a separate device probably adds 10-20% to the total cost of the WAN-modem + router costs.  My ISP rents the modem/router for $18/month. I'm not allowed to buy it to stop the rental fees.  I use their router as a bridge and guest wifi device only, with the real network security for my network happening with my APU2 router.
[/LIST]
Hopefully, that was clear enough?

When it comes to Ubuntu, you probably don't want the backup server and the media server to be a single machine. Just something to consider.

---

