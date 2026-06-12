---
title: "Cable unpluged, still on lan"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by latle on 2008-03-04
Hi,

When I've pulled out the network cable networmanager is still showing the lanicon, and I can't get the SSID-list to show.

I have restarted, reinstalled NM, conected to lan again, started and stoped wifi. 

When I run NM from terminal I get something like: Baddevice, ivalid or unitialized input device 169

Is it a way to fix this? Maybe to get a real fresh install og the networkmanager or something?

---

### Post by latle on 2008-03-05
Anyone?
Bumpetybump

---

### Post by Eiríkr on 2008-03-05
From numerous posts and other reading, NetworkManager appears to me to be a half-baked piece of software... but anyway.  Try running this in a terminal:
```
sudo /etc/init.d/networking restart
```
Let us know if that works, and if it doesn't, please paste in any error messages.  

Cheers,

Eiríkr

---

