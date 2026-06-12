---
title: "linux-image"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by godsmAsh on 2009-12-05
i have linux-image 2.6 31-15-generic 2.6 31-15 50. if i uninstall the old linux image( linux-image 2.6 31-14-generic 2.6 31-14 48) would it affect my computer or performance?

---

### Post by 73ckn797 on 2009-12-05
You can remove the earlier kernel and image via Synaptic. I just removed the -14 kernel stuff and restart caused no problem. Grub2 also recognized the -14 kernel was no longer installed and deleted it from the boot menu automatically.

---

### Post by godsmAsh on 2009-12-05
thanks...

---

### Post by bumanie on 2009-12-05
There is no problem with removing old kernels, however it is a good idea to keep an old kernel that is known to work, in case an update to the present kernel causes issues for your computer. Many users keep one old kernel as a back-up, just in case.

---

### Post by 73ckn797 on 2009-12-05
> **bumanie said:**
> There is no problem with removing old kernels, however it is a good idea to keep an old kernel that is known to work, in case an update to the present kernel causes issues for your computer. Many users keep one old kernel as a back-up, just in case.

I did not mention this fact. I keep at least the last working kernel installed until I am certain there are no problems. Typically another comes out before I ever delete that older one so I always have 2 installed.

---

