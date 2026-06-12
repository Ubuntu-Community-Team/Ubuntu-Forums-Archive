---
title: "My Wifi wont work"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by Jeffonfire on 2009-07-17
My wifi wont work. I installed ndiswrapper and  the driver for my **[B]BCM4318 AirForce Card. It still wont work.**
[/B]

---

### Post by TeoBigusGeekus on 2009-07-17
If you have access to wired network install wicd - it is generally better than gnome network manager when it comes to wireless.
```
sudo apt-get install wicd
```

---

### Post by Jeffonfire on 2009-07-17
Still wont work.:confused:

---

### Post by abn91c on 2009-07-17
if you have ubuntu 9.04 the drivers for the broadcom driver is included by default, did you look under hardware drivers to "activate" the BCM driver?
you will need to remove the ndiswrapper

---

### Post by Jeffonfire on 2009-07-18
Oddly this dosen't work.

This is the error code:

Sorry, the Jockey backend crashed. Please file a bug at:

  ubuntu-bug jockey-common

Trying to recover by restarting backend.

---

### Post by LewRockwell on 2009-07-18
I thought 9.04 corrected that problem...

unless it's a system we've not yet encountered...

.

---

### Post by Jeffonfire on 2009-07-18
So what do I do?:confused:

---

