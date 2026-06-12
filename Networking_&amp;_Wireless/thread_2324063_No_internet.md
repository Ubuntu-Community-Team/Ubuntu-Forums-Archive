---
title: "No internet"
date: 2016-05-10
forum: Networking &amp; Wireless
---

### Post by daniel_Miedema on 2016-05-10
Hello,
i installed ubuntu 16.04 LTS on my lenovo thinkpad (laptop), but i cannot get internet access. When connecting either by wire or by Wifi it recognizes the network but cannot finish connecting. A message saying that my laptop disconnects keeps popping up. In other related threads i saw that this info was needed:

nmcli general status
STATE CONNECTIVITY WIFI-HW WIFI WWAN-HW WWAN
connecting none enabled enabled enabled enabled

hopefully someone can help me

---

### Post by Bucky Ball on 2016-05-10
*Thread moved to **Networking & Wireless**.*

Welcome. Although you're a newcomer, people will take that into account and you'll have a better chance of support here. ;)

Better is the info from the wirelessinfo script which you'll find linked in my signature at the bottom of this post. Please run that and post the output here between code tags (for how to use code tags, see the green link in my signature). 

In the meantime, this will give some details:

```
sudo lshw -C network
```

Please post the output between code tags. Thanks.

---

