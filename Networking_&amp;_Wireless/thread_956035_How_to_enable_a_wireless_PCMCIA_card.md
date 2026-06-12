---
title: "How to enable a wireless PCMCIA card"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by nu2this2 on 2008-10-22
I have a Buffalo 54gs card in the slot of my laptop. The light on the card does not light up. Does that mean that it is not active. I have installed Hardy Heron.

Thank you.

---

### Post by nu2this2 on 2008-10-23
> **nu2this2 said:**
> I have a Buffalo 54gs card in the slot of my laptop. The light on the card does not light up. Does that mean that it is not active. I have installed Hardy Heron.

Thank you.

Anyone??

---

### Post by Ayuthia on 2008-10-23
Can you post the results of the following:
```
lspci -nn
lsusb
lshw -C network
```Maybe it might help us see something so that we can get it to turn on.

---

### Post by nu2this2 on 2008-10-25
> **Ayuthia said:**
> Can you post the results of the following:
```
lspci -nn
lsusb
lshw -C network
```Maybe it might help us see something so that we can get it to turn on.

Thanks for getting back to me:). My problem has been solved though. I purchased a different wireless card and it works perfectly right out of the box, I couldn't believe it. Just put it in the slot and Presto, I'm able to browse with four bars strength.

---

