---
title: "networked devices and firewall"
date: 2020-11-12
forum: Networking &amp; Wireless
---

### Post by bradhaack on 2020-11-12
I'm trying to wrap my head around how networked devices, like bulbs, plugs, water heaters...   get access.  Or more precisely how do I get access to the device when I'm not on my local network.  Since I don't have any ports open, my router should discard any incoming traffic that isn't a response to something inside my network.  I have a rough concept that the smart device (in my case, a Moen Flo, and a GE water heater) send out regular signals to their host (Eufy, GE, Moen or whoever), requesting a response.   Does this sound about right?

---

### Post by TheFu on 2020-11-13
Yep, probably close enough.

A bunch of those makers use 3rd party pseudo-vpn tools to simplify access. The by-product of that impacts LAN security.  The FBI says all those types of devices need to be on different networks than the systems we trust.  A link: 
[https://www.zdnet.com/article/fbi-recommends-that-you-keep-your-iot-devices-on-a-separate-network/](https://www.zdnet.com/article/fbi-recommends-that-you-keep-your-iot-devices-on-a-separate-network/)

---

