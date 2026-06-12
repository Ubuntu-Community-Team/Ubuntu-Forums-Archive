---
title: "Network Question"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by TuckLive on 2008-03-18
I'm trying to set up a box to sniff the traffic on my home network, but I'm having problems.  My network topology goes like this:  internet to cable modem to hub to wireless router.

I want to run the sniffer off the hub.  I have 3 computers connected to my wireless router (2 wired, 1 wireless) that I want to sniff.  When I connect my Ubuntu box to my hub it will not establish a connection.  

Any suggestions?  Can this be done?

I hope I have explained my situation enough.

---

### Post by erwall on 2008-03-18
> **TuckLive said:**
> I'm trying to set up a box to sniff the traffic on my home network, but I'm having problems.  My network topology goes like this:  internet to cable modem to hub to wireless router.

I want to run the sniffer off the hub.  I have 3 computers connected to my wireless router (2 wired, 1 wireless) that I want to sniff.  When I connect my Ubuntu box to my hub it will not establish a connection.  

Any suggestions?  Can this be done?

I hope I have explained my situation enough.

Your cable modem will only hand out one address, and that's likely the outside interface of the router right now.

---

### Post by TuckLive on 2008-03-18
ok my computers that are connected to the wireless router all have internet connection now with internal ip's.  Is their a way I can give my sniffer pc an internal ip also?  The hub is in front of the wireless router, but behind the cable router.

---

### Post by tlink on 2008-03-18
You'll need to put the sniffer box on the internal side of the router, otherwise it won't give you an internal ip.  

I guess you COULD set up some kind of vpn or tunnel or "wan" kind of thing, but I wouldn't know how to do that, and its really the difficult way of going about it.  More than likely wouldn't let you sniff the traffic on your home network anyway.

---

