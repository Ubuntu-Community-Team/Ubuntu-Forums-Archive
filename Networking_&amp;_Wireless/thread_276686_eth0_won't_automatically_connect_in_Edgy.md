---
title: "eth0 won't automatically connect in Edgy"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by anti-dan on 2006-10-13
I recently upgraded to Edgy Eft (because I'm mad and crazy and like living on the edge :p) and now my eth0 network won't start itself up on boot.

I can still open a terminal and type `ifup eth0` and it connects fine, or I could put it in my WM start up script or something, but does anybody know why it might not be doing it where it should in the boot cycle? Everything is there and accounted for in /etc/networking/interfaces - it's a static IP so there's no worry with dhcp or anything, and all the gateway and nameserver lines are there. I'm just confused :confused:

Thanks!

---

### Post by Iowan on 2006-10-13
I haven't done Edgy yet...
You might post the **/etc/networking/interfaces** file - just in case someone sees something.

---

### Post by justintime32 on 2006-10-13
Check your /etc/network/interfaces file. Make sure there is a line that says "auto eth0". If not, add it.

---

### Post by anti-dan on 2006-10-14
Ah brilliant, thanks :D Schoolboy error that one!

---

