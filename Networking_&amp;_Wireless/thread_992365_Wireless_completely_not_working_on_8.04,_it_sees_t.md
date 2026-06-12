---
title: "Wireless completely not working on 8.04, it sees the network but can't connect"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by RyeGye24 on 2008-11-24
I've searched through alot of forums but still can't find anyone with a solution that works. I installed 8.04 and everything went smoothly, but I plugged in my wireless antenna (an old belkin one, its usb, not a card) and it can see the network but not connect. At first i thought it was the WPA cause the help file said something about needing the wpasupplicant package, but I turned security off completely and it still won't connect. Basically, if I'm in roaming mode, it will think its connected, the network manager will show the little signal strength bars, and I can ping the router even, or at least it thinks its pinging, but i can't reach any web pages or even ping any. I also tried manual configuration. With manual configuration, the network manager symbol just becomes the two computers, no little orange triangle, but I can't even ping the router. I know its not a DNS problem or a DHCP problem because I tried manually setting all the settings for those too. 
Anyone know what it could possibly be? My problem is too vague to just google ("wireless doesn't work on 8.04")

Edit: By the way I know this isn't a hardware issue because way back when i ran Ubuntu 6 on all the same hardware and the wireless worked fine.

Edit: Resolved. I was using a really old belkin wireless USB adapter and it turns out the new drivers that come preloaded on 8.04 can run it perfectly right up until it comes to actually connecting to a network. I just had to install the older drivers from belkin's website.

---

