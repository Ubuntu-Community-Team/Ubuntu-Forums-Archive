---
title: "K8NGM2-NBP onboard NIC not working"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by SteelRush on 2006-09-11
I recently upgraded my server machine from a Pentium 3 800MHz, to a Athlon 64 3200+.  I simply swapped the components out, and put the HDD into the new machine, and everything seems to work except the onboard LAN.

ifconfig shows only the local loopback adaptor.  What must I do to get the onboard NIC working?

---

### Post by SteelRush on 2006-09-11
I got it working! :D 

In /etc/iftab, erase the old references to the previous NIC, and it should be detected properly.

Hope this helps anyone with similar problems.

---

