---
title: "Connection Dropping"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by rsh on 2008-01-07
I have been running Gutsy since the release and ran into my first network problem.  I am running in w/ roaming mode/dhcp enabled and my connection to the network drops after about 25 seconds.  My gateway (et all) is a 2wire model and it seems to work with my other components (laptop running Kanotix, Ps3, Xbox360, Wii).  

The only thing I have done today is uninstall MythTV (wasn't using it).  I used Synaptic to remove it.  

Connection returns if I:

```

sudo ifconfig eth0 down
ifconfig eth0 up

```

But once I reach the dreaded 25 second mark it drops again.  Any ideas?

---

### Post by dstath on 2008-01-09
did you manage to fix this? I have a similar problem. My connection drops after ~30 seconds. I use a USB modem. I can ping and access internet for the fist seconds but then it stops.
See [here ]("http://ubuntuforums.org/showpost.php?p=4093248&postcount=32")for more detalis.

---

