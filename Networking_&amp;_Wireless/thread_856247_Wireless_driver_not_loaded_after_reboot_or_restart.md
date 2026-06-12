---
title: "Wireless driver not loaded after reboot or restart"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by jbperkins on 2008-07-11
I'm trying to use a Senao NL-2511CD pcmcia wireless card to work in an IBM T21 ThinkPad.  It did not work at all to begin with so I started searching th e forums.  I found a thread about blacklisting the orinoco_cs module so that it does not get loaded and the hostap_cs driver gets used.  I did an lsmod and sure enough the orinoco_cs and the hostap_cs modules were loaded.  I blacklisted the orinoco_cs module and rebooted the system.  It still did not work.  I "hot-swapped" the NL-2511CD card and the system loaded the driver and brought up the card.  I set the WEP password in the configuration tool and all was well until I rebooted the system.  After reboot (or restart) the driver does not get loaded.  I verified this with lspcmcia.  If I hot-swap the card after reboot or restart the driver gets loaded and it works.  So, how do I get the driver to load after a reboot or restart?
Thanks,
Jim

---

### Post by ModelM on 2008-07-11
Just add the driver filename to the file:

/etc/modules

and you should be good to go.

---

### Post by jbperkins on 2008-07-11
I tried it with no luck.  lsmod always shows the driver is loaded.  lspmcia says there is not driver for the card loaded after a reboot.

---

