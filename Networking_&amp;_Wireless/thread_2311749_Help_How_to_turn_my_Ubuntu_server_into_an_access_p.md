---
title: "Help: How to turn my Ubuntu server into an access point without unnecessary traffic"
date: 2016-01-29
forum: Networking &amp; Wireless
---

### Post by petwri on 2016-01-29
Hello!

I have my Ubuntu 15.10 server connected to my FritzBox WLAN router via 100MBit LAN which then gets me me online. I now use the FritzBox WIFI for all my devices. But my Ubuntu server has an AC WLAN card, which therefore should replace the much slower FritzBox WLAN. Furthermore, an AVR is connected to the FritzBox via LAN to have access to the WWW:

   WWW
<------------->
 FritzBox (provides DHCP & WLAN & DSL) 
<-----LAN----> Server
                                                                                                  <-----LAN----> AVR
                                                                                                     <----WLAN---> other devices

What I want is the following setup:

   WWW
<------------->
FritzBox (provides DHCP & DSL)
<-----LAN----> Server (provides WLAN) <-----WLAN----> other devices
                                                                                         <-----LAN----> AVR
                                                                                           

My question now: what, besides the configuration of hostapd on my Server, would I need to get this setup working, so that I DONT have any unnecessary traffic from a device that accesses something on the Server via the FritzBox? Imagine my tablet accesses a video stored on the server, I don't want any traffic redirection to the FritzBox.

Can the FB still provide the DHCP server? Would that result in any duplicate or circular traffic? Is it preferable to have a DHCP server running on my Server device?

Help and input would be highly appreciated.

Thanks!

---

