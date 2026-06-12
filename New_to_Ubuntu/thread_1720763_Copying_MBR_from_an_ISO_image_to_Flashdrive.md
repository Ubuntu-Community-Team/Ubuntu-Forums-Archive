---
title: "Copying MBR from an ISO image to Flashdrive"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by Igneo676 on 2011-04-03
Basic Problem: I have a disk image that I cannot use any disk utility to place on a flash drive and have it successfully boot.

Solution: So my basic thought is that, of course, if I burn this same image to a CD it would successfully boot on my hardware (which, alas, lacks a CD drive). So, how would one use the dd command to copy the MBR from the iso image I have to the MBR of my flashdrive?

---

### Post by TeoBigusGeekus on 2011-04-03
Have you tried using the dd utility for the whole image?
```
dd if=/path/image.iso of=/dev/sdd
```
(replace sdd with your flash drive's device)

---

### Post by Igneo676 on 2011-04-03
Stupid me, I had created a partition and extracted the contents of the ISO to the partition itself. Stupid mistake, trying that now and seeing the results.

---

