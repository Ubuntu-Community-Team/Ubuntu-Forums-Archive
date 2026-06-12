---
title: "No network/internet for HP pavilion a250n"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by kendall14 on 2008-09-17
HI, I'm pretty much a noob to linux here so please try to be patient with me. I recently installed ubuntu 8.04 on my hp pavilion a250n. Now the problem is that I can't seem to get my network to work. I think it picks the network card up (see the attached picture) but it doesn't seem to want to work. I tried checking the router, a netgear WGR614v9, on a different computer but the router doesn't see it and the light for that port is not light on it or the computer, it's a wired network. So anyone knows what gives?:(

---

### Post by Iowan on 2008-09-17
The avahi address means DHCP didn't work.  The 169.x.x.x IP address probably makes the machine pretty lonesome in it's own subnet. I've seen several similar threads recently... but haven't found a good solution. One thing to try - if "roaming" is checked, uncheck it and restart networking (**sudo /etc/init.d/networking restart**)

---

### Post by kendall14 on 2008-09-17
N luck, still no internet or network. Though tthe oddd thing is that when I got back into windows the LAN was disable, I don't believe I disabled it.:confused:

---

### Post by kendall14 on 2008-09-23
The problem was something to do with ubuntu not liking my integrated nic. I poped in a pci nic and it worked fine. Would like to know if any one does know how to fix that but it's ok now.:guitar:

---

### Post by Iowan on 2008-09-23
Possibly a driver issue on built-in NIC (which I can't help with). Good luck.

---

