---
title: "proxy servers, help with my dumbness!"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by benjhi on 2008-08-27
this is probably not going to generate a lot of response, and I have yet to recieve any indication that it is possible on other forums, but i thought i'd post here just in case.

basically I have been trying to set my netgear DG384G wireless router/switch up as a proxy server on my halls network. the connection to the halls server is wireless only, and is MAC address restricted.

what I want to achieve is setting the MAC address on my switch to be the one that is registered on the halls firewall (i.e. that of my main PC's network card), and use this as a bridge to  switch's LAN allowing all my PC's to connect to the internet.

If this is not possible I am amenable to setting up one of my PPC's (runing ubuntu hardy) as a gateway to connect the my netgear LAN tot he outside world.

any help (or a quick NOES! if it can't be done :D) would be very greatly appreciated.

---

### Post by jimv on 2008-08-27
This might work for you:

[http://kbserver.netgear.com/kb_web_files/n101227.asp](http://kbserver.netgear.com/kb_web_files/n101227.asp)

The other idea that I have is that you could connect wirelessly to the Halls network with your PC, then bridge that wireless connection with your PC's ethernet and connect the PC to the router's WAN port.

If you're using Windows XP, it's as simple as turning on Internet Connection Sharing for your wireless connection.  In Ubuntu, it's a bit more difficult, but do-able.

EDIT:

I was just thinking that your router probably doesn't have the ability to connect to another wireless network as a client, so that first link likely won't work.  You'd need a router with a bit more capability, like a Linksys WRT54GL flashed with DD-WRT firmware.

---

### Post by benjhi on 2008-08-28
thanks jimv, that link was exactly what I was trying to do, the downside of it was that it did indeed confirm my inadequacy as an ameature net admin, seeing as it was child's play to implement!

however soimetimes you need a fresh pair of eyes to point out the obvious and for that i thank you! :D

---

