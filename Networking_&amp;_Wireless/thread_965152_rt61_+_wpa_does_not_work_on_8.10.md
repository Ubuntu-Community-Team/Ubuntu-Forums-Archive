---
title: "rt61 + wpa does not work on 8.10"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by rascal on 2008-10-31
Hi!

I'm trying to get my Ralink rt61 based d-link card to work on 8.10.
On 8.04 and before that I have always compiled my own rt61-driver from serialmonkey. For some reason it does not work anymore. I can't connect to wpa network but I can connect to an unsecured one. When network-manager asks for a network password, I can only select WEP.

Both the rt61 (from serialmonkey) and rt61pci (8.10 default) do not work. How can I fix it?

Thanks

---

### Post by rascal on 2008-11-01
The make/model of the card is D-Link AirPlus G DWL-G510 rev. C.

---

### Post by eldragon on 2008-11-01
if your rt61 is anything like my rt73. you will have to remove the network manager, since it will not work with the serialmonkey legacy drivers. instead. install rutilt from the repositories and use it to configure your networks.

---

