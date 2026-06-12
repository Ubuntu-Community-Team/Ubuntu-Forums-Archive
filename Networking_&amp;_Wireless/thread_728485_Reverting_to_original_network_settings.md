---
title: "Reverting to original network settings"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by tttllc on 2008-03-18
I want to revert my network settings back to the 'fresh install' level without doing a total reinstallation.

I've been using Kubuntu (now 7.10) for about 6 months and the wired network that I connect to has worked fine the whole time.  Recently I tried to install a vmware without doing much research on how to setup the networking for the virtualized OS.  In doing so I disabled my internet connection from regular Kubuntu.

I'm not worried about getting vmware working now, just on getting back online from my kubuntu partition.  I have live cds and internet access from other computers, so if there is a plain text copy of the relevant files, or whole sections of code somewhere on the live cd, a point in that direction would be appreciated.

Thanks in advance for the help.

---

### Post by Eiríkr on 2008-03-19
Well, it depends on your physical network config.  Are you connecting over ethernet, or wireless?  What are your physical devices (eth0, eth1, wlan0, etc)?  Let us know, and also post the contents of your /etc/network/interfaces file, and perhaps we can get started.

Cheers,

Eiríkr

---

### Post by tttllc on 2008-03-19
I only (want to) connect over ethernet.

The devices in the network settings manager are eth0 and wlan0

the entire content of my ect/network/interfaces file is:

auto lo
iface lo inet loopback

---

