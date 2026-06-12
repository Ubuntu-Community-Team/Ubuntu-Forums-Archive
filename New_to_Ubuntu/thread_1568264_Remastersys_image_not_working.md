---
title: "Remastersys image not working"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by Fifthmarch on 2010-09-05
I tried using remastersys, then running the .iso file on a virtual machine. This is what I got. Does anyone know what to do?

---

### Post by bodhi.zazen on 2010-09-05
> **Fifthmarch said:**
> I tried using remastersys, then running the .iso file on a virtual machine. This is what I got. Does anyone know what to do?

That error message means your iso is 64 bit, but virtualbox only supports 32 bit. Either you have a 32 bit processor, or your 64 bit processor does not support KVM .

You may have to burn the iso and boot the CD / DVD

---

### Post by Fifthmarch on 2010-09-05
Oh ok. I have a 64 bit processor, so I think the disk should boot properly once I burn it to a DVD. 

Thanks!

Cool Signature, btw.

---

