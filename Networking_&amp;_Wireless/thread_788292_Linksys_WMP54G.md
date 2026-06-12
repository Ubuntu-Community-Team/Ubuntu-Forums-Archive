---
title: "Linksys WMP54G"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by neptuneg on 2008-05-09
Hi,

I'm having trouble getting my Linksys WMP54G card to work. It seems this a common problem that is most easily resolved by using ndiswrapper.

The computer is an eMachines T2824. I've installed the latest version of Ubuntu.

I've followed many instructions to get ndiswrapper to work properly, but it doesn't seem to. It (seemingly) successfully finds the drivers and copies them to /etc/ndiswrapper (using ndiswrapper -i), but the card does not seemed to be tied to the driver.

To make matters worse, I don't have the "Restricted Drivers Manager", and I don't see a way to add it; it is not listed in Add/Remove.

Any ideas?

Thanks!

---

### Post by prshah on 2008-05-09
> **neptuneg said:**
> Hi,
them to /etc/ndiswrapper (using ndiswrapper -i), but the card does not seemed to be tied to the driver.


After "ndiswrapper -i" use ```
sudo ndiswrapper -m
sudo ndiswrapper -l
sudo modprobe ndiswrapper
```

The first command "modularises" the ndiswrapper, the second verifies it's installed correctly, the third loads it.

Then, a simple ```
iwconfig
``` should find your wireless.

Why not try my step-by-step guide ([http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260)) to set up your wireless network card? If you run into any problems, post back which step you are stuck at.

---

### Post by neptuneg on 2008-05-09
Thanks for your response.

I am doing all of these commands without any errors.  The light on the wireless card does not activate.  The PC obviously sees it, but the driver is not set to ndiswrapper.  iwconfig shows that it isn't connected to any network and dhclient just says "Network is down"

---

