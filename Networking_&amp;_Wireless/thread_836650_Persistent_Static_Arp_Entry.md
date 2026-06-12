---
title: "Persistent Static Arp Entry"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by josmcc on 2008-06-21
Hello does anyone know how to create a static entry at startup other than using sudo arp -s at the command prompt. Can I create a script to do this?
Im familiar with simple batch scripts in windows, I've tried adding the necessary command under sessions in gnome, but I think I need root privilleges to set arp address, which doesn't seem to be working when logging in to my user account. 

Thanks in advance

---

### Post by pharper on 2008-11-04
I'm curious about this as well.

---

### Post by liquider on 2008-11-05
You can just add
```
arp -i eth0 -s 89.90.0.1 00:90:ma:c0:ad:dr
```to /etc/rc.local, right before the "exit 0" line.

edit:ed some non-sense

---

