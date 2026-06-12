---
title: "tg3 wake_on_lan"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by jobertel on 2006-12-22
I installed ubuntu-6.06.1-server-i386 on an HP TC2120 with a Broadcom 5702 network card embedded on the motherboard. I am trying to enable wake-on-lan at bootup, and I am having trouble finding the correct location and syntax to enable the option. I tried 

options tg3 enable_wol=1 

in /etc/modprobe.d/options, but the module would not load and gave an error to the effect that enable_wol is an unknown option. Commenting the line out and running modprobe tg3 worked fine.

Any ideas on the correct location and syntax to enable this option?

BTW I saw other posts regarding troubles with Ubuntu not recognizing the Broadcom card. Mine was not recognized during installation so I added a 3Com 3C905B-TX and reinstalled. BOTH cards were recognized! I continued with the install setting up the Broadcom card and removed the 3Com card after the install completed. Everything is now fine except for above issue.

Any thoughts Bunters?

John B.

---

