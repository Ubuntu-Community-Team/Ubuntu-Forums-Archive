---
title: "Disable madwifi"
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by Rob2687 on 2005-11-12
My PCMCIA card has an Atheros chipset but madwifi doesn't fully support it so it won't connect to anything.
How can I disable madwifi and use ndiswrapper instead?

---

### Post by Lambert on 2005-11-12
You'll want to do a little more research on what I offer but I believe you need to remove the driver by

```
sudo modprobe -r ath_pci
```

then follow the steps for setting up ndiswrapper

---

