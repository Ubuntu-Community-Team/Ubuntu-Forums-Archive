---
title: "udev high cpu"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by Trinity33 on 2010-04-02
in karmic updating udev to version 147 6.1 make cpu working in about 30 to 50% probably some sort of bug. i reported bug already but no response. i got q9000 quad core. after downgrading it to version 147 6.0 cpu went straight to 0%. 

i tried lucid beta and i got the same problem with udev ver 151... does anyone know how to downgrade udev in lucid to version 147 6.0? Using synaptic i cant do it so is there any other way to do it?

---

### Post by Trinity33 on 2010-04-03
i found temporary solution after every bootup to karmic or lucid use command sudo restart udev or sudo stop udev after that cpu is going back to 0% thats not real solution and there is no proper fix for it  i think. matter is that udev 147 6.0 which is preinstalled in karmic doesnt use much of cpu but it doesnt recognise usb flash drive. udev 147 6.1 does recognise usb flash drive but use 40% of cpu the same in lucid after every bootup i need type sudo restart udev thats nonsense maybe someone could do something with it.

---

