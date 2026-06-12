---
title: "Repairing my ethernet connection"
date: 2005-06-11
forum: Networking &amp; Wireless
---

### Post by tmccartney on 2005-06-11
or, "When n00bs try to muck around where they don't belong"

I've been trying to get my Microsoft MN-520 wireless card working; tonight was my first time whacking away at it since probably December.

Previously, my ethernet connection worked fine, but I think I managed to screw it up messing around in the network admin and the /etc/network/interfaces file.

Now I get no connection, and when I try to set up an ethernet connection in the network admin, it won't stay activated.  I'm guessing I've created a conflict somewhere.  (The Ethernet card also no longer shows up when I do ifconfig.)

Is there a file I should just delete and start clean?  I'd like to get some kind of 'net connection working so I can update to Hoary.


Thanks,

Tracey

---

### Post by bjorn on 2005-06-12
This is my /etc/network/interface file, I have not touched it :grin:

 ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
		script grep
		map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0

```

---

### Post by tmccartney on 2005-06-12
That did it - thanks!




Tracey

---

