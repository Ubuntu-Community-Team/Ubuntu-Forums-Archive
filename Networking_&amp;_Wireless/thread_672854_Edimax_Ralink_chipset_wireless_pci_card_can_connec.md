---
title: "Edimax Ralink chipset wireless pci card can connect to WAN but not LAN"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by ilektron on 2008-01-20
Alright, so I have an Edimax wireless pci card with the ralink2561 something chipset.  Anyway, I have ubuntu gutsy, server edition installed on my computer.  I have it set up so that i can connect to my router, but all is not well in candy land.

I can browse the web using links, but I can't ping anything on my LAN, including the router.  Additionally, none of the the other computer on my network can ping the server.  I only get 'Host Unreachabled'.

I ran iptables -L and all the chains are accepted.  I'm stumped.  I'm using the drivers out of the box with ubuntu gutsy for the card.  If I run nmap localhost I get that all the ports needed are open.  I did have to change something to get it to connect at start up, but I can't remember what I changed.

Any ideas?  I'm stumped, and about ready to give up on it and sacrifice my MMC to use as a server.  Maybe I'll start doing that...

---

### Post by ilektron on 2008-01-20
Ok.  So all it took to get it working was post my problem.  How does that work?  I've been dealing with this problem for a week, and just decided to post on the forums.  Thank you forum gods for fixing it!

Note:  I may be back if the problem comes back...

---

