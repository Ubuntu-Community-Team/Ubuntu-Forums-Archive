---
title: "Nvidia lag"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by jtblackguy on 2009-12-13
Hi, i am using ubuntu 9.10 and i find that using the restricted Nvidia drivers for my geforce2 mx 400, the interface is kind of laggy. When i use the open source nouveau driver however, the interface is snappy again. Does anyone know what the problem could be and how to fix it?

Thanks

---

### Post by 4Orbs on 2009-12-13
I would guess that when you activate the nVidia driver, Ubuntu automatically turns on the desktop 3D effects, which consume more of your resources than the nv driver (which is 2D and doesn't permit 3D effects). Activate the driver, turn off desktop effects in the Appearance mgr and you should achieve the best performance your computer is capable of.

---

### Post by ZipoTe on 2009-12-17
The same here. Doesn't matter if I turn off desktop effects or not, the same happens.
And in my case, Ubuntu doesn't remember my screen resolution when I reboot the computer. Before using the nVidia driver resolution was working OK
:(:(

---

