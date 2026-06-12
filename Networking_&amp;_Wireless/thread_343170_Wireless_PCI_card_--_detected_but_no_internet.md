---
title: "Wireless PCI card -- detected but no internet"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by master5o1 on 2007-01-21
I can input all my wireless AP data, etc like WEP and IP, but still no internet...what do i need to do?

---

### Post by Metaljaz on 2007-01-21
run list hardware from the terminal window:
 
lshw

go to the bottom where you see *network. Check the product which is the name of your card
and then check vendor which is the name of the chipset. Make sure the drivers for that
chipset are installed.

---

