---
title: "Terminal code to get hardware configuration"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by webwiller on 2009-09-16
hi all!
I'd need to have specs of my hardware configuration, more about video-card and supported plug types for it.
I was wondering about which command should I use in Terminal to get the most complete answer.
Ty all! ;)

---

### Post by Hospadar on 2009-09-16
There are many commands you might use:
lspci - pci info
lshw - all hardware info
xrandr -q - xserver info

---

### Post by GenePayne on 2009-09-16
Try:

```
sudo lshw
```

---

### Post by webwiller on 2009-09-16
Ty!!! ;)

---

