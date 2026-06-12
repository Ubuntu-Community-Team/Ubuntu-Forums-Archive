---
title: "Kill 2 sec gap"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by newlinuxuser2008 on 2008-12-19
I have only ubuntu on my computer and i want to kill the 2 sec gap with grub

how?

---

### Post by taurus on 2008-12-19
You can change the **timeout** in /boot/grub/menu.lst.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by vikramaditya on 2008-12-19
Let me know if you change it to "0", **newlinuxuser2008**.  I've been tempted to try, but afraid it might break something. :shock:

---

### Post by newlinuxuser2008 on 2008-12-20
> **vikramaditya said:**
> Let me know if you change it to "0", **newlinuxuser2008**.  I've been tempted to try, but afraid it might break something. :shock:

it worked.

---

