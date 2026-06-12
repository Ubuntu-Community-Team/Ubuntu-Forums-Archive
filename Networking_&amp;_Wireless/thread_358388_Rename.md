---
title: "Rename"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by homer.s on 2007-02-10
I just got all my Internet connections working on my laptop, but now my wireless connection is named ETH1, I need it to be WLAN0 for some of my online programs, how do I rename it?

---

### Post by gradedcheese on 2007-02-10
The names are assigned by the kernel.  You might be able to rename an interface by editing /etc/iftab (run "man iftab" for more information) but I've never tried.

---

