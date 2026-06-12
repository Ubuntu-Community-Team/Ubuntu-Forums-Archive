---
title: "How do I get original 10.04 Splash Screen back"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by jbocean on 2010-10-28
In my search for my favorite combination of theme & icons, I installed the Ubuntu studio theme which replaced the original splash w/ some studio one.

How do I get back the original 10.04 Ubuntu Splash screen (the orange-ish one w/ the dots)?

Thanks!

---

### Post by buntudawg on 2010-10-29
Hi.

You should be able to type:

```
sudo update-alternatives --config default.plymouth
```in the Terminal which will list the installed themes. Then just select the number that corresponds to the ubuntu-logo.

Good Luck.

---

