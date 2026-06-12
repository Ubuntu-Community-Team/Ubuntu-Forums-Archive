---
title: "Cannot get DRBL install to recognize virtual ethernet card"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by jxjordan on 2010-08-18
I'm new to Linux/Ubuntu, so please bare with me.  I am in the process of setting up Clonezilla on Ubuntu server32.  When I modify my /etc/network/interfaces for a virtual ethernet card, it replies "only one configured network card was found on this system" when attempt to run the DRBL install.  I found an old post at ubuntuforums.org/showthread.php?t=555319, and set it up like that, but still nothing.  Does anyone have any suggestions?  Any would be greatly appreciated.  Thanks.

---

### Post by jxjordan on 2010-08-21
Issue was with having the hardware address in the network/interfaces file. Removed it andi it worked fine.

---

