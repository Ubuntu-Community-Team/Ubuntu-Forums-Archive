---
title: "Broadcom 4310 startup issue - long pause during boot"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by CTenorman on 2008-02-03
Hi guys,

I had a fully operational Broadcom 4310 until this morning. When I booted it up this morning the card was not found, and I had to re-install the driver manually in ndiswrapper. I had to keep repeating this each boot until I discovered that ndiswrapper was not in my /etc/modules. After adding it, I'm connected on boot. Does anyone know why it would go away?

The other new change is that my boot time is extended. Just as icons start to fill across my top panel, the machine pauses, and essentially nothing happens for about 10-15 seconds. Then it finishes loading up, and all is well. This pause did not exist before.

I'm wondering, is this a device conflict of some sort? Does anyone have any ideas about why this might happen? Thanks,

Scott

---

