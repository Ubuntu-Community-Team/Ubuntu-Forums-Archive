---
title: "Ubuntu 14.04 LTS lost wireless connection after devices plugged into ethernet port"
date: 2017-06-15
forum: Networking &amp; Wireless
---

### Post by yz9202 on 2017-06-15
Hi,

I just configured the wireless connection on the Ubuntu 14.04 and it worked fine. I can remotely ssh onto it using its obtained IP address. 

However, when I connect a Velodyne Laserscanner to the machine via its ethernet port, the machine lost its wireless connection. I checked the router administration page and find the router received a request from the machine however didn't assign any IP address to it. I know this is the request from the machine by checking the MAC address.

I wonder why this happens. I am also curious about the structure here. The Laserscanner should share data with machine via this ethernet connection. And the machine should also be connected to the wireless router. This wireleasss router serves as an access point to a LAN (192.168.1.xxx). So are the Laserscanner and the Ubuntu machine belonging to this LAN or they form a subnet between them? I am a newbie to this networking stuff.

Thanks for any reply,
Yan

---

