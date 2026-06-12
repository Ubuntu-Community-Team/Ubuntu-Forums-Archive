---
title: "oem install with safe graphics mode"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by KCormier on 2009-10-23
Hey all.  How can I boot into the oem install with safe graphics mode?

-Kevin

---

### Post by DezSP on 2009-10-24
I'm not quite sure what you mean. OEM means Original Equipment Manufacturer, which is pretty meaningless in the context of Ubuntu. The OS will automatically load a safe graphics mode if for whatever reason the normal X session fails (this is known as bullet-proof X and allows fairly easy graphics setup under Ubuntu).

---

### Post by qamelian on 2009-10-24
> **DezSP said:**
> I'm not quite sure what you mean. OEM means Original Equipment Manufacturer, which is pretty meaningless in the context of Ubuntu. The OS will automatically load a safe graphics mode if for whatever reason the normal X session fails (this is known as bullet-proof X and allows fairly easy graphics setup under Ubuntu).

Actually, it isn't meaningless as Ubuntu provides an OEM install mode for vendors who want to provide Ubuntu pre-installed. I believe it's one of the options on the Alternate Install CD.

---

### Post by KCormier on 2009-10-24
It's one of the alternate boot options on the normal live cd for 9.04 at least.  The only problem is that the install in safe graphics mode is also one of the alternate options...and it only allows you to select one alternate option.

I'm also familiar with bullet proof x, however there is a bug in the ati drivers on the live cd with my x1600pro card.  The driver locks up when X starts and I'm stuck.  It must be passing some option to the kernel that I could specify manually.  Anyone have any ideas?

-Kevin

---

