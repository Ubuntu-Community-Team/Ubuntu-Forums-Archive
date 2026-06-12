---
title: "Hub for a LAN?"
date: 2005-11-17
forum: Networking &amp; Wireless
---

### Post by drummer on 2005-11-17
Hi there, This question isn't exactly Ubuntu related, but is nertwork related, so I thought this is the place to post it (Admins please move it if you think otherwise).

Some friends and I are having a LAN party in a couple weeks and so far all we have for a larger scale network is a 10mbps 16 ports hub. I'm guessing we'd have maybe 10-15 players, so just a small party. 

My question is will the hub be able to support the constant network traffic of 10+ gaming machines? The bandwidth is enough (10000kbps split 16 ways with 70% efficiency, about 54kBps each) but what's the ping going to be like and are we likely to experience any lag? I'm a noob when it comes to networking and the like, so any help and/or info is greatly appreciated.

Many thanks, Owen.

---

### Post by drummer on 2005-11-18
bump

---

### Post by darth_vector on 2005-11-18
hubs are crap. they basically broadcast every transmission coming into them to every device on the lan. so if you have a 100Mbps hub with 5 clients, your maximum data rate is 20Mbps (because the other four channels are receiving at 20Mbps each). when more than one person sends data, everything goes to hell.

i would recommend that you get a network switch. they are slightly more expensive, but they isolate transmission domains. this means that any two clients can potentially communicate at link speed (100Mbps, in the example above), and you get communications at the kinds of speeds you would expect. they are far superior.

---

### Post by drummer on 2005-11-18
Thanks for the reply. Would a 10mbps switch be enough? We'd like to spend as little money as possible and I could probably get an old one for not much. I know 100mbps would certainly be better (the bigger the better :p), but do you think there'd still be no lag / low ping even with the lower bandwidth?

---

### Post by darth_vector on 2005-11-18
10Mbps is heaps. mind you, with gigabit ethernet (1000Mbps) the 100Mbps switches have gone down in price quite substantially.

---

