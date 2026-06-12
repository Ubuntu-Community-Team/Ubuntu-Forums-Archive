---
title: "Reconnection Problems"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by rpat on 2006-09-05
I hope someone can help with this problem. I had my desktop Ubuntu 6.06 LTS in another part of the house. It was connected by hardwire to a D-Link Wireless router, which was connected to a Linksys switch, which was connected to a Linksys broadband router. I moved the Ubuntu box and now I cannot connect to the network. I have re-set the router, the switch and the wireless router, however I still cannot get a WAN connection. I have noticed that the Network connection now uses LO instead of ETH0.
Can anyone assist with this please ?
Edit/Delete Message

---

### Post by tbonius on 2006-09-06
Sounds like eth0 isnt coming up upon boot.  What module does it need for the network interface?  What type of hardware/chipset is the ethernet card?

T

---

### Post by rpat on 2006-09-07
Tibonius : I tried DSL as a Live CD in the Ubuntu box and it did not obtain an internet connection either. I have a Cat-5 tester and  have checked the hardwire and the connection wire from the computer to the wall recepticle. The wiring checks out OK. I can only assume that because I am at the other end of my house, that I am having a connection problem. Is there a setting on net cards to boost the strength. Can you also tell me how to change the " multicasting settings " on the netcard.

---

