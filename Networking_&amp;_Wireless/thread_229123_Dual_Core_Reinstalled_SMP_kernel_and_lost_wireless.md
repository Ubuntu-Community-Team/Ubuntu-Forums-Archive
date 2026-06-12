---
title: "Dual Core: Reinstalled SMP kernel and lost wireless"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by teb on 2006-08-04
Bought my nice Sony Vaio VGN-SZ28GP laptop (trying to forget about sony's rootkit actions) and installed Ubuntu 6.0.6 from CD. I have been using Ubuntu on my laptops (and desktops) for 1.5 years now, and most of it just works, as in this case as well. I am really grateful for that!

Then I had my Intel PRO/wireless 3945abg working as should. But ubuntu saw only the one processor. So I found out that I was using the 386 kernel, and upgraded (with synaptic, so easy) to the linux-image-2.6.15-26-686 kernel. And now it sees two processors (with: cat /proc/cpuinfo). The eth1 device however is not recognised anymore. Strange enough.

What should I do, because the Intel drivers are all installed.

thanks,

Wouter

---

### Post by holyroller1 on 2006-08-07
BUMP,

I am having this same issue.

---

### Post by kevinsun on 2007-03-25
me, too. I think it becomes a common bug and people are still fixing it.

---

