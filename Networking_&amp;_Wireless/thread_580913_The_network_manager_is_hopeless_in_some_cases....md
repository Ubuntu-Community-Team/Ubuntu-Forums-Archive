---
title: "The network manager is hopeless in some cases..."
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by mhakali on 2007-10-19
... for example, I have hooked up two laptops with a crossover cable wired to wired network. 

I am usally connected to the wireless network on both laptops. Though magically when plugging in a wired cable it tries to get a DHCP IP from the wired network. This won't work since it's a crossover connection which I later want to manually configure IPs for internal communication.

Ok. That's fine (well. actually not, but it's acceptable). I click the network manager and select the Wireless network while it's requesting a DHCP IP from the wired. Magically this ends up with no IP set, and the network manager have put a dot indicating selected connection next to "Wired network" AND the wireless network selected. Yet none of the interfaces has got any IP. And iwconfig shows that it does not have any connection to the wireless network which the Network Manager pretends to have.

Fine, I think. I go in to network settings and disable roaming for the wired interface. Now all my options for wireless connectivity dissapeared in the network manager. Using "iwlist eth1 scanning" shows an accurate list of all networks available.

Can it really be that hopeless maintaining a connected connection without switching media as soon as you pull the network plug? Maybe it just slipped?

Can it really be that hopeless to set up a local net between two laptops using the wired network without the Network manager involving? I just want to scp some files and maintain my wireless connection...

Maybe I should just uninstall it. But then again WPA will be a pure hell getting a nice interface for. Which is essentially the only thing that the Network Manager does well. Or. Um. most of the time when key exchanges etc dosen't bug out and I am forced to modprobe -r and reinsert my wireless module that is... :-)

---

