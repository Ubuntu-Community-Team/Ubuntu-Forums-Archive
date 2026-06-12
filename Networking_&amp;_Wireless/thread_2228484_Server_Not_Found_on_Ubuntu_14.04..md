---
title: "Server Not Found on Ubuntu 14.04."
date: 2014-06-07
forum: Networking &amp; Wireless
---

### Post by steven36 on 2014-06-07
Despite wasting my life in front of one nearly every hour of every single day, I don't know a whole lot about computers (specifically, how they work.) I installed Ubuntu 14.04 on my computer in hopes of having a faster alternative to Windows 7 on my aging Inspiron 580 (to its credit, it is.) When I was trying it out via Live DVD, the internet worked just fine, and as I type this on Windows 7, it works just fine. However, when I actually try to open up Firefox on Ubuntu after I installed it, and having both my wireless cards (don't ask me to explain) connected and working it tries to connect and says "server not found." I don't know why, and I don't know how to fix it; that's why I'm asking you guys.

---

### Post by squakie on 2014-06-07
If that wifi is internal:

lspci | grep Network

If external (USB in particular):

lsusb

Copy and paste the output back to a reply here so we can see the model and the chipset being used.  It's most likely just a missing driver and/or firmware that can be installed.

If you can hard wire to the router, try checking in additional drivers to see if a driver is available.

---

