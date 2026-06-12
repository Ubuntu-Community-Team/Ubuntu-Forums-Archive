---
title: "[SOLVED] Disabling network card"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by stee on 2008-11-03
Hello,

I installed Kubuntu 8.10 on my laptop yesterday, and everything worked great "out of the box"! Very nice! However, one problem arised after a little while:

I have two wifi cards; one internal (Broadcom 4318) and one external/pc card (d-link dwl-something). The internal is useless, and I do not want to use it.

As I said, everything worked great at first, and the internet connection worked automatically from the dlink (eth1). I could see that the broadcom (eth0) also picked up a signal, but it wasn't connected.

After I did an update with adept (I think it was an "upgrade"), I got a message that I had to update my hardware driver for the broadcom. I knew it was a bad idea, but did it anyway. 

Now I can't get online at all. How can I disable the broadcom completely?

---

### Post by superprash2003 on 2008-11-03
you could ifdown eth0 by typing sudo ifdown eth0 .. if you have wifi problems, try system->admin->hardware drivers.. if you still have problems, post output of lshw -C network.

---

