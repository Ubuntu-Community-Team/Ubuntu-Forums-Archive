---
title: "Upgrade problem"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by amityadav9314 on 2011-03-05
Hi!
I recentally upgraded to ubuntu 10.10 from ubuntu 10.04.
But while booting the secreen shows ubuntu 10.04 on the pink screen.
Can anyone tell me how to change that to ubuntu 10.10?
Thanks!

---

### Post by davidmohammed on 2011-03-05
I presume you mean that you just see a black screen with a blinking cursor until the login screen appears?

If so try the following in a terminal session (Accessories - Terminal)

```
sudo su

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u

exit
```

---

### Post by amityadav9314 on 2011-03-05
> **davidmohammed said:**
> I presume you mean that you just see a black screen with a blinking cursor until the login screen appears?

If so try the following in a terminal session (Accessories - Terminal)

```
sudo su

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u

exit
```


No, The screen appears but it's still like the old one showing ubuntu 10.04 instead of 10.10.

---

