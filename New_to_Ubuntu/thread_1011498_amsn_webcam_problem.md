---
title: "amsn webcam problem"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Thoralex on 2008-12-14
Hi!
I finally got my webcam working on the desktop, but i doesent work with amsn. works with ekiga and cheese, but in amsn there is no picture. it works on my laptop with 8.04 (dektop has 8.10)
Anyone know what could cause this?

---

### Post by spiderbatdad on 2008-12-14
> libv4l-0:
works with Skype, Cheese
does not work aMSN, Kopete, Camorama.
with this:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so xxx
camorama, kopete works, amsn does not.
none of this three works with LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
This is one experience. The experience are not consistent, and are dependent upon hardware.

[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)

---

### Post by Sef on 2008-12-14
1) What webcam do you have?

2) Are you using it on both your desktop and laptop?

---

### Post by Thoralex on 2008-12-14
> **Sef said:**
> 1) What webcam do you have?

2) Are you using it on both your desktop and laptop?

1) logitech quickcam for laptops

2) not at the same time, just fixed the desktop after the drive crashed so i've been using it with the laptop for a while

---

### Post by Thoralex on 2008-12-14
> **spiderbatdad said:**
> This is one experience. The experience are not consistent, and are dependent upon hardware.

[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)

I trued to find what that was meaning, but it seems i'll need some spoon feeding here:confused:

---

### Post by spiderbatdad on 2008-12-15
here are a few commands to help gather information. They can be copy/pasted or typed one at a time. Please save the outputs and include in another post here. Make sure cam is plugged in.
```
ls /var/cache/apt/archives | grep libv4l-0
lsusb
lsmod 
```unplug your cam and plug it in again.
```
dmesg | tail
```

---

