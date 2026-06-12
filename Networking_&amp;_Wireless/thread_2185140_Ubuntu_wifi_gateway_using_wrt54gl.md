---
title: "Ubuntu wifi gateway using wrt54gl"
date: 2013-11-01
forum: Networking &amp; Wireless
---

### Post by martien_b on 2013-11-01
Hello,

I've a problem I would like to setup a wifi network at home for my guests. I would like it to be separate from my home network.

The way I want to accompish this is by using my ubuntu-box with dual Lan and a old Linksys wrt54gl.

[guest pc using wifi] -> [wrt54gl] -> [ubuntu pc] -> [home network] -> [ISP]

I understand there are easer ways but I like to experiment with this kind of setup.

I triend google-ing but the problem is I dont really know what the correct termenology is for this kind of setup. I hope someone can stear me in the right direction!

---

### Post by tgalati4 on 2013-11-01
See if your wrt54gl will support [http://dd-wrt.com](http://dd-wrt.com).  If so, install it and look through the split network capabilities.  You should be able to accomplish this through the router itself.  Otherwise, new routers generally have "guest" network capability.  I have not set one up, so I don't know if they provide a decent level of security to the existing LAN.

I'm not sure why you would need the Ubuntu PC with a dual network card, unless you want to run an additional firewall.  This will result in slower network response times and your guests complaining.  

I would be more concerned about the toilet network.  Slow response times and packet rejection have immediate effect.

---

### Post by martien_b on 2013-11-01
Thanks for the reply. I've installed dd-wrt on the router but this is not exactly wat I want. I do want to add an additional (better contrable) firewall and I also want to be able to monitor the amounts of traffic on the network. Just to be sure there are no unwanted 'guests' using my accespoint.

---

### Post by tgalati4 on 2013-11-01
Tomato firmware has some extensive bandwidth monitoring:  [http://www.polarcloud.com/v/scbwm.htm](http://www.polarcloud.com/v/scbwm.htm)

---

### Post by martien_b on 2013-11-01
I do appreciate you trying to come up with simpler approach, but I would really like to try this using a Ubuntu box as gateway. I want learn more about setting up gateways and monitoring traffic.

I did found some articles about setting up a hotspot (gateway) but they all depend on a Wifi network card. Instead I would like to use my wrt54gl router, connecting one NIC on the WAN side of the router and the other NIC on my homenetwork.

Does anyone know if this is possible?

---

### Post by tgalati4 on 2013-11-01
So you would use network bridging to handle the NIC going into and out of the Ubuntu box.  [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

You would probably use *iptables* to set up basic routing and some sort of firewall:  [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

I've seen web blogs and posts on these forums with experiences on how to set up an Ubuntu router.  Keep searching.

Maybe:  [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

Or:  [http://askubuntu.com/questions/111381/how-to-make-an-internet-server-as-firewall-using-ubuntu-11-10](http://askubuntu.com/questions/111381/how-to-make-an-internet-server-as-firewall-using-ubuntu-11-10)

---

