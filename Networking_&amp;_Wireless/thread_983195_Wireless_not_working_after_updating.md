---
title: "Wireless not working after updating"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by ramidavis on 2008-11-15
I hope this in the right board, and if it is not, please let me know, or have mod move it to where needs to be.

Ok, i am running ubuntu ibex 32 bit, i recently upgraded my ram from 2 512-mb sticks to 2 2-gig sticks. Ubuntu would not pick up my memory, so some one told me to run the following in a terminal:
```
sudo apt-get install linux-server linux-headers-server
```
After doing that, and booting using the server entry from my grub list, my memory is working fine, but my wireless is no longer functioning. My system is a acer aspire 5100 laptop, using an atheros card(one that came with the system).

I really do not understand why ubuntu can not see my wireless card anymore, when i can boot into the generic-kernel from grub, and use wireless there (but the memory drops to 2 gig when i do so... )

Any help or suggestions?

P.S.: I had the same memory issue using ubuntu hardy, and fixed it the same way, using the code above, and under hardy server my wireless was just fine. I really, really do not want to down-grade back hardy just to fix this...

---

### Post by rlzyoner on 2008-11-15
I'm not entirely sure but usually for me, after the headers are updated, I need to reinstall the drivers / ndiswrapper

Try that

Again, this works for me but there may be a handier way to do it

---

