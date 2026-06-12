---
title: "help, atheros chipset"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by nwadams on 2007-05-04
hi, i need help making my wifi card 

```
08:00.0 Class 3a6a: Atheros Communications, Inc. Unknown device 0023 (rev 86) (prog-if 11)
        Subsystem: D-Link System Inc Unknown device 3a6a
        Flags: 66MHz, medium devsel, IRQ 18
        Memory at 54000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

```

---

### Post by ronocdh on 2007-05-04
Try running ```
sudo update-pciids
```

---

### Post by nwadams on 2007-05-04
uhh and then what 
lspci -v gives me this now
```
08:00.0 Class 3a6a: Atheros Communications, Inc. AR5416 802.11a/b/g/n Wireless PCI Adapter (rev 86) (prog-if 11)
        Subsystem: D-Link System Inc Unknown device 3a6a
        Flags: 66MHz, medium devsel, IRQ 18
        Memory at 54000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

```

---

