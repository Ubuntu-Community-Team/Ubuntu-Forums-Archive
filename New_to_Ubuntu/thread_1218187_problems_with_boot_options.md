---
title: "problems with boot options"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by lmgranger on 2009-07-20
I am using Hardy Heron, 8.04 on a Dell D800 laptop. I have updated several times in the past year, and now have - on the options to boot page - upwards of 20 choices to boot UBUNTU before I can scroll down far enough to find Windows as a choice to boot from a separate partition on the HD. Is there a way I can eliminate some of these choices and why do they keep adding in? I may transfer data and go to the new version. Would that solve this problem?

---

### Post by ~sHyLoCk~ on 2009-07-20
> **lmgranger said:**
> I am using Hardy Heron, 8.04 on a Dell D800 laptop. I have updated several times in the past year, and now have - on the options to boot page - upwards of 20 choices to boot UBUNTU before I can scroll down far enough to find Windows as a choice to boot from a separate partition on the HD. Is there a way I can eliminate some of these choices and why do they keep adding in? I may transfer data and go to the new version. Would that solve this problem?

```
sudo gedit /boot/grub/menu.lst
```

Delete the irrelevant [as in old entries] and Keep the most recent entry and the Fallback entry..

---

### Post by TeoBigusGeekus on 2009-07-20
It's just a list of older kernels.
Open terminal and type 
```
gksudo gedit /boot/grub/menu.lst
```
Post us the contents.

---

