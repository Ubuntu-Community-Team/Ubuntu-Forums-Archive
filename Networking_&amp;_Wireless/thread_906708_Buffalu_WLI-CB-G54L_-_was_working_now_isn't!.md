---
title: "Buffalu WLI-CB-G54L - was working now isn't!"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by djm-uk on 2008-08-31
A customer has Hardy installed on a Laptop - this was working using the above PCMCIA card with no problems.  At some point in the last month or so it has stopped working. 

lspci reports the card as "Texas Instruments ACX 111 54Mbs Wireless Interface"

I am pretty sure that this was set up with a native driver as I didn't fancy the hassle of using ndiswrapper :)

We now get a kernel panic whenever we try and connect to the (WEP) network. I have tried a generic USB dongle (Zydas WLA-54L WiFi) and that works fine!!

Are there any recent updates that may have broken support for this card?

I'm going to try without WEP but that means rebooting the router so I will post this first!!

David

---

### Post by djm-uk on 2008-08-31
Tried without WEP - doesn't connect but doesn't panic either! 

I wonder if the card has died...  Tried an (old) lucent card which reports as "hermes 1" & that worked fine...

If I have to get the Cu a new card can anyone recommend one that plugs & plays...?

Thanks

David

---

