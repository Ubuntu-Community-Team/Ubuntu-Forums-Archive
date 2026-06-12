---
title: "need router/networking recommendations"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by atarileaf on 2007-10-12
Hello all. I recently got a new computer which has XP on it and my old computer is an XP/Ubuntu 7.04 dual boot. 

So now that I have two machines, I'm looking at networking them together. I know I need a router and I guess wireless cards. What I don't know is if I need wireless cards for both machines or just the second machine (since I'm guessing the one machine could plug into the router or modem directly)

I noticed best buy has a  D-Link Xtreme G 802.11g Wireless Router (DI-624) on sale and was wondering if it will work well under Ubuntu. 

I need opinions on this, what kind of wireless card(s) to get and I need to get pointed in the direction of a good tutorial about hooking this stuff up.

I'm fairly adept with computers and Windows but Ubuntu is fairly new to me and I know next to nothing about networking so any advice or recommendations would be appreciated.

Thanks

---

### Post by bvmou on 2007-10-12
As far as routers, most anything will work as you would expect it to.  I once came across a web gui that preferred Explorer but that is the exception.  If you want a more linuxy experience, and something that highlights the advantages of open source, find something compatible with the free dd-wrt and/or OpenWRT embedded software, it will amaze you how much more you can do with your router and wireless AP.  There are very cost effective options there, check the d-link to be sure.  Not everything that claims to be supported is equally easy so check the device-specific instructions first on the dd-wrt wiki.  My personal favorite is the Buffalo WHR-HP-G54, it is like $60, or $50 Canadian :) and has excellent range, although flasing the firmware is a bit of a hack.  On wireless, as a rule broadcom chipsets will make you miserable, though you can always get them working; intel chipsets are well supported in linux; Atheros wireless has some great free drivers, and so on.  Do your best to find out what works before hand, and when in doubt that means Intel's integrated stuff, which may or may not help you. For networking with Windows machines, the main package is called Samba, and it can be as simple or sophisticated as you want.  Good luck and enjoy...

---

### Post by steveneddy on 2007-10-12
Linksys is east to operate and affordable.

---

