---
title: "Wireless Issues with HP dv6000 and BCM4328"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by rmstone1s on 2008-03-13
I've got a unique issue with a new HP Pavilion dv6000 (dv6748us).  I can't seem to find anyone else having this issue.

First most dv6000s seem to at least attempt to use restricted wireless drivers... mine does not, doesnt even show in the list.  Anyways, i blacklisted it, went through the typical tutorial to install ndiswrapper and the windows driver (i tried both in 64-bit and then reinstalled ubuntu 32-bit and get the same result).  ndiswrapper and modprobe seem to have a number of issues...

After the install if I do a: sudo modprobe ndsiwrapper
The console hangs but slowly the wireless starts up and works... and i can close the locked console and everythings fine until a reboot.

The solution for this seems to be to add modprobe to the /etc/modules file.  This causes my boot to hang at a step that says something about "loading manual drivers" (and i have to go into rescue mode just to remove modprobe from that file).

Another strange issue is that ndiswrapper seems to only partially work... for instance "ndiswrapper -l" locks the console up and nothing ever returns...  if also had the gui install for ndiswrapper and when it starts up its all blank, nothing in the window at all.  I can install the driver just fine with it but i cannot list the installed drivers.

I even tried downloading the source for ndiswrapper and compiling it on my machine to see if that helps, no difference, this issue is also there in 32-bit and 64-bit mode.

I've tried everything I can find, anyone have any ideas?

---

### Post by rmstone1s on 2008-03-14
Bump, anyone?

---

