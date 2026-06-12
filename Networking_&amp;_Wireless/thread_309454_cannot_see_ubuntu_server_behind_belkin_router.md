---
title: "cannot see ubuntu server behind belkin router"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by owarnes on 2006-11-29
I have a belkin router and I have setup ubuntu to run as a server with a static ip. I can reach the server locally through its ip address, but accessing it through the router from my fixed ip has so far defeated me.

I have set up the router to forward port 80 to the internal static ip of the server on my network, but it does not work???

I can access the router through the ip addresses when its in remote management mode, but so far I have no luck trying to get the port 80 requests through to my server.

](*,)

---

### Post by owarnes on 2006-11-30
I have tried a D-link router and encountered the same issue

---

### Post by owarnes on 2006-12-04
Well what do you know I have gone and fixed it!

Guess what it was working all along, the only thing was that I could not see that it was working all along because it can only be accessed from outside the LAN with the server on using the fixed IP - type the IP in otherwise and it won't be visible! you have to use the local IP for that!

---

