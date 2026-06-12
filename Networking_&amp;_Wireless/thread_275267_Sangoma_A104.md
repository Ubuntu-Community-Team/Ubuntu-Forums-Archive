---
title: "Sangoma A104"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by jpmrblood on 2006-10-11
Hi, all,

I two PCs and each is installed with Sangoma A104. I have tried to compile the driver (2.3.3-7, 2.3.4-beta7, 2.3.4-beta9) with no luck. Have any of you have manage install the card and connected both PCs well?

Please share any idea, howto, step-by-step. I'm using Dapper 6.06.

---

### Post by jpmrblood on 2006-10-12
Looks like I've figured it out.

[LIST=1]
[*]Just grab the source kernel and latest sangoma driver (I use the beta7, beta9 is the latest).
[*]I install gcc-3.4 and use that compiler to do the job. I think this is not needed, the only reason I use it because the installation of Sangoma give gcc warnings when using gcc-4.x for compiling the tools.
[*]So, I compile the kernel, boot from it, and then run the sangoma driver installation.
[*]Just run wancfg and the card is up and running.
[/LIST]

Btw, to have back-to-back connection like 2 PCs linked together, we must use specialised cross cable. I think I found it in the Sangoma web somewhere. I asked my friend to make the cross.:)

---

