---
title: "Restrict bandwidth available to certain devices"
date: 2014-07-12
forum: Networking &amp; Wireless
---

### Post by Tristan_Williams on 2014-07-12
I have a home network with only one modem/router.

There is currently one device connected via ethernet cable, which is my main computer (running Xubuntu, not that it matters)
There are between 1 and 8 devices connected via WiFi at any given time. These devices are:
[LIST]
[*]Xbox 360 
[*]Between 1 and 4 iPod Touches 
[*]HP Compaq Laptop 
[*]Nintendo Wii 
[*]LG Android Phone 
[/LIST]

How can I restrict bandwidth available to each device. I want the main computer to have 1st priority, and (if possible) be able to take bandwidth from other devices if needed.
The main devices I want to restrict are the Xbox 360 (My brother kills us with XBL), and two of the iPod touches (kids don't need to restrict me from my work)

The only thing I can think of is to restrict per MAC address. But how would I give a certain percentage of bandwidth (when available) to each device, and adjust according to how much is being used and by which machines?

---

### Post by untrustytahr on 2014-07-13
What you want to implement is Traffic Shaping (TS) and Quality of Service (QoS).  Modern home routers have advanced this functionality in recent years, so it's best check what your router's capability is.  If it is limited/non-existant, you might want to get a new one or setup a firewall that runs pfSense (probably overkill though).

It does require a little bit of network knowledge though, but you can learn quite a bit with a basic google search.  Research it and come back if you have specific issues and questions.

---

