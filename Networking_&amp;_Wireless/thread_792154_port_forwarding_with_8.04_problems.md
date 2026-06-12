---
title: "port forwarding with 8.04 problems"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by Xvani on 2008-05-12
Hi!

After installing 8.04, upnp does not seem to work (tried transmission, Azureus and Deluge). In addition, Ubuntu does not care if I manually forward the ports in my router...

I'm guessing the ufw has something to do with it, but even after I disabled it, the torrent programs do not recognize the ports being forwarded.

How do I properly (and preferably using upnp) forward my ports again?

Thanks a bunch!

---

### Post by vorgusa on 2008-05-12
This sounds like more of a router problem then an Ubuntu problem.. you need to go into the router config and tell it to port forward to the IP of your computer (which you might want to make static).  Also make sure UPNP is enabled on the Router.

---

### Post by Xvani on 2008-05-16
Thank you for your reply!

I should have added that UPnP is enabled, its port forwarded and this works on other linux distros I have as well as all the other guys in my household....

This is definately only relevant for **my** system =)

---

### Post by DarthTibault on 2008-05-19
> **Xvani said:**
> After installing 8.04, upnp does not seem to work

I've noticed the same thing.
Opening ports on my router manually is something I'd rather not do as I would forget closing them.

---

