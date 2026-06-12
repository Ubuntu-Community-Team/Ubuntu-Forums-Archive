---
title: "Monitor Wireless Network?"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Alex82 on 2009-03-19
Hello, I would like to know if there is any program that is available which will let me know if anybody is trying to access my protected wireless network (and then let me zap them!)

We are at an outback campgrounds and don't want anyone except us using the network

---

### Post by bruno9779 on 2009-03-19
When it comes to wireless monitoring, Wireshark rocks.
While being one of the best tools for this, you may need to put up a machine just for that.

Have you thought about increasing security instead?
MAC locking and logging of all network activity may do the trick in a cheaper way

---

### Post by jbrevik on 2009-03-19
You can try airmon-ng. But perhaps if your concerned about other people trying to access your wireless network, try MAC address filtering in the router.

---

### Post by bruno9779 on 2009-03-19
> **jbrevik said:**
> try MAC address filtering in the router.

that is what i meant for MAC locking. :D

---

### Post by Alex82 on 2009-03-19
> **jbrevik said:**
> You can try airmon-ng. But perhaps if your concerned about other people trying to access your wireless network, try MAC address filtering in the router.

Thanks very much.
Unfortunately I cant access my router at the moment as I have misplaced the password and don't want to mess around resetting it!  Hopefully will find the password tonight.

---

### Post by xpod on 2009-03-19
> You can try airmon-ng. But perhaps if your concerned about other people trying to access your wireless network, try MAC address filtering in the router.

Mac Address filtering is about as much use as a poke in the eye with a sharp stick if someone who actually knows what their doing is scanning your networks & trying to gain access.

---

### Post by jbrevik on 2009-03-19
If someone really wants to gain access to your wireless network, they will but I'd rather "poke someone in the eye with a sharp stick" than have limited security at best. 

Might also want to try masking the SSID. I know the masked SSID can still be picked up using airmon-ng but I'll default to the old saying "Out of site, out of mind"

---

### Post by bruno9779 on 2009-03-19
you may want to have a look at this too:

[http://www.ex-parrot.com/~pete/upside-down-ternet.html](http://www.ex-parrot.com/~pete/upside-down-ternet.html)

interesting read

---

