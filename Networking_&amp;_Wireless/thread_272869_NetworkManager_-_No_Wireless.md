---
title: "NetworkManager - No Wireless"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by TDave on 2006-10-07
All

I've been running Kubuntu 6.06 on my Apple PowerBook G4 since the full release and was very impressed when I first installed and ran KNetworkManager, simply as it seemed to just work.

Howegver, recently I had to reinstall everything due to a hard drive failure and found that upon reinstalling KNetworkManager (after setting up the AirportExtreme Wireless Card to work) it only gives me the option of seeing Wired Devices.
Selecting it to 'Enable Wireless' doesn't appear to do anything. However, on startup it does popup an in of box saying it detects the networks in the area, but there just appears no way to connect to them.

I have tried the various options in the wiki (commenting out other items in /etc/network/interfaces and the like) but to no avail. I have also reinstalled numerous times, always with the same error.

Anyone else suffered similar to this, or any suggestions on what else I may not have tried?

My /etc/network/interfaces looks like this:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

```

Cheers

TD

---

