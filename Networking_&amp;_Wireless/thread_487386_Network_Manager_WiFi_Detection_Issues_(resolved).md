---
title: "Network Manager WiFi Detection Issues (resolved)"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by Gnub_Daemon on 2007-06-29
So I accidentally removed the notification area from my panel and, being a Gnub myself, I didn't know that that was how to get the Network Manager icon to appear.  I searched the forums and google for a couple of hours, and uninstalled/reinstalled Network Manager in the process.  My internal WiFi antenna was not detected afterward, and I could not connect to any wireless networks (or even see them for that matter.)  Also, Network Setup showed no option for Wireless connection.  I was getting really, reeeeally upset.  Nothing I found that was previously posted helped at all.  So finally, out of desperation, I restarted and used the Recovery Mode in the GRUB options.  It ran through its little schpiegl and ended up at the root@zeke~# input line.  I didn't know how to restart from terminal, so I just held down the power button until it turned off.  Upon restarting my computer, the Network Manager was working with my internal WiFi card, and I could once again connect to wireless networks.  

So, if any of you have this problem, or something similar to it, try the Recovery Mode in the startup GRUB.  It might just fix your problem.

---

