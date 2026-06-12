---
title: "Using two WAPs"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by DaveAK on 2007-07-29
Not really an Ubuntu question, but can I set two WAPs to use the same SSID, security model and password?  I have an access point at each end of my house running slightly different setups, (because of an older machine that doesn't do WPA-PSK).  I'm upgrading this old machine and was wondering if I set both WAPs to be the same, would this be transparent to the user and I could just take my laptop around the house and have it connect to the WAP with the best signal, but using the same configuration settings on the laptop?

---

### Post by spd106 on 2007-07-30
Yes you can, however it does mean that you have to careful how you configure the rest of the network. You want to ensure that you don't have duplicate dhcp servers with the same IP address pools.

I think it's more common the APs in WDS mode, if your equipment is capable. It doesn't always work well if they are from different manufacturers.

[http://en.wikipedia.org/wiki/Wireless_Distribution_System](http://en.wikipedia.org/wiki/Wireless_Distribution_System)

---

### Post by DaveAK on 2007-07-31
> **spd106 said:**
> Yes you can, however it does mean that you have to careful how you configure the rest of the network. You want to ensure that you don't have duplicate dhcp servers with the same IP address pools.

I think it's more common the APs in WDS mode, if your equipment is capable. It doesn't always work well if they are from different manufacturers.

[http://en.wikipedia.org/wiki/Wireless_Distribution_System](http://en.wikipedia.org/wiki/Wireless_Distribution_System)
Thanks!  I only have one DHCP server, and a wired back bone so I won't need WDS.  Should hopefully be straightforward once I get the old machine updated to WPA-PSK. :)

---

