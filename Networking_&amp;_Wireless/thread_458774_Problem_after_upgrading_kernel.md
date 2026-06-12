---
title: "Problem after upgrading kernel"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by chr3681 on 2007-05-30
Okay, so I ran the many updates that were recently available for my computer which included a kernel update, and now the only way I can get my wireless card to work is to boot with the previous kernel. What can I do to fix this? The card is a D-Link DWL-G630. I am using madwifi (patched) drivers that worked fine until the update.

---

### Post by Kobalt on 2007-05-30
I guess you need to boot from the new kernel and rebuild/recompile your drivers against the new kernel.

---

### Post by chr3681 on 2007-05-30
thanks! that worked i just needed to redo make, make install, and modprobe for the madwifi =)

---

