---
title: "Linksys WMP54G Wireless network optimisation"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by parkejr on 2006-10-03
Hi,

I recently bought a linksys WMP54G PCI wireless card. Slung it in the machine, and booted up with no problems. Card is detected and assigned to ra0, and I have been able to connect to my router and to the internet with no problems.

However, data transfer rates to my machine are about a tenth of the speed that my wireless laptop achieves, in the same room.

I've tried booting into windows, and the transfer rates are much closer to what I would expect, so I'm wondering if there is something in the configuration that I need to tweak to improve the transfer rates (g mode only, etc?) 

There is lots of advice on getting this card recognised by Dapper, but not much on optimising the configuration.

Would anyone be able to tell me where to start?

Thanks,

Jeff.

---

### Post by wieman01 on 2006-10-03
Try disabling "ipv6" both in Firefox and in Linux by blacklisting the module, etc. There are many threads describing a solution.

---

### Post by parkejr on 2006-10-05
how do I disable ipv6?

Also my transmission power seems to be stuck at 2 dBm. Is there any way I can get it up to its nominal 15 dBb?

Many thanks,

Jeff.

---

### Post by wieman01 on 2006-10-05
Disabling it in Firefox: [http://wolphination.com/linux/category/howto/]("http://wolphination.com/linux/category/howto/")

Disabling it globally: [http://www.ubuntuforums.org/showthread.php?t=271702&highlight=alias+net-pf-10+off]("http://www.ubuntuforums.org/showthread.php?t=271702&highlight=alias+net-pf-10+off")

But I suspect that your problem has another cause... If you're saying that the transmission power is bad. Is the router running on G only? Are all your devices wireless G?

---

