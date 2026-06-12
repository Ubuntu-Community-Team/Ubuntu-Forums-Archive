---
title: "Still having printing problems with Photosmart 7450"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by woody1 on 2009-03-07
I thought this problem had been resolved !!! It worked reasonably for a day.
Printing is still very much a hit or miss affair.
I have installed the latest Hplip, edited hpmud.rules.
One thing that I have noticed is when the printer stops printing lsusb stops finding it and the only way to reestablish communication is to cycle power to the printer off and on.
What else can I be doing wrong?

---

### Post by linux6994 on 2009-03-07
Perhaps try a different port via Printer properties under the device url: section. I have found that selecting via hp: or usb dows make a difference.

Also have you tried to delete the printer from the Administrator > Printers and the reboot and let hplip find it by it self?

Just some ideas. Good luck.

---

### Post by woody1 on 2009-07-12
Thanks for your suggestions, it is still being obstinate!!

---

