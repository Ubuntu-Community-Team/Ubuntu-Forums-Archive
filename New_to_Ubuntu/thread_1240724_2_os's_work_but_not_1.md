---
title: "2 os's work but not 1"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by dustinz31 on 2009-08-15
Ok so i got a new hard drive a couple of weeks ago and i installed ubuntu on the whole thing and when i went to start the computer it didnt load anything and after the mobo boot screen just went to a black screen with a blinking line in the corner. Figuring it was a bad hard drive i sent it back and got a new one, tried same thing on new one but with linux mint, did the same thing, so installed ubuntu and same thing, so i went in and installed mint on half and ubuntu on the other half and now it boots into ubuntu, but not mint! what the heck is going on and how can i just get mint on there? its for my mom and she like mints interface more sorry ubuntu guys haha

---

### Post by sideaway on 2009-08-15
Hey there, I'm not entirely sure why. But does Grub detect both installations?

---

### Post by dustinz31 on 2009-08-15
yes, it does, it also shows two extra installs of ubuntu, now i have ubuntu on her other hard drive (old 40gb) but thats supposedly disabled by the bios, but no matter what i boot from in grub, be it either ubuntu or mint it just takes me strait to the newest install of ubuntu.

---

### Post by sideaway on 2009-08-15
What does your menu.lst look like?
will be in /boot/grub

Also post the output of

```
sudo fdisk -l
```

---

### Post by dustinz31 on 2009-08-15
ok ill get that stuff tomorrow and post it, i have to work all night so i cant get it right now. thanks for helping though, thought maybe someone would have maybe ran into this before

---

