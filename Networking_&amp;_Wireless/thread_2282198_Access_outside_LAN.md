---
title: "Access outside LAN"
date: 2015-06-12
forum: Networking &amp; Wireless
---

### Post by kurt13 on 2015-06-12
Hello fellow ubuntu community!

I have a ubuntu server running at my home. Currently I can access the server via any computer that is connected to my LAN.

My goal is to be able to access my server outside the LAN. For example, running a website server.

The problem is that I live in a condo complex with over 300 condos who all share the same connection. From what I have been able to gather, the condo building has a router that assigned local ips for each device withing my building and each condo has their own external ip. I don't have access to the router setting because the ISP manages that.

The way i have my WiFi network inside my condo is: A WiFi router connected to the wall Ethernet socket. This WiFi router is set to bridge mode only. Any other setting will not work, this is due to the fact that the building router is doing all the DHCP and NAT. All other devices are connected wirelessly to the WiFI router. Within my LAN (the WiFi network inside my condo) i can access any device. When outside my WiFi network I cannot access anything (or at least I have not been able to).

To the best of my knowledge, every device connected to my WiFi network receives a static ip but every device inside my WiFi network has the same external ip. 
How will I be able to direct any traffic that is assigned to my external ip to the specific device (in this case the server) inside my WiFi network.

I hope this isn't too confusing... All these multiple layers are hard to explain.

Thanks for your time.

---

### Post by TheFu on 2015-06-15
If your router doesn't have a real, public IP, then you will never be able to initiate a connection from the outside world. Sorry.  If the WAN IP on your router is 10.x.x.x/8 or 172.16.x.x/16 or 192.168.x.x/....  then you are done. [https://en.wikipedia.org/wiki/Private_network](https://en.wikipedia.org/wiki/Private_network) should help explain it. Those IPs are NOT routed over the internet - therefore anyone outside the LAN (in your condo) cannot attempt to access those IPs from a cafe or work or over cell data networks, etc...

Wired or wifi - doesn't matter.

---

