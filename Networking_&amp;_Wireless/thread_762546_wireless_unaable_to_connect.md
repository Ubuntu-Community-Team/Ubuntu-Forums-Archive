---
title: "wireless unaable to connect"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by nhler on 2008-04-22
I'm running 8.04. I did a synaptic update on Saturday and lost my wireless connection. I have an ar5007eg wireless card, set it up using ndiswrapper. I can see a bunch of wireless networks (including mine) but cannot connect to any of them. I am using wicd for a network manager. Any help, tips or suggestions would be appreciated...I need to get of this vista crap and really use my laptop! Thanks

---

### Post by mrbuntuman on 2008-04-22
lets start from the beginning so , 1st off win vista aint so bad, i heard great comments on how vista make a great paperwieght lol.

So if ur network manager see other wifi lan its obviously working somewhat a little.

1st thing i would do is make sure all ur wireless setting are correct.
 open a terminal window and type 
iwconfig.

if anything in there is outta place like ur ssid , wep key not present or anything,make sure ur fix that like so

iwconfig <interface> <option ie key: <ur key here>
etc etc
once everything looks fine bring it up

ifconfig ath0 up

try it

ping [www.google.com](www.google.com)

if u get a reply ur good to go if that doenst work try to see if the AP itself is seing you

ping 192.168.0.1 <or whatever ur AP addy is>

if u cant get a reply from ur AP make sure ur setting match what ur AP setting are.

from that let me know how it goes and we'll take u further.

basic stuff 1st. the problem may lay behind the k/b ... lol j/k

---

