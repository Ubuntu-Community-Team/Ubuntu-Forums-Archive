---
title: "HP A6300n eth0 not recognized"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by schizoman on 2007-10-27
We have a new HP A6300n.  Just installed Edgy on it.  The install went smoothly, but the onboard ethernet connection isn't being recognized.  Specs say it's a Realtek RTL8201N.  Searching for "Linux RTL8201N" hasn't been fruitful.  Nor has trying the various terminal commands (ifconfig -a, ifup eth0, etc).

I'm wondering if this particular chip is too new to have a Linux driver for it yet.  Anyone know?  Should I just go out and get a NIC?

Thanks.

---

### Post by gwoodard on 2007-10-27
What you should do is try Gutsy, see if your onboard is disabled through bios, or left click on the network "icon" on the taskbar by the sound control choose manual config click on "wired connection" select properties and choose "DCHP" see if that works

---

