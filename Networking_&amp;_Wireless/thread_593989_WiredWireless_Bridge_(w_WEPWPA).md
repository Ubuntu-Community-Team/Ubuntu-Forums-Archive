---
title: "Wired/Wireless Bridge (w/ WEP/WPA)"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by cparker on 2007-10-27
I have a request I'm sure you've all heard of before. I've browsed through some other threads here, but didn't find a solution to my specific issue.

My laptop has a wired and a wireless network connection. It's connected to the Internet wirelessly with a WRT54G (OpenWRT). It's currently secured using WEP, but I'm planning on setting up WPA in the near future.

I have a switch with a few networked devices attached to it.

What I'd like to do is attach the wired connection of the laptop to the switch, bridge the wireless and wireless connections on the laptop, and have all of the devices attached to the switch to be able to access the rest of the network through my laptop.

It's important that other nodes on the rest of the network can access these devices. Because of this, I'm thinking they all have to be on the same subnet.

Is there a way to bridge these two connections and have the WRT54G assign the IP addresses to all of the devices attached to the switch through my laptop, so everything is on one subnet? I attempted to set things up manually in /etc/network/interfaces after installing bridge-utils, but I can't seem to figure out how to incorporate my wireless settings into that sort of a configuration.

---

### Post by kevdog on 2007-10-27
Interesting configuration -- wish I could help.  Make sure dhcp is turned off in the switch.

---

### Post by cparker on 2007-10-27
Thanks for your reply! I don't think I have to worry about that... it's just a D-Link 10/100 Fast Ethernet switch... not a router or anything.

If I come up with a solution outside of this forum, I'll document it here in case someone else will find it useful.

---

