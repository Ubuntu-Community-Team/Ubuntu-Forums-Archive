---
title: "Getting vmware to see my w2k server"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by corbypete on 2008-04-05
I have loaded xp within vmware on ubuntu, however I cant access any of my windows shares?

I cant even ping the ip, just the ip of my router and get on the internet.

I set it up as NAT.

I want to get to my windows servers shares on the lan

Any ideas?

---

### Post by PilotJLR on 2008-04-05
Switch the network mode to Bridged, and then either give it a static IP address or renew the dhcp lease, and you should be all set.

---

