---
title: "torrent"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by nuddelmaddin on 2007-06-18
azureus (and other torrent-apps) just build up very few connections, perhaps 1-5, even if the tracker knows about 1000seeds.... anyone an idea why? under winxp using utorrent it works all fine. using ubunut 7.04

---

### Post by dfreer on 2007-06-18
Try manually opening the ports on your router if you haven't already done so.
I find most windows bittorrent clients support UPnP (I think that is the correct acronym), basically it communicates with your router and tells it to open such and such ports for it. It then seems that this doesn't work for the linux clients, requiring you to open them manually. Just my experience :D

---

### Post by nuddelmaddin on 2007-06-18
thanks, but i did this before, doesn't solve the probleme. and yes, it's called upnp port forwarding ;-)

---

### Post by dfreer on 2007-06-18
You might wanna try disabling IPv6 in the kernel, see if it is simply a problem with that. I dunno, I know that torrentflux on a dedicated server with ports forwarded works great for me (I think torrentflux uses bittornado to actually download the files). Sorry I wasn't much of a help :(

---

### Post by Peverel on 2007-06-19
Transmission in 7.04 has the option to enable UPnP... Works good for me...

---

