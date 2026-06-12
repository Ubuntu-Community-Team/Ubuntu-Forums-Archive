---
title: "ndiswrapper applying driver to wrong device"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by smokingwreckage on 2008-08-15
just put together a new box and i have hardy installed via wubi in xp (btw, i'm very new to the whole linux territory). i've installed ndiswrapper, utils, and ndisgtk, and used them to install the xp driver for my wireless card (d-link dwl-g520m). my problem is when i "ndiswrapper -l" it shows the driver being applied to the pci address of my onboard NIC and not my wireless card. ubuntu definitely sees the card, but it does not show up in network settings.

any help would be greatly appreciated.if it would be easy to get ubuntu to completely ignore my onboard NIC that is an option as i dont plan on using it.

---

### Post by smokingwreckage on 2008-08-15
scratch that, drivers applied to the right device according to "ndiswrapper -l", but the card isnt coming up in my network connections at all.

---

### Post by Ayuthia on 2008-08-15
> **smokingwreckage said:**
> scratch that, drivers applied to the right device according to "ndiswrapper -l", but the card isnt coming up in my network connections at all.

Can you post the results of:```

ndiswrapper -v
ndiswrapper -l
lshw -C network
uname -a
```

---

