---
title: "Bridge question"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by lespaul_rentals on 2008-01-17
I have a few quick questions about bridging two LAN cards together.  I know how to do it, but I need to know about some issues I might have.  I have Ubuntu on my main computer/server and this has two LAN cards in it.  eth1 will be plugged into the main router, the way I normally plug into my network.  eth0, the secondary network card, is what I will send network access out.

My questions are as follows:

1. The following setup should logically work, correct?

Main router --> eth1 |--| eth0 --> Wireless router --> End device

2. Will I still have network access just like normal (other than the obvious bandwidth sharing if someone else is connected)?

Basically, the goal I have in mind is a prototype honeypot.  For example, if some cracker connects to a WLAN called "Anonymous Internet," what does the traffic look like?  What kind of packets will be sent through the network?  Honeypots have always fascinated me, so I decided this would be a good after-school project.

---

### Post by Mithrilhall on 2008-01-18
Internet <---> Main Router <---> eth1 - Computer - eth0 <---> Wireless Router <---> Other stuff

That should work fine. Your wireless router should pull it's information from the Main Router.

---

