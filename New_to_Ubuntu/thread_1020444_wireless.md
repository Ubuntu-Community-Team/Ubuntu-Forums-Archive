---
title: "wireless"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by garrydog on 2008-12-24
Hi
I am running wired at present ,will it be possible to use my netgear wnp111 wireless adapter with ubuntu .If it is possible will someone please tell me how to do it .
Thanks .

---

### Post by RomeReactor on 2008-12-24
Hi. Is this a PCI card, or a USB dongle? Please open a terminal (Applications->Accessories->Terminal), paste the following commands, and post the output of each:

```
lspci -nn
```
```
lsusb
```

---

### Post by mapes12 on 2008-12-24
> **garrydog said:**
> Hi
I am running wired at present ,will it be possible to use my netgear wnp111 wireless adapter with ubuntu .If it is possible will someone please tell me how to do it .
Thanks .
Give it a go. I would Shutdown, remove the wired connector, insert the wifi device, reboot and see if it works.

---

