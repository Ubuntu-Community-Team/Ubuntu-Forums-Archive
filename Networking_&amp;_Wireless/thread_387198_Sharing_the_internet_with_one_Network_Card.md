---
title: "Sharing the internet with one Network Card"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by Frenzy-br on 2007-03-18
i saw alot of posts about sharing the net on ubuntu with 2 cards, but i need to find out how to do it with one card... i have broadband here and when i used XP it all worked fine but now me and my mate have both installed Linux, i have gnome and he has KDE, and to be honest we don't know much about Linux i managed to get the Internet running on mine and when he had it on his we was able to share it with me but not to the pcs that have win 98 .. but now that im being the router i cant seem to manage it ... 
this is the set up we have

Dlink modem>> switch >> me >> Everyone else, 

i need to find out how to share it and be able to set NAT rules so i can open ports for torrent dl...

i greatly apreciate any help...

---

### Post by Austin_KW on 2007-03-18
Why not just connect "everyone else" to the switch? Everynone can just set their default route to the Dlink?

---

### Post by koenn on 2007-03-18
> **Austin_KW said:**
> Why not just connect "everyone else" to the switch? Everynone can just set their default route to the Dlink?
This would work of the "Dlink" is a router and can do NAT. If it's just a modem (and nothing else), something else would have to do the routing and NATing, eg the "me".
So you'd have to figure out whether that DLink is a NAT router or not.

---

### Post by Frenzy-br on 2007-03-18
it is and it would work fine like that but theres only one problem.. it wont loopback and everyone here except me is adicted to warcraft and play it online all day long and the only way some one from this house can connect to some one from this house is to have one of teh pc, being the router...

---

