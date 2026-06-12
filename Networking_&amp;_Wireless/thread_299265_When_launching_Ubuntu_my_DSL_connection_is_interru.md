---
title: "When launching Ubuntu my DSL connection is interrupted"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by Robertjm on 2006-11-13
Hi all,

I've got a REALLY odd thing happening on my home network and I'm hoping some suggestions can be had here.

When I come home my Zyxel DSL modem has a solid connection light to my Earthlink DSL connection. Next I hit the power switch on my desktop computer and it starts to load Ubuntu. mid-way through all the services/programs being loaded the orange light that signifies a connection with Earthlink goes green or flashing green, which signifies NO connection with Earthlink. If I power cycle the modem, I get the solid orange light again.

I can repeat this at will. 

Is there a setting in Ubuntu I need to change so that it doesn't probe the DSL connection (my guess of what's happening)?

Here's my setup:
home computer connected to DLINK router, which is connected to the Zyxel modem, which goes directly to the Internet. I also have a Tivo unit hooked into the same DLink router and when it goes to download info from Tivo, it doesn't nock anything offline.

Thoughts?

Robert

---

### Post by stream303 on 2006-11-14
Most likely not Ubuntu related thank goodness. :)

I had a similar problem where my Netopia modem (from what I hear issued before the Zyxel's) wouldn't retain my username and password.  When I'd boot up, as soon as the startup process tried to access the ntp server, I'd lose my PPPoE and only much later would find my username and password gone.  Once I put them back into the modem, the pppoe light would come back on an things were fine.

I don't know why they do this, but I did leave the modem off for up to a half-hour at a time to try and get Earthlink to release the lease between them and the modem so the modem would get a new address.  This seemed to work, but whenever I lose pppoe, I've always had to manually go back into the modem setup page and enter my info again.

Dunno' why this is...note: ever since I've gone to using IPV4 only on my local stuff, this happens much less frequently - not really sure if this has anything to do with it.

---

