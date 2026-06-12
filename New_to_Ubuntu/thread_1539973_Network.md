---
title: "Network"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by Whatrymes on 2010-07-27
Ubuntu 10.04 is up and running and seems to be glitch free. One thing I still haven't figured out is how to connect to other devices on my network. In particular, there is a memory card attached to my network printer that I have no access to under Linux. In Vista, the card is accessed at Computer/Network Location. It is listed as drive Z: and the address is "\\192.168.1.200\memory_card". I haven't been able to see anything on a network or do I know how to set it up. Hope I explained this all correctly.

Thank you,
Ed

---

### Post by Morbius1 on 2010-07-27
Can you see it if you do this:

In a terminal type:
```
nautilus smb://192.168.1.200/memory_card
```If you can, then Bookmark it so it shows up on the left side panel just like a Z drive does in windows.

---

### Post by Whatrymes on 2010-07-27
No, I get this error:[ATTACH]164651[/ATTACH]

---

### Post by Morbius1 on 2010-07-27
See if you have the following package installed:
> gvfs-backends

---

### Post by Whatrymes on 2010-07-27
> **Morbius1 said:**
> See if you have the following package installed:

Yes and I tried a re-install.

---

### Post by Whatrymes on 2010-07-27
re-install didn't seem to help

---

