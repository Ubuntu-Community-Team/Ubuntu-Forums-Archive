---
title: "Only Reboot Fixes Wireless Connection"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by energy_One on 2008-10-27
There's no cable long enough in the house to run to my room from the router, so I do not know if this is only a wireless problem (though I'm betting it is).

Originally, wireless was working fine on my desktop, running Ubuntu 8.04, or at least seemed to be. Fine, as in at listed 2 Mb/s with the rt73 driver for my Belkin Wireless Mimo Plus G USB network adapter. Then I found a Windows driver that ndiswrapper's GUI liked. It -still- seemed to work fine after that.

Then I decided to play with fire. Firestarter, actually. After deciding it wasn't for me, I decided to play around with the network manager instead. I replaced nm with wicd for a while. That definitely didn't work. Crashed when switched to ndiswrapper, which was the only method I could find to give the adapter full functionality.

Switched back to network-manager.

Now I have begun to notice this problem, the main concern of my request for help:

An hour, two, three hours after reboot, wireless shuts down and will not start up again. The LED is off on the adapter. Unplugging and replugging has no effect. I tried flushing the IP tables to see if firestarter had left a mess behind, but it seems no config files remain for the program, and the IP table did not helped (still have not rebooted since doing so).

What command would you folks like me to run in order to show you helpful diagnostic information? I'd prefer not to have to restart my desktop every few hours to use the internet properly on it.

---

### Post by energy_One on 2008-10-29
I managed to clear the settings for wicd.

Still looking for advice on what command to run to post relevant diagnostic information.

---

