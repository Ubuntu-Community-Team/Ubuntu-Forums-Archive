---
title: "Downloading Ndiswrapper from another computer."
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by Monster_user on 2008-01-06
Alright, my Kubuntu 7.10 computer connects to the internet wirelessly. It would be a big hassle to try an connect it via Ethernet, just to connect to the internet.

So how can I download the required DEBs, in order to either install, or compile Ndiswrapper.

---

### Post by ugm6hr on 2008-01-06
> **Monster_user said:**
> Alright, my Kubuntu 7.10 computer connects to the internet wirelessly. It would be a big hassle to try an connect it via Ethernet, just to connect to the internet.

So how can I download the required DEBs, in order to either install, or compile Ndiswrapper.

Here:
[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common)

Near the bottom are links to the downloads (under Architecture).

---

### Post by Monster_user on 2008-01-06
Thank you. 

Now, I've loaded the correct driver, but it won't load wlan0.

> sudo ifup wlan0

ignoring wlan0=wlan0

I've run "modprobe ndiswrapper", and "iwconfig", and it still isn't working.

**[Solved]** 
It seems I left out an option for iwconfig.

---

