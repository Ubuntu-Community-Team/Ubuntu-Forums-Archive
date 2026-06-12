---
title: "Grub Problem"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by jnmjr on 2011-05-20
Hello all:

I need help with Grub2. I have lost the boot menu, I run 10.04 on 1st HD, WinXP on 2nd HD. Grub2 is installed on both MBR's. From terminal all looks fine yet I boot directly to Ubuntu without menu. Bios is configured to boot from HD 1, Drives are SATA's. Any help would be greatly appreciated.:confused:

---

### Post by _0R10N on 2011-05-20
Have you tried runnning # update-grub? It will force grub to check what OS installations are available on your master drive.

Question: it always worked in this way, or something happened that caused this weird behaviour?

Regards!

---

### Post by jnmjr on 2011-05-20
> **_0R10N said:**
> Have you tried runnning # update-grub? It will force grub to check what OS installations are available on your master drive.

Question: it always worked in this way, or something happened that caused this weird behaviour?

Regards!


Thanks for your reply, actually I had a major brain freeze   :lolflag:         when I edited the etc/default/grub file, I forgot the minus on this line;

GRUB_TIMEOUT=-1

left out this causes menu not to appear.

---

### Post by _0R10N on 2011-05-24
Well! I'm glad you worked it out and that you aren't afraid of experimenting! thumbs up!

---

