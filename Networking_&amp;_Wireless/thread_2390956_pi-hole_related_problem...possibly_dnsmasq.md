---
title: "pi-hole related problem...possibly dnsmasq"
date: 2018-05-04
forum: Networking &amp; Wireless
---

### Post by sp40140 on 2018-05-04
I did fresh install of 18.04 64bit.
Everything went fine. I installed pi-hole (ad-blocker, which basically uses dnsmasking to get rid of ads).
Now, configuration of pi-hole went fine.
But the host is unable to connect to anything but the router.
All other devices are fine on network.
After a bit of research I found that this could be related to "dnsmasq" service.
I tried to restart the dnsmasq service and it doesn't. the command returns error.
I briefly changed the dnsserver in "/etc/resov.conf" from 127.0.0.53" to 8.8.8.8 (google dns) and it worked.

However, ad-blocking doesn't work anymore.

One of my friends uses this set-up successfully. The only bug is that every time he reboots the machine, he has to re-start the dnsmasq service.

Any help with this problem is going to be helpful.

---

