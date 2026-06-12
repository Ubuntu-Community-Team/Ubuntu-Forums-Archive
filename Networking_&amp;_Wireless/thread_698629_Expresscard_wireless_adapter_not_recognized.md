---
title: "Expresscard wireless adapter not recognized"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by firecat53 on 2008-02-16
Hi. I just got a Belkin F5D8073 N wireless expresscard for my hp dv6058 (since the internal card stopped working). Running Gutsy AMD64.

I can't get the card to even be recognized after trying the following:
- Rebooted with the card installed
- modprobe pciehp, then insert the card (dmesg shows the driver being loaded, but nothing when the card is inserted or removed
- modprobe acpiphp (same result as pciehp)

Some people have reported this card working with ndiswrapper, but my computer won't even see it!!

Any thoughts?

Thanks, Scott

---

### Post by bwang on 2008-02-16
Does your card show up in Device Manager?

---

### Post by teaker1s on 2008-02-18
```
lspci
```
will tell you model of chipset

---

