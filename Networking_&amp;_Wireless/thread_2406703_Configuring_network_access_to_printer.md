---
title: "Configuring network access to printer"
date: 2018-11-24
forum: Networking &amp; Wireless
---

### Post by kobras on 2018-11-24
Hi folks,
I have a bit complex setup of network at my home.

So I have router1 through which I'm connected to the provider. I wasn't satisfied with WiFi power capabilities of that device, so I have bought a second router and connected it to the first one, so now I'm using router1 for connecting just my workstation, router2 is used for WiFi at my home. Also I have an Epson printer that is connected to the WiFi network. All my devices that are connected to the WiFi can print without any problems (phones, laptop), but I just can't access any device connected to the router2 from devices connected to router1. I can't even pint router2 from my workstation unless I completely disable firewall in my router. Is it possible to make my printer visible for devices connected directly to router1?

Here is a list of IP address:

Router1: 192.168.0.1
Workstation: 192:168:0:248
Router2 (from router1 point of view): 192.168.0.87

Router2: 192.168.1.1
Printer: 192.168.1.94

Thanks in advance.

---

### Post by TheFu on 2018-11-24
Nope.
If you had purchased a wifi-AP, like a Ubiquiti LR AP,  usually for $80-$120. then it could have been placed where you need it thanks to PoE and provided huge coverage.  Plus, if you need more APs, they can be daisy chained to cover your entire compound like a grid, with centralized management using an Android App or a Java program running during the times you need to setup any of the APs.

But if you don't want to trust the ISP router, and I don't think you should, then you should connect all your computers to your router and effectively ignore the routing from the ISP completely. Many have a "bridge mode" which passes the public IP to an internal system - like your personal router without molestation.

But none of this is really connected to Linux/Ubuntu.

Let me assure you, your network setup isn't complex at all.

---

### Post by SeijiSensei on 2018-11-25
I have the setup TheFu describes. All my devices share one router which is connected to the "LAN" side of my provider's router.

It might be possible to resolve this with static routing, but you would need to manage the provider's router. "Daisy-chaining" the routers is a simpler solution.

---

