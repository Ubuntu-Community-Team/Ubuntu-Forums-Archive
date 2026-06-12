---
title: "Ubuntu 14.04 Server Network Stopped Working"
date: 2014-11-30
forum: Networking &amp; Wireless
---

### Post by sgharp on 2014-11-30
Hi Guys,

I have a 14.04 server that has lost network connectivity.  I can boot from a live CD and everything is fine so it is not hardware related.  The server hasn't been touched in days but became inaccessible to the network overnight.  I can't ping anything from the server and nothing on my local network can ping the server.  Ethtool doesn't report any problems with the NIC.

Ideas?

---

### Post by newbie-user on 2014-12-01
Rat chewed the ethernet cable? Switch port died? What does ifconfig say? Is the ip address statically or dynamically assigned?

---

### Post by sgharp on 2014-12-01
> **newbie-user said:**
> Rat chewed the ethernet cable? Switch port died? What does ifconfig say? Is the ip address statically or dynamically assigned?

ifconfig looked normal.  Strangely, after no configuration changes and several reboots, it started working again.  I'm baffled.  It's like the NIC just decided to take a day off.  Everything seems to be fine now.

Thanks for you reply....

---

