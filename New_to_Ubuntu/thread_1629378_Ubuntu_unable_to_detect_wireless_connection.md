---
title: "Ubuntu unable to detect wireless connection"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Tipau on 2010-11-23
Hi all,

I recently downloaded Ubuntu 10.04 into my Windows Vista laptop & I have downloaded the one that can run alongside my current system, so I'm running dual OS.
At the start up screen where I choose the OS, I choose Ubuntu & it loads fine. Everything looks perfect except that it won't connect to or detect any wireless connections. I have tried clicking the Network Manager icon & clicking New Connection. I typed in the security key for my wireless connection/router & after I hit create, a small window pops up saying "Wireless Disconnected: you are now working offline" or something like that. Nothing happens/changes. There is no internet connection on Ubuntu OS. But when I switch over to my Vista OS, the internet works perfectly (obviously.)

What can I do to fix this?! I really want to use Ubuntu OS. Thank you.

---

### Post by mikewhatever on 2010-11-23
Connect an ethernet cable, then check out System->Admin->HardwareDrivers.

---

### Post by Tipau on 2010-11-23
Many thanks!

---

### Post by Bucky Ball on 2010-11-23
You will be offered updates. Take 'em.

After that, check in 'System->Administration->Additional Drivers'

Anything in there disabled?

The catch 22 is that for some cards, and yours may be one of them, you need to get online with a cable before you can get wireless working (proprietary firmware/third-party software for some cards cannot be included by law on the Ubuntu install disk).

If this all goes well, your machine should be offering you a selection of available networks.

---

### Post by Bucky Ball on 2010-11-23
Incidentally, are you talking about a Wubi install or have you got the two OSs running side by side (on separate partitions and totally independent)?

A Wubi install is NOT a dual-boot and getting your network up with Wubi could be a slightly different proposition.

---

