---
title: "Ubuntu Server: Can't connect to network via wifi"
date: 2015-01-24
forum: Networking &amp; Wireless
---

### Post by rob116 on 2015-01-24
hi, 

Apologies if this has been posted before but I've had a quickly look (and google) and found no solution. 

I'm new to the whole Ubuntu thing having never really had chance to try it out before, so my understanding of things may not be that great. 

I've recently installed Ubuntu(server) onto an old laptop with the idea of playing around with it and see how things work. I got it all installed no problem and everything seemed to be going well. Unfortunately I now need to connect the the network so that I can access the internet for updates/downloads etc. Its really not practical for me to use a wired connection and since the laptop has wifi I figured just go with that. This is where the problems started, firstly my wireless connection was disabled and the switch on the laptop would do nothing, google helped me fix this but it still won't connect.* iwlist* *scan* brings up the following:

lo - interface doesn't support scanning 

Vibr0 - interface doesn't support scanning 

**wlan0 - No scan results **

p1p1 - interface doesn't support scanning 

So i guess that the lo, vibr0 & p1p1 are something else that I dont need right now? But wlan0 is the wireless connection and for some reason its not returning any results. I know that this isn't a fault on the side of the router and when I was last using this laptop a few weeks ago with Windows the wireless was working fine and theres been no reason for it to have broken since, and the drivers seem to be installed. So that leads me to think that the issue must be something to do with the configuration of the network/wireless settings or just my incompetence. Anyone have any ideas? Could this be a case of the hardware not being compatible with Ubuntu or am I just missing something really simple?

---

### Post by mörgæs on 2015-01-24
Hi, welcome to the fora.

It's best to use a wired connection during install and while updating the first time. When that is done please read the sticky note here in Networking.

---

### Post by rob116 on 2015-01-25
Ok, thanks for your help.

---

