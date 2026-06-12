---
title: "DI 524 router problems"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by dbzsephiroth on 2007-04-13
Hey guys, could use a little assistance here ^^
normally i wouldnt post anything but this is something that 3 hours of searching on the forums has come up with nothing XD (waits egerly for someone to prove me wrong in 5 minutes)

So anyway as u can tell it has something to do with graphic design......*looks at title* oh WAIT! nvm, Router problems! =D

Currently my set up is:

Main machine HP media center connected directly to the internet. (Ubuntu edgy)
HP connected to wireless router via wire.
Server connected to router via wire as well. (some bill gates OS BS)
And soon to be another machine to be connected wirelessly. (Edgy...<3 ubuntu =P)
Plus a PSP and a Wii (and a PS3 when i get the cash for it) =P


Well a simple ISC should be sufficient....but NOOOO! D-link decide to make ISC routing a mystery.

Initially both machines were connected via a wired hub, everything worked fine, internet shareing, remote desktop, etc etc. (Btw learning how to make ubuntu share internet was fun! *end sarcasm*) But as soon as a wireless router repleaces the hub, chaos is unleashed!....well yeah im sorta exaggerating there but u get the picture.

Connecting the modem directy into the router sorta does, and sorta doent work, but id rather it be to the ISC to the linux machine, i get more control over it that way.


So anyway im basicly asking for help on configureing the router to allow this, and if any work needs to be done to the ISC on ubuntu..


I think thats it......[edit]My bad, no they cant ping eachother, but they can ping the router

Thanks guys, first one to solve this gets a E-cookie!

---

### Post by dbott67 on 2007-04-13
There are 2 ways to accomplish this:

_**1. Easy way: **_

Let the D-Link 524 handle connection sharing and routing.  Connect your DSL/Cable modem to the WAN port on the D-Link.  Connect all PCs to one of the 4 LAN ports on the D-Link.  Disable/remove "internet sharing" on Ubuntu.
[U][B]
2. The somewhat more difficult way:[/B][/U]

If you wish to let the Ubuntu box continue to handle the 'ICS' part, then you really on want the D-Link to handle the internal LAN stuff.  Basically, just do the following:[LIST]
[*] Turn off DHCP on the D-Link and let your Ubuntu-box handle assigning DHCP, NAT and routing requests
[*]Assign the D-Link a static IP address on the same internal subnet as your PC-router (this way, you will be able to login to the D-Link from any PC on the internal LAN).
[*]Connect the D-Link to your network hub/switch using one of the LAN ports.  [COLOR=Red]**Do NOT use the WAN/INTERNET port on the D-Link.**[/COLOR][/LIST][COLOR=Red][COLOR=Black]By using only the LAN ports on the D-Link and turning off DHCP, you will essentially have turned the D-Link into a wireless AP and switch (no router, no NAT, no firewall, etc.).

-Dave[/COLOR][/COLOR]

---

