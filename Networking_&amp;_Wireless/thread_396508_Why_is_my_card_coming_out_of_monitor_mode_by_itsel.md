---
title: "Why is my card coming out of monitor mode by itself?"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by mlapaglia on 2007-03-29
I have my USB wireless card installed (rausb0 in iwconfig)

when i set it to monitor mode, it comes out randomly and automatically.

this happens even when i have network-manager turned off...

help please :)!

---

### Post by menacespb on 2007-04-04
I have a Fujitsu Siemens Lifebook P7010, and it has the exact same problems. I'm running Feisty Fawn.

For example, when using kismet, it will start and work for a short while, then just stop gathering packets since it appears to be forced out of monitor mode. Then if I, while keeping kismet running, open another terminal and do "sudo iwconfig eth1 mode monitor", then kismet will start collecting packets again... for about one minute, then stall again.

It certainly appears like something is monitoring the wireless connection to make sure it is in managed mode. Love to know how to turn that off.

---

### Post by mlapaglia on 2007-04-05
well i found a workaround at least. let network-monitor run, dont turn it off. right click on the icon and select "disable wireless".. that seems to do the trick.

---

