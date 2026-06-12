---
title: "Using a Linux box as a router"
date: 2015-03-01
forum: Networking &amp; Wireless
---

### Post by PWMKzzJ on 2015-03-01
Im trying to get some help with a project Ive been thinking of for a while now. I have a network that has gotten to be pretty huge and we stream almost everything like Netflix, Hulu Plus, XBMC, etc. We also have an old Dell Poweredge 2950 acting as a media server. My problem is that we keep burning out routers with the heavy use. Im on my third one and it starting to act up as well. Im assuming that pushing dozens of Tb of data through the over the counter stuff is just asking too much.

I was thinking of building a small Linux box with a couple of good wifi cards and essentially building a router that can handle the kind of traffic were asking it to put up with. I counted and we have 20 devices on wifi in total and 2 on ethernet. Probably 12 on wifi simultaneously at any given time. What I was hoping to do is get 2 cards and set them as half duplex so one handles incoming data and the other handles outgoing. Does anyone have any experience in this? I've looked at the other threads and they are all using 1 NIC instead of 2.

---

### Post by houstonbofh on 2015-03-03
You are actually talking about two things; A router, and WiFi.  Right now you have both of them in one (cheap) box, and performance is poor.  The way businesses do it is to have a router and to have Access Points.  (And APs do burn out over time, but not as fast if they are business class)  I like the EnGenius EAP-350 and the EAP-600.  Very solid, and very high power.  They also support v-lan if needed.

What you are talking about doing with the split cards is a lot of complexity on top of cunsumer grade cards...

---

### Post by PWMKzzJ on 2015-03-03
Well after a lot of digging I found a cool project called pfsense that seems to do everything I would like. I was thinking of changing my setup to have the routing done by my server and only use AP's instead, but this seems to take care of everything really well. Now all I need to do is find a pair of really good wifi cards that support master mode and promiscuous mode.

---

### Post by PWMKzzJ on 2015-03-03
Everything I have found so far that is compatible with APmode is all 80211n, I can't find anything 802.11ac. Does anyone know of an ac chipset that is confirmed to run AP mode?

---

### Post by houstonbofh on 2015-03-03
I was a m0n0wall developer, and pfSense forked from them.  I am still friend with Chris, the guy behind pfSense, and we were talking last week.  If you look in both the m0n0wall mailing lists and the pfSense forums, everyone says get an AP.  On m0n0wall, I said it often.  (Note that m0n0wall retired on the 1st, and I am now the guy behind SmallWall.org a continuation of m0n0wall.  And I still say, "get an AP."

---

