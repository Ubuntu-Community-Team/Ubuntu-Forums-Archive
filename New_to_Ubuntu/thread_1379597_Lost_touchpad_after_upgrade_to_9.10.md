---
title: "Lost touchpad after upgrade to 9.10"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by qwwerty on 2010-01-12
Hi,
I upgraded (via Update Manager) to 9.10 from 9.04 and now my touchpad doesn't work (Samsung NC10). Tried it in windows and it works fine, and an external mouse works as well.

Any idea what the problem could be?

---

### Post by tom.swartz07 on 2010-01-12
> **qwwerty said:**
> Hi,
I upgraded (via Update Manager) to 9.10 from 9.04 and now my touchpad doesn't work (Samsung NC10). Tried it in windows and it works fine, and an external mouse works as well.

Any idea what the problem could be?

Alrighty, lets try 2 things.
There might be a driver for it, and its just not enabled. Head on over to system>admin>hardware and drivers
See if theres something there.

If not, open synaptic and search for touchpad

There should be xserver-xorg-input-synaptics. If its not installed, click it and put that on.
You could also look for tpconfig, that might have some support for your touchpad.


While youre at it, just run another update from the update manager just to be sure everythings up to speed.

---

### Post by qwwerty on 2010-01-13
I checked Hardware and Drivers, but it says there's no property drivers for my system, checked xserver-xorg-input-synaptics is installed, and upgrade manager says the system is fully up to date.

Tried tpconfig, but it failed saying it couldn't open a PS/2 port.

I know that 9.10 works on this laptop (a friend has the same model), so I don't know why it's not working for me.

Also noticed the sound has gone, and the GRUB label still says 9.04 (Kernel:2.6.28-17), might be related?

---

