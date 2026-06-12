---
title: "Kismet stops collecting packets after 2 secs"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by imrazor on 2008-03-27
I'm having a rather odd problem with Kismet. I've installed Ubuntu 7.10 on a Thinkpad T42 with an onboard ipw2200 adapter. Kismet starts without errors, but only seems to collect packets for about 2 seconds. All the counters then stop advancing and I get no more info. I've had no luck searching the forums or Googling for similar problems. Has anyone else seen this, or better yet, have a solution?

---

### Post by PgR on 2008-04-17
I've noticed exactly this problem (though some times it will get to 3 whole seconds)

7.10 on an HP laptop with 2200 card, for what it's worth.

Sorry - not found a solution yet, but I'll let you know if I do find one.

---

### Post by imrazor on 2008-04-17
I think I found the problem, but I haven't done much research on it. I believe the problem is caused by Network Manager. One day NM crashed, and presto! kismet began collecting packets. I haven't figured out yet how to kill Network Manager yet, but I haven't tried very hard. I don't want to uninstall it; just kill it every once in a while to monitor packets.

---

### Post by PgR on 2008-04-18
Ah - I think I have it.

I tried killing network manager, but it seems to pick itself up again.

However, running ```
sudo ifdown eth1
``` before starting kismet appears to let it work.

---

### Post by imrazor on 2008-04-18
> **PgR said:**
> Ah - I think I have it.

I tried killing network manager, but it seems to pick itself up again.

However, running ```
sudo ifdown eth1
``` before starting kismet appears to let it work.

Thanks...that works quite well. Anyone know why Network Manager interferes with Kismet?

---

