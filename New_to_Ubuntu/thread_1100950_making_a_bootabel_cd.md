---
title: "making a bootabel cd"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by shayvasa on 2009-03-19
hey whats up?
so i have this cd rom with windows xp on it but its not a bootable cd....of course its not original...so i was wondering how i can make that cd bootable without erasing the content or making a new cd.
thanx

---

### Post by 73ckn797 on 2009-03-19
Not original? Meaning that it is a copy (pirated)?

---

### Post by cwsnyder on 2009-03-19
> **shayvasa said:**
> so i have this cd rom with windows xp on it but its not a bootable cd....of course its not original...so i was wondering how i can make that cd bootable without erasing the content or making a new cd.
thanx
I think you are out of luck.  You need to write the master boot record (MBR) of the CD to make it bootable, and if it is already written, you cannot do that.  You might be able to copy the CD to an ISO file, mount the file, and copy the boot record from a bootable copy of XP to the MBR of the ISO and burn the ISO back to a CD, but I haven't done that, and have no idea how complicated it would be.

Sorry I only have bad news to offer.

---

### Post by kanikilu on 2009-03-19
Even if this is a legit "backup" or some-such of XP, I don't believe you can add a boot image to an existing CD.

---

