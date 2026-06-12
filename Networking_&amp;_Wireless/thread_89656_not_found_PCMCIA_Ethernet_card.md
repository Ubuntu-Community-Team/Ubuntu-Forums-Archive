---
title: "not found PCMCIA Ethernet card"
date: 2005-11-13
forum: Networking &amp; Wireless
---

### Post by sportovec.lukas on 2005-11-13
Please, help me!
I installed Ubuntu 5.10, all is OK but Ubuntu not found my network card.
type: Plug&Play PCMCIA Ethernet card by Novell/Amthen
under Windows work good.:confused: 
please help me Im beginner and I need internet connection.

Thanks

---

### Post by Lambert on 2005-11-13
Open the terminal and type this in

```
sudo lshw -C network
```

Post the out put here.

What's the model # of the device?

---

### Post by az on 2005-11-13
If you have an older laptop, the pcmcia may be on the isa bus and you will need to load the pcmcia kernel driver by hand.  It is not hard to do.

---

