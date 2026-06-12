---
title: "Network settings doesn't work with ubuntu server under vbox!"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-08-03
I installed ubuntu server 10.04 under vbox virtual machine 3.2.0, what exactly i need is how to setup two network cards on the ubuntu server, one connected to internet while the other is attended to share the internet to all network "virtually",
 so here's my settings in vbox :

adapter1: bridge "connected to the router"
adapter2: host-only  "connected to the network"

but when i typed ifconfig command on the server i don't see any connection, look to the image below:

---

### Post by OriginalName on 2010-08-04
Have you tried installing the "guest additions" - Had a similar problem with Win7 & it fixed that...

Just a guess though...

---

