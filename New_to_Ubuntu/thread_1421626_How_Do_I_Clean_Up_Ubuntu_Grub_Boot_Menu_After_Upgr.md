---
title: "How Do I Clean Up Ubuntu Grub Boot Menu After Upgrades?"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by SecretFace on 2010-03-04
I just updated today from the "Update Manager" and rebooted and noticed the old entry was still there. I know it's in the /boot/grub/grub.cfg...but how do I remove the old entries from the list at boot? Please help and thanks in advance.

---

### Post by philinux on 2010-03-04
> **SecretFace said:**
> I just updated today from the "Update Manager" and rebooted and noticed the old entry was still there. I know it's in the /boot/grub/grub.cfg...but how do I remove the old entries from the list at boot? Please help and thanks in advance.

You could use system>admin>computer janitor.

Or synpatic. Search the kernel number and mark for removal/complete removal.

I always keep 2 installed just in case.

---

### Post by wojox on 2010-03-04
Run:

```
uname -r
```


See your newest kernel. Then open Synaptic and search for 

```
linux-image
```

Mark for Removal the old one's.

---

### Post by SecretFace on 2010-03-04
> **philinux said:**
> You could use system>admin>computer janitor.

Or synpatic. Search the kernel number and mark for removal/complete removal.

I always keep 2 installed just in case.

Doh! That makes sense...Thanks! :D

---

### Post by SecretFace on 2010-03-04
> **wojox said:**
> Run:

```
uname -r
```See your newest kernel. Then open Synaptic and search for 

```
linux-image
```Mark for Removal the old one's.

Thanks Again! I like the Fast responses. You guys are very helpful. Please mark as Solved...not sure how to myself or if I even can. Thank Again!

---

### Post by Paddy Landau on 2010-03-04
In addition to linux-image, also remove old versions of linux-headers and linux-restricted-modules (if you have them).
> **SecretFace said:**
> Please mark as Solved
Only you can do that. Go to the top of the page, click on the red [COLOR=Red]Thread Tools[/COLOR], and select *Mark this thread as solved.*

---

### Post by SecretFace on 2010-03-04
> **Paddy Landau said:**
> In addition to linux-image, also remove old versions of linux-headers and linux-restricted-modules (if you have them).

Only you can do that. Go to the top of the page, click on the red [COLOR=Red]Thread Tools[/COLOR], and select *Mark this thread as solved.*

 ;) Thank You!!!

---

