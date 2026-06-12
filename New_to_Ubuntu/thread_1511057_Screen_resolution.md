---
title: "Screen resolution"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by dev1152 on 2010-06-16
I have loaded ubuntu 9.10 on to my old PC.  I can't change the screen resolution higher that 800 x 600.  Have tried display preferences any ideas?

---

### Post by dev1152 on 2010-06-16
:confused:> **dev1152 said:**
> I have loaded ubuntu 9.10 on to my old PC.  I can't change the screen resolution higher that 800 x 600.  Have tried display preferences any ideas?

---

### Post by roger_1960 on 2010-06-16
Hi

What type of graphics chipset does it have?  The command > lspci run in a terminal should list it (among many other things)

---

### Post by dev1152 on 2010-06-16
> **roger_1960 said:**
> Hi

What type of graphics chipset does it have?  The command  run in a terminal should list it (among many other things)

NVidia NV11DDR GForce 2

---

### Post by roger_1960 on 2010-06-16
Hi

Looks like its a known bug - see

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/502669](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/502669)

---

