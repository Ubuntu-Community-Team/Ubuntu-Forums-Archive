---
title: "Ping utility needed"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by RudolfMDLT on 2007-06-18
Hi there,

I'm a little out of my class here. I have installed a Wireless network in our complex(6 houses) that links all the houses to a asterisk VOIP system. Some times some of the connections go down between the houses. Is there a ping "Server" program that can ping multiple IP's at the same time and record the results? I just want to see how many ping's go through in a day to some of the problem houses?

Thanks,

Rudolf

PS: Is there a way to open multiple terminals through SSH? what I'm asking is, is there a way to open 1 through 6 of the TTY terminals running on the ubuntu server machine, the pc has no monitor and i access it via ssh?

---

### Post by nymphaeles on 2007-06-18
The first utility sounds like a network attack to me.  I used to know a utility like that many years ago, but I quit using it for an obvious reason.  
I can answer your 2nd question though.  You can open multiple tab consoles.  To do so, just go to File, Open Tab.

---

### Post by Mr. C. on 2007-06-18
There are numerous utilities on Sourceforge.  Search for "ping".

Also consider:
[http://oss.oetiker.ch/smokeping/](http://oss.oetiker.ch/smokeping/)

For a Windows utility:
[http://www.pingplotter.com/](http://www.pingplotter.com/)

MrC

---

### Post by RudolfMDLT on 2007-06-19
Thanks guys! The network uses no security so I don't need to crack it(because I own it), it's just darn unreliable and I need to fix that! :)

Thanks again,

Rudolf

---

### Post by netztier on 2007-06-19
> **RudolfMDLT said:**
> Thanks guys! The network uses no security so I don't need to crack it(because I own it), it's just darn unreliable and I need to fix that! :)


Care to elaborate a bit on how you "link" the houses with Wireless? 

Which are the wired parts, which are the wireless parts of that network? 

What wireless operation modes (Access Point,  Repeater, Client, Wireless Bridge) are used by which devices? 

Which channels do they use? Are there any other 2.4Ghz senders in the area (such as broken Microwave ovens, wireless headset units or wireless transmitters on a stereo set?

And: why no encryption? Telephony/VoIP data is very private and I'd want these encrypted! If not done on the WLAN layer, then at least with VPN!


regards

Marc

---

### Post by RudolfMDLT on 2007-06-20
Sorry for the late reply!

Topology:

6 wireless bridge stations communicate to 1 Access point via Unidirectional aireals(all 7 Senao units). inside each house, there is one Netgear WG602 AP/Bridge connected via eithernet to the senao and from there the wireless is distributed within each house.

Today I have changed the senoa bridges and AP to 802.11b, channel 2 and forced them to run on 2mbit/s. Comms are better except for one house - I'm getting on the roof and checking arial alignment tomorrow even though the bridge is reporting an 83% signal strength as on average only about 42% of my pings made to that network. The netgears inside each house are running 802.11g on channel 11.  

I don't use WEP as it can be hacked very easily and that the UT starcomms don't support WPA-SK or the latest 802.something standard. I'm actually throwing the darn things away tomorrow. Secondly the network is only being used as an Intercom system and not actual private telephone conversations, unless the neighbors daughter has an affair with the gaurd. :) But i do agree that the security inscription is needed.

Other phones being used are Snom 320's, Snome 300's, Polycoms's and 2 Hitachi's Wireless VOIP phones.

Thanks,

Rudolf

---

