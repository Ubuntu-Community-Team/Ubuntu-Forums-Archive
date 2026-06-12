---
title: "Network Interfaces"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by dbulante on 2007-07-20
I need help.  I inadvertently deleted my /etc/network/interfaces file, during my chat with a Dell technician.  Now, when I boot, it shows that the network manager fails.  However, I can still hop onto my wireless network (wifi), but my Google Desktop stopped working.

Can someone send me a default interfaces file which I can put back in the network folder?  Also, what would be the best way to get my Google desktop working?

Thanks for the assistance, my ubuntu friends.

---

### Post by bapoumba on 2007-07-20
Hello,
a little info is needed :)
what network card, DHCP or static IP, wireless I presume etc..

---

### Post by revilodraw on 2007-07-20
I also want a default /etc/network/interfaces file... 

thats all, no need to go into long detail, just the file... anyone?

---

### Post by bapoumba on 2007-07-20
This file is created during the install process according to the network cards that are detected and the drivers you use. So it is basically adapted to your own hardware configuration.
The minimal file will be this:
```
# The loopback network interface
auto lo
iface lo inet loopback
```
with no particular network set up.

---

