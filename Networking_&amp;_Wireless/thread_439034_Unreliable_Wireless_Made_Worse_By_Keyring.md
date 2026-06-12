---
title: "Unreliable Wireless Made Worse By Keyring"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by ret3 on 2007-05-10
My ThinkPad T30 with an Orinoco PCMCIA wireless adapter is running Fiesty. The wireless connection had been unreliable, connecting after I entered my password into Keyring, then growing slower and slower over the course of an hour or so, until I rebooted. However, this morning, Keyring didn't come up. I tried configuring the connection manually, but even though the strength bars show up, the connection info shows no assigned ip or anything else. What do I do now?

---

### Post by chili555 on 2007-05-10
Please let us see:```
lsmod | grep orinoco
lsmod | grep hostap
lsmod | grep prism2
```Thanks.

---

### Post by ret3 on 2007-05-10
ls mod | grep orinoco

orinoco_cs             16900  1 
orinoco                43028  1 orinoco_cs
hermes                  8448  2 orinoco_cs,orinoco
pcmcia                 39212  1 orinoco_cs
pcmcia_core            40852  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

the other two didn't return anything

---

### Post by ret3 on 2007-05-11
bump!

---

### Post by ret3 on 2007-05-13
Anybody?

---

### Post by ret3 on 2007-05-30
Bueller?

---

