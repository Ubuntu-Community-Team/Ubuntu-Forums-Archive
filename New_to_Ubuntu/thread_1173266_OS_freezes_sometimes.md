---
title: "OS freezes sometimes"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by bradfordmayne on 2009-05-29
I installed jaunty through wubi.  Sometimes the mouse and everyhing just freezes up.  Is there any way I can find out why this is happening?  This is on a laptop.

---

### Post by agurk on 2009-05-29
Could be overheating, try monitoring the temperatures in your laptop.

It could also be some other kernel bug; I had similar symptoms with a slightly older AMD64 machine and had it fixed by activating the 'pre-release' repository and installing the latest kernel only.

---

### Post by agurk on 2009-05-29
Ugh, strike that. I just had another lockup while doing some compiling in 'safemode with networking', so no X involved even.

---

### Post by porchrat on 2009-05-29
I get that too on an Acer travelmate. Seems to come and go, often goes whole days without a lockup and then other days locks every few minutes.

I end up having to switch off the machine, can't even get a terminal through ctrl+alt+F1 etc.

At first I thought it was some sort of ACPI issue, haven't tried booting with "noacpi" yet, but I'll give it a go if it continues. Seems like this is a pretty common problem on laptops with 9.04.

---

### Post by albinootje on 2009-05-29
> **bradfordmayne said:**
> I installed jaunty through wubi.  Sometimes the mouse and everyhing just freezes up.  Is there any way I can find out why this is happening?  This is on a laptop.

Check the log files, specifically the kern.log* and syslog* in /var/logs/

---

