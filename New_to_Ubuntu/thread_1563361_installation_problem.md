---
title: "installation problem"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by zerobinary on 2010-08-29
I can't dual boot ubuntu 10.04 with window 7 ultimate. I try to partition the hdd but it is not working! I am using an alienware m11x with i5 and install with ubuntu live usb using linux live usb creator to create the live usb.

---

### Post by diablo75 on 2010-08-29
> **zerobinary said:**
> I can't dual boot ubuntu 10.04 with window 7 ultimate. I try to partition the hdd but it is not working! I am using an alienware m11x with i5 and install with ubuntu live usb using linux live usb creator to create the live usb.

Behind that error message window, what does it say?  Specifically, what is sda5 have for a mount point?

---

### Post by diablo75 on 2010-08-29
There's your problem.  sda5 needs its mount point to be specified.  Highlight it, click Change, and tell it to use / as its mount point.

---

