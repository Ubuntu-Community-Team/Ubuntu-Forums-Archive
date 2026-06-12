---
title: "ZD1201 USB Wireless / hotplug Issue - So Close!"
date: 2005-08-10
forum: Networking &amp; Wireless
---

### Post by displaced on 2005-08-10
Hello everyone,

I'm new (2 days) to Ubuntu, and so far I'm really really liking it!  In two evenings I've got closer to what I'd call a usable Linux desktop than I have in any other distro.

I even managed a first (for me):  my ZD1201-based USB Wireless adapter works great!  With a little caveat that I hope someone can help me with.

If I start up the system and type:
```
modprobe zd1201
```
... then it all goes well.  The interface shows up in **System > Administration > Networking**, it can be configured, and picks up an IP address.  Woohoo!

But...   (ain't there always a 'but')

I can't get it to initialise correctly during boot, or apparently whenever hotplug's involved.

If the device is unplugged and re-plugged, the syslog shows firmware upload failure (error -2).  If I add zd1201 to /etc/modules, likewise, the firmware doesn't take.

Seems odd -- I've put the firmware files into the correct location(s): /lib/hotplug/firmware and /usr/lib/hotplug/firmware just to be on the safe side.  And as I've noted, rmmod'ing and modprobe'ing manually works as expected.

Any tips?

Thanks!

Chris

---

