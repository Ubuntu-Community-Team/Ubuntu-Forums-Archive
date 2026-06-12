---
title: "Wireless Bridge"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by bd_thompson on 2008-10-31
This is not Ubuntu specific, but I know there are wizards here. 

I currently have a wireless network at home with 5 computers and 2 printers attached both wired and wireless.

I want to set up a mini network in my barn/workshop.  I would like to set it up with a wireless bridge to the house.  

Question:  Do I need two additional wireless routers set up as bridge devices?  If so, does the one in my office attach as a wired device behind the current router?

Thanks. 

Dave Thompson

---

### Post by helgman on 2008-10-31
Hello!

That's a sweeping question but I'll give you half an answer ... ;-)

Radio (as you probably know) uses frequency for communication. Too many clients communicating on the same frequency is never good, and the wifi-network is a shared media - only one client can/should communicate at any given time.

So ...

... if you are going to use wireless both in your house and in your barn and in between (connecting the two network) then I guess there are a few ways of doing it:

1. I've set up Ad Hoc/mesh wireless network where the APs communicates at one frequency (in that case they actually used 802.11a, the 5GHz spectrum) and then the clients connected to the APs on another (on some 2.5GHz channel). This setup requires APs that can work on two frequencys simultaneously. As long as the APs use different "non overlapping" channels for "backbone" communication and "access" communication, you should be home free.

2. I'm going to do a setup that is one ordinary home router ADSL/AP all-in-one (from Netgear I think) that is connected in a main building and then I'm going to use a Linksys with DD-WRT as a "client" that connects to that AP from a different building. But in that setup the client will be wired to the Linksys.

Other factors are distance and what in between the antennas of the APs etcetera. Maybe you'd like to use external antennas attached to the outside of the buildings, maybe even directional for "maximum" quality. Or you might use an Ubuntu box with two wireless NICs in the barn - one for connecting to the AP and on for serving the connection to other clients in the barn ...

... the possibilities are (almost) endless.

I hope this can be of some help.

Regards,
Helgman

---

