---
title: "Samba using 25KB/sec with no connections. Is this normal?"
date: 2014-07-03
forum: Networking &amp; Wireless
---

### Post by danny2368 on 2014-07-03
In gnome-system-monitor, I noticed a lot of network activity, when I wasn't downloading anything.

I downloaded nethogs. It showed smbd is sending out 25KB/sec while receiving <1KB/sec. Is this normal? Is my system corrupted? This seems like a lot of traffic when there are no connections.

BTW, is there anyway to change my username, so it is not derived from my email address?

---

### Post by sandyd on 2014-07-03
> **danielw150 said:**
> In gnome-system-monitor, I noticed a lot of network activity, when I wasn't downloading anything.

I downloaded nethogs. It showed smbd is sending out 25KB/sec while receiving <1KB/sec. Is this normal? Is my system corrupted? This seems like a lot of traffic when there are no connections.
smbd is samba, the equivilent to windows file sharing, so you may see some traffic if it is scanning the network for other computers.

meanwhile...
> **danielw150 said:**
> 
BTW, is there anyway to change my username, so it is not derived from my email address?
You can post in the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123") to change your username.

---

### Post by QIII on 2014-07-03
Hello!

That looks to me like normal broadcasting stuff between the server and any clients on the network. 

Somewhat like:
"Hey, guys!  I'm still here!"
"OK.  Thanks!"

You can modify your configuration to cut down on the broadcasts, but that is a piddlingly small bit of traffic compared to the risk on messing things up.

Cheers!

---

