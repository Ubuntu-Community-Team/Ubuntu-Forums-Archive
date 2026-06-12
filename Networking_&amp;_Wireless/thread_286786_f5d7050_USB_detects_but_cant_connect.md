---
title: "f5d7050 USB detects but cant connect"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by warriorscot on 2006-10-28
Hi, had a friend who got his wireless sorted here so I figured I would try here as well. I'm fairly new to using Linux at least as a permanent OS on my system but I know my way around I also use Unix at uni so I'm fairly proficient these days I'm not just cutting and pasting all the time from how tos, still do that allot of the time though I always spell something wrong.

I have one f5d7050 USB probably a version 1000, this I want to connect to the Belkin wireless G router it came with I also have a PCI version but its broken and I haven't sent it back yet. 

Drivers that are on the installation disk are rt2500 windows and in Vista x64 its rt2500x64 drivers that are working fine. So i know the chipset is the ralink, now initially i tried Ndiswrapper it was a no go got to a point where i could see networks in network but again couldn't connect. Then i tried the rt2500 and rt2570 drivers from serialmonkey. i install those and wifiradar and wireless tools can both detect networks both secured and unsecured but cant connect. However with serial monkey driver no networks are listed in networks to get the card enabled in there i had to type the SSID in myself with ndiswrapper the networks showed up in the drop down, still wouldn't connect though.

Its strange everything appears OK the card is detected rausb0 its Mac address shows up correctly and when I use wifiradar it flashes like it wants to give me an epileptic fit. But no connection and no traffic other than it detecting the SSID.

I'm at a loss, I've done all of this on 6.06, 6.10RC, and now 6.10 final its driving me insane.Can anyone think of anything I have missed, had this problem before, I'm really at my wits end and I really need this so I can do my programming work at home, as gfortran is the only decent free compiler, its also the only thing stopping me using Ubuntu as my main OS and my other is Vista RC2 so my computer is really driving me nuts right now

---

