---
title: "Drivers for noka N-73"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by krishnakittu on 2009-02-27
Hi, i want to transfer my pics from my mobile to pc.how can i do it in ubuntu 8.10

Phone model is Nokia N-73

---

### Post by llamabr on 2009-02-27
This is very rarely a drivers problem.

How are you connecting?  You probably have a standard usb cable that connects pc to camera?

Plug it in.  Gnome will automount it, and put it on your desktop.

If it doesn't, plug it in, wait a few seconds, and post the output of

```
lsusb
tail dmesg
```

---

### Post by deepclutch on 2009-02-27
have the same phone(N73ME).It automounts.when plugin the phone via usb ,select "mass storage" mode.

---

### Post by krishnakittu on 2009-02-27
Thanks dude its working now

---

