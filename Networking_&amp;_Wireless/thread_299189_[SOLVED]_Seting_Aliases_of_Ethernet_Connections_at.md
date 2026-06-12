---
title: "[SOLVED] Seting Aliases of Ethernet Connections at startup"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by siriusfox on 2006-11-13
I know that I can set an alias for a physical port with the command... ```
ifconfig eth0:0 192.168.0.#
```. I would like to set that every time I startup the computer, as if I restart right now this is not set.

I can make a little SH script, but how would I ensure that it runs at startup as root? The other option is manually editing some config file so that it would always use these. I don't know how though.


Any ideas would be appreciated,
-siriusfox

---

### Post by dmizer on 2006-11-14
add the line in /etc/rc.local:
```
gksudo gedit /etc/rc.local
```
and add your line above where it says: exit 0

save, exit, reboot ... and all should be well :)

---

