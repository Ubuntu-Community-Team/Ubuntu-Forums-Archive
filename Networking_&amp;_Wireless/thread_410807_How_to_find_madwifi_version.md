---
title: "How to find madwifi version"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by MikeAK on 2007-04-16
Hi

How do I find which version of madwifi drivers/hal are loaded for my Atheros 5005G?

I want to upgrade to the latest (0.9.3) if I don't already have it, which I believe corrects the incorrect signal stregnth problem.

Thanks

Mike

---

### Post by spd106 on 2007-04-16
Try this command
```
modinfo ath_pci | grep version
```

---

### Post by MikeAK on 2007-04-16
Thanks for that. I've got version 0.9.2.1. So now to get to grips with compiling and installing a driver for the first time. I'm sure I'll be back soon....

Mike

---

