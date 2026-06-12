---
title: "SOLVED-wireless failure after update"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by musical1too on 2008-06-05
Thank you, chili555, for your experience and insight. The Atheros 5007 wireless card is now recognized after I typed sudo modprobe ath_pci.

Will the module reload upon a new boot or is there something I can do to ensure its loading every time I boot?

---

### Post by petzworld999 on 2008-06-05
Add what you modprobed to the /etc/modules file.

```


sudo gedit /etc/modules


```

Then, add "ath_pci" to the bottom of the file. Make sure that line has no # on it.

---

