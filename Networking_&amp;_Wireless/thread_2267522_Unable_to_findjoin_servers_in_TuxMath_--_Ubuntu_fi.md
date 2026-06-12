---
title: "Unable to find/join servers in TuxMath -- Ubuntu firewall/networking issue?"
date: 2015-03-02
forum: Networking &amp; Wireless
---

### Post by Christopher_Taylor on 2015-03-02
I recently dug a couple of old computers out of my school's IT storeroom. I had carte blanche to do with them as I pleased so I ditched Win Vista and replaced it with Edubuntu. I connected the two machines with a length of crossover cable and set up an ethernet network: I used ifconfig to get the MAC Address. One machine I set to auto (DHCP). The other I set to draw its IP details, etc from the other machine. The two machines were able to ping each other. I then entered TuxMath and tried to get one machine to host a game and the other to join in. The second machine could not find any servers to join. I dug around (admittedly not particularly deeply) online to see if there was some kind of known issue with TuxMath that might explain what was going on and couldn't find anything, aside from someone running into issues that were solved by "sudo ufw disable" (the machines aren't on the school network/connected to the internet). Disabling this firewall didn't do anything to resolve my issue. I'm yet to try, say, sharing directories or playing other games via LAN.

Are there any obvious (well, to an experienced user--not to a chickenhead like me) explanations for why this doesn't just ... work?

---

