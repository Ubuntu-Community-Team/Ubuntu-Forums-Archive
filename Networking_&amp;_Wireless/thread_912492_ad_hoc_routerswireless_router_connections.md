---
title: "ad hoc routers/wireless router connections?"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by embolalia1187 on 2008-09-06
This is a question about wireless networking in general.
Is it possible to have a wireless connection between two routers?

The reason I ask is that ndiswrapper just won't work with the cards I have on hand. So I tried using my Xbox 360's external wireless adapter (which connects via Ethernet, not USB or PCI), and it works perfectly. I figure I can buy a new one for only a little more than a card (but with a lot less hassle). Then the thought occurred to me that I have a wireless router lying around that I'm not using. (And, being a Linux user, I want to find a free way out) So I was wondering if I could set up one router in my room with my Linux box, and the other downstairs with the Vi$ta machine and the DSL modem, and have the two connect without wires.

Oh, and the routers in question are a SMC Barricade 7004vwbr 802.11b, and a Netgear WGT624 v2 802.11g.

Thanks in advance!

---

### Post by bab1 on 2008-09-06
I believe you can use the barricade as a wireless AP (like an extender) to connect the two hosts. 

Ubuntu<=====>Barricade (AP mode)<=======NetGear<===>Vista

The Netgear is also the the gateway to the internet.

---

### Post by Qloor on 2008-09-07
Try connecting to your SMC Barricade via your broswer and setting it to Access Point mode. The SMC Barricade has an easy-to-use AP function.

---

### Post by embolalia1187 on 2008-09-07
I can't find an AP setting on either router. Both were bought because they were the cheapest available, so it doesn't surprise me. Thanks for the help, though!

---

