---
title: "no wireless after kernel upgrade"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by cully on 2006-10-04
I just upgraded my kernel from 2.6.15-26-386 to 2.6.15-27-686.  When I restarted, my wireless interface is nowhere to be found.  I'm thinking that this has something to do with a missing kernel module.  However, I'm not sure how to discover which module I need or to install it.

Thanks for any help.

---

### Post by cully on 2006-10-04
I removed the old linux-resricted-modules, restarted, and my wireless card was found.  However, it only connects for like a second at a time and then restarts.  Also, my sound went out for some reason.  Any ideas?

---

### Post by anelar on 2006-10-04
The exact same thing happened to me when upgrading! Havent found a fix yet... Why do you think that the linux-restricted-modules helps? 

/A

---

### Post by cully on 2006-10-04
I reinstalled the old linux-restricted-modules (and kept the new ones).  Now my sound works and my network card is found, but I'm still having the problem of losing my connection every second.  The wireless card connects, lets me browse/download for a second or so, and then needs to reconnect.

---

### Post by cully on 2006-10-04
> **anelar said:**
> The exact same thing happened to me when upgrading! Havent found a fix yet... Why do you think that the linux-restricted-modules helps?/A

I read another post about a user solving a similar issue by installing the restricted modules, which apparently has some wifi modules in it.  I was thinking that maybe the old modules were being used or something.  I'm not sure why reinstalling them worked in any way.

---

### Post by cully on 2006-10-08
I hope I'm not speaking too soon, but I believe I discovered the problem with my wireless card disconnecting and then reconnecting every couple of seconds.  

I had originally set up wpa supplicant to manage my wireless connection.  I later switched to KNetworkManager.  I never removed the wpa supplicant lines from my /etc/network/interfaces file, so wpa supplicant was running at the same time as KNetworkManager.

It worked fine at first, but something must have happend when I upgraded to the new linux-restricted-modules, and apparently they started to conflict.  So, I shut down wpa supplicant and took the lines out of my /etc/network/interfaces file and my wireless is working like a champ.

---

### Post by joergenlie on 2006-10-09
> **cully said:**
> I just upgraded my kernel from 2.6.15-26-386 to 2.6.15-27-686.  When I restarted, my wireless interface is nowhere to be found.  I'm thinking that this has something to do with a missing kernel module.  However, I'm not sure how to discover which module I need or to install it.

Thanks for any help.

what wierless drivers are you using? I found that ndiswrapper stopped working after innstalling the nvidia drivers, this removed the restricted modules so I reinstalled them. If you have compile ndiswrapper I think you need to reinstall it after kernel upgrade. Try it out.

Jørgen

---

