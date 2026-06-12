---
title: "Wireless card not recognized."
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by headbanger1547 on 2006-09-04
I have an internal wireless card (Accton WN4201B) in a desktop running Kubuntu 6.06.

I installed ndiswrapper and I know it's loaded and fine (using `sudo depmod -a` and `modprobe ndiswrapper`). But I can't tell what interface the wireless is on. iwconfig doesn't show it, but rather just brings up "NOT READY" along with the other info.

---

### Post by NetworkGuy on 2006-09-04
When you do a ```
ndiswrapper -l
``` from a terminal, what do you get back?

---

### Post by headbanger1547 on 2006-09-12
"wn4201b
driver installed
hardware present"

---

