---
title: "Is there anyway to re-install or reverse sound settings?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by listerdl on 2009-02-11
Everything was set up so nicely with the latest ubuntu version, Ibex, bt suddenly, I like many others, was hit by this mysterious sound removal issue. For no reason my sound vanished, (this is a popular bug/issue it seems for Ibex users) and I am thinking, is it possible to revert back to an older setting?

Thanks!

---

### Post by 73ckn797 on 2009-02-11
If the problem has occurred after a kernel update and you have the older kernel listed in the grub menu, you can boot into that kernel and see if the sound works again. I gather by your post that this has happened in Ibex only?

---

### Post by listerdl on 2009-02-12
Yes exactly, it only happened in Ibex. Caan you kindly tell me how to revert to the older grub menu? Thanks!

---

### Post by Elfy on 2009-02-12
Use the previous kernel in the menu list, it will look like

Current kernel 
Current kernel - recovery
Previous kernel
Previous kernel - recovery
and more if you have them

Pick the previous kernel - not recovery

---

### Post by listerdl on 2009-02-13
> **forestpixie said:**
> Use the previous kernel in the menu list, it will look like

Current kernel 
Current kernel - recovery
Previous kernel
Previous kernel - recovery
and more if you have them

Pick the previous kernel - not recovery

Thanks, but how do i do the above? I tried to access from the Applications / Places / Systems and I cant seem to find the kernel list....

Does anyone know? Thanks!

---

### Post by Elfy on 2009-02-13
The menu list shows when you boot

---

### Post by listerdl on 2009-02-13
thanks

---

