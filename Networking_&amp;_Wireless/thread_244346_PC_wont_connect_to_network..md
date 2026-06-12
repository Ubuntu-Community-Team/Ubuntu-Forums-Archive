---
title: "PC wont connect to network."
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by djkp on 2006-08-26
Right, gotta big problem. 

At the min we have one pc connected wirelessly to a netgear router. However, the 2nd older computer does not connect at all. We have tried using a wireless adaptor, just says "aquiring network address" then come up with "limited or no connectivity", and we have used an ethernet cable to connect it and it still will not connect to the network.

Ive checked the router settings and its set up as a DCHP server, but i cant even ping the router from the 2nd computer even though its hard wired to it, ive checked loads of settings but cant find anything.

Its like something is stopping the pc communicating with the router. I turned off all firewalls but still no joy. The network card is apparently working correctly and i know the wireless adaptor was.

Please help me, im tearing my hair out trying to sort it!!

---

### Post by steve.horsley on 2006-08-26
Can you post the output from these commands?

ifconfig
sudo iwlist scan

---

