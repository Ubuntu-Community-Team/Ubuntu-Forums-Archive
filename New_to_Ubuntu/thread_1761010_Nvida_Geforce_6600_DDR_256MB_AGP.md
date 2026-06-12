---
title: "Nvida Geforce 6600 DDR 256MB AGP"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by rbowen1 on 2011-05-17
This is a new install using a Nvida Geforce 6600 DDR 256MB AGP adapter.   I do not think that Ubuntu 11.04 OS is using the correct driver for the adapter.  The screen resolution seems to change on reboot.  Sometimes it will be 640 x 480.  Monitor properties currently show unknown with a resolution of 1280 x 1024 with a 50 Hz refresh rate.    I can click on detect monitor but no change.    

Additional drivers showed;
Nvida accelerated graphics driver (version 173)  This driver is not activated
Nvida accelerated graphics driver (version current) Recommended 

I downloaded the current driver and rebooted as requested.  Now I see 

Nvida accelerated graphics driver (version 173)  This driver is not activated
Nvida accelerated graphics driver (version current) Recommended This driver is activated but not currently in use. 

Please help.

---

### Post by TeoBigusGeekus on 2011-05-17
Give
```
gksu nvidia-settings
```
do your customization, press the "Save to X configuration file" after you're done, reboot and post us what happened.

---

### Post by rbowen1 on 2011-05-17
How do I get to the command line?

---

### Post by TeoBigusGeekus on 2011-05-17
Ctrl+Alt+T

---

### Post by Joe of loath on 2011-05-17
You may have to use the 173xx drivers, I don't believe your card is supported using the newer drivers.

---

### Post by rbowen1 on 2011-05-17
Slam dunk!   gksu nvidia-settings  & customized the display.  now shows using the current Nvida driver:  
                                 NVIDIA Driver Version:  270.41.06


Thanks a heap!    :)

---

### Post by TeoBigusGeekus on 2011-05-17
You're welcome. 
Don't forget to mark the thread as solved.

---

### Post by -=hazard=- on 2011-05-17
> **Joe of loath said:**
> You may have to use the 173xx drivers, I don't believe your card is supported using the newer drivers.

Yes it can. It can even use the latest drivers released on the nvidia website.

---

### Post by TeoBigusGeekus on 2011-05-17
I think that the 173xx drivers don't support the latest xorg server, but don't quote me on that.

---

