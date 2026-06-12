---
title: "ubuntu 8.04 asus laptop acpi/wirelless problem"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by psujok on 2008-06-12
Please help me !!!
My wireless connection worked fine in previous versions of ubuntu but when I installed the 8.04 I can`t get it to work.
When I start my laptop the wifi led is on but when The Xwindow server starts the led turns of. The wifi is working ok in the rescue mode.
My barebone is Asus S37E and the wifi is bcm4328 based asus wl270 card.
Read almost all on the forum but still no success.

---

### Post by Ayuthia on 2008-06-12
> **psujok said:**
> Please help me !!!
My wireless connection worked fine in previous versions of ubuntu but when I installed the 8.04 I can`t get it to work.
When I start my laptop the wifi led is on but when The Xwindow server starts the led turns of. The wifi is working ok in the rescue mode.
My barebone is Asus S37E and the wifi is bcm4328 based asus wl270 card.
Read almost all on the forum but still no success.
I am assuming that you are using ndiswrapper.  Can you check and see if ndiswrapper -v is showing that you are using version 1.50 or higher?  If it is, can you post your lshw -C network results?

---

