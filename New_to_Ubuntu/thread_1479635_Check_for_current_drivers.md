---
title: "Check for current drivers?"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-05-10
Hi, I'm having problems with compiz and a 3D game running very slowly after doing a fresh install with 10.04 64-bit Ubuntu. I did install the proprietary drivers, but it's almost acting like it isn't using them. What command would I use to check and make sure I really do have them installed correctly and running? 

OS: Ubuntu 10.04 64-bit

Gfx card: ATI Radeon HD 5770

---

### Post by cap10Ibraim on 2010-05-11
```
lspci
```

---

### Post by adam22 on 2010-05-11
ATI drivers suck for Linux, big time. Better off using the open source driver or trying a newer driver from the ATI site.

---

### Post by Ozymandias_117 on 2010-05-11
> **cap10Ibraim said:**
> ```
lspci
```

That simply tells you what PCI devices are connected... I know it is connected and seen by Linux, I need to know if it's using the proprietary driver I downloaded, or if it's still trying to use the generic VGA drivers.

---

### Post by Ozymandias_117 on 2010-05-11
> **adam22 said:**
> ATI drivers suck for Linux, big time. Better off using the open source driver or trying a newer driver from the ATI site.

I downloaded their newest proprietary driver. I'm just trying to make sure it is actually in use.

---

### Post by mikewhatever on 2010-05-11
Try this:

sudo lshw -C display | grep driver

---

### Post by Ozymandias_117 on 2010-05-11
> **mikewhatever said:**
> Try this:

sudo lshw -C display | grep driver

Thanks! It looks like it's using the drivers... Guess I'll have to start looking for other culprits.

---

