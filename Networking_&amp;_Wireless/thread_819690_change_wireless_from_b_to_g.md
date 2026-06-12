---
title: "change wireless from b to g"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by xboxbman on 2008-06-05
Simple problem,  I've forgotten the command for it.  My desktop has a wireless card that supports both b and g, but is defaulting to b.  I can't seem to figure out how to set it to g. Could someone point me in the right direction please?

---

### Post by xboxbman on 2008-06-07
bump for a simple question....

---

### Post by cdtech on 2008-06-07
sudo iwpriv wlan0

Without any argument, iwpriv list the available private commands available on each interface.

---

