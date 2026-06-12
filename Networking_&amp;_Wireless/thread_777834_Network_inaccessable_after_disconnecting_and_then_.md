---
title: "Network inaccessable after disconnecting and then reconnecting wire"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by Bradl3yJ on 2008-05-01
At first i thought it was another bug with suspending, but it turns out, if I unplug my network cord, and plug it back in, the network is from then on unresponsive until i reboot. When i plug the network cord back in, it goes through the motions, gets an IP address, ifconfig looks just like it should, but nothing is accessible. I have tried disabling and reenabling the adapter, i have tried using sudo ifconfig eth0 down then ifconfig eth0 up, nothing seems to work to bring my network access back to life other than rebooting.

When i try to ping my router when the problem is there, i get a destination host unreachable error.

---

