---
title: "Removing boot choices from grub in Puppy?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by ceaser_salad on 2009-02-28
Hi there

I've just put puppy 4.2 on an PC of mine, as a single OS. 
It seems really nice, and boots quite fast, but the fact that I have to choose it in the grub loader at start up is annoying.

Any help is appreciated.

Emile

---

### Post by BOZG on 2009-02-28
> **ceaser_salad said:**
> Hi there

I've just put puppy 4.2 on an PC of mine, as a single OS. 
It seems really nice, and boots quite fast, but the fact that I have to choose it in the grub loader at start up is annoying.

Any help is appreciated.

Emile

I'm not sure if you can get GRUB to automatically boot an OS but you could definately change the timeout settings so that GRUB would automatically load Puppy.

As root, try:

```
gedit /boot/grub/menu.lst
```

And search for this:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3
```

Change the number as you see fit.

---

### Post by BOZG on 2009-02-28
Alternatively, you can install StartUp-Manager which will allow you to edit the GRUB list through a GUI.

---

### Post by ceaser_salad on 2009-02-28
Thanks guys, I'll give that a try.

---

