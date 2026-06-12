---
title: "What is a kernel patch and how do I use it?"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by mahela007 on 2009-12-15
What is a kernel patch and how do I use it? also how do I update the kernel?

---

### Post by tom.swartz07 on 2009-12-16
> **mahela007 said:**
> What is a kernel patch and how do I use it? also how do I update the kernel?

kernel patch is an update to the underlying code that runs your ubuntu/ *nix OS. usually theyre updated to fix security holes or solve problems that occur from bad code.

all you have to do to update the kernel is open system>administration>update manager 
check for updates, apply them, and youre all set!

---

### Post by mahela007 on 2009-12-16
Thanks.. DO they come from the repositories just like the other packages ? and if so, how long does it take an update / patch to get into the repos after it has been written?

---

### Post by ~sHyLoCk~ on 2009-12-16
```
patch -p1 < patchfile
```

---

### Post by mahela007 on 2009-12-16
what does that do?

---

### Post by 3rdalbum on 2009-12-16
A patch is something that you can apply to the kernel source code (not to the compiled, machine-usable version).

Any patches that fix security issues or critical hardware problems will be applied to the kernel's source code and compiled at Canonicals end, and then the new compiled kernel will be pushed out to you in Update Manager. There is testing that is applied to the patched kernels before they are pushed out to you which can vary the amount of time between the patch being written and the new kernel being pushed to you, but usually it should be less than a day.

For the moment you shouldn't worry about applying a patch to your kernel; just keep your system up-to-date with the Update Manager.

---

### Post by mahela007 on 2009-12-16
Ok.. that's all I need. 
But just out of curiosity, what would I need to do if I wanted to apply a patch manually? say I found a patch that caconical isn't aware of I wrote my own patch (that won't happen for another few centuries ;-)). how would I apply such a patch?

---

