---
title: "Want to return from &quot;attempted&quot; internet sharing to original setup"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by LO Matt on 2006-12-28
So I was playing around with an older box, and following the instructions in [http://www.ubuntuforums.org/showthread.php?t=91370]("http://www.ubuntuforums.org/showthread.php?t=91370"),  I attempted to share a wireless connection with another box.  I wasn't able to get it working, and now I just want to return the old box to it's original wireless connection to a router (which was working flawlessly for months).  Unfortunately, I don't know how to get back to my original configuration

I've attempted to reverse all the instructions, but I still can't connect.  Can anyone help?  I'm preparing to do a reinstall, but if there's a quick and dirty way to get back to the original config, that'd be great.  

I'm using Xubuntu Dapper

/etc/network/interfaces

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface

iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# The primary network interface
iface wlan0 inet dhcp
wireless-essid orange
wireless-key a1b2c3d4e5

auto wlan0

```

---

