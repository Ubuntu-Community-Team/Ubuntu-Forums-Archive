---
title: "Routing my internet connection through my Ubuntu machine"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by william_hunter on 2007-06-17
I have a question, and I am not sure how to find it via search, so I am going to lay it out there and see what everyone thinks. 

Here we go:

I want to route my internet connection through my Ubuntu machine, then out to my wireless router (which has been assigning IPs via DHCP). I have only one ethernet card in there right now, but I am planning on adding a second if I can make this work. Basically, I want to work around a problem wherein my router (USR 5461) occasionally crashes, breaking connections. I run the Ubuntu machine as a Neverwinter Nights server and as a webserver for my students, so I can't have it going offline, and I figure I can make it more stable by hardwiring it to the cable modem. Yes?

How do I go about doing something like this, if it is even possible?

---

### Post by Toitoine on 2007-06-17
It's possible and can be done easily with some tools.

Take a look at firestarter ([http://www.fs-security.com/]("http://www.fs-security.com/")), it's available in universe.

Here : [[Link]Documentation on connection sharing]("http://www.fs-security.com/docs/connection-sharing.php"), it seems to be what you want to do.

---

### Post by william_hunter on 2007-06-17
THats handy, as I already have firestarter on the machine to deal with the firewall. Thanks for the input.

---

