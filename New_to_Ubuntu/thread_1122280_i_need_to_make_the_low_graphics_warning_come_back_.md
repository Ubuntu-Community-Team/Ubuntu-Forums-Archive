---
title: "i need to make the low graphics warning come back up"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by klein de usa on 2009-04-10
hi
   i'v been working an a computer with a nv graphics card, ubuntu kept booting in low graphics mode, i reinstalled nv new driver and rebooted and the low graphics warning came up again, i went into configure and and looked at the driver or ini file for the 17" flat panel dell screen it was set to pnp. and when i tryed to change it to a 17" flat panel it was asking me for a file.
   so i found the exe file for the 17" flat pannel install and down loaded it, used file roller to extract the ini file, rebooted and just before login a warning came up saying will start in low graphics mode at the bottom left of this warning i clicked on configure went to pic monitor and added the ini file i down loaded, rebooted and behold it booted with the right screen resolution 1024x768 !!!!!!!!!!!!!!!!!!!! before i could never get it past 800x600 and everyone kept telling me it was nv and the driver.
   so  i was not smart i pushed my luck and tried to change the graphics mode lol told me to reboot and right back to 800x600, my question is how do i make that warning come back up (gonome is starting in low graphics mode)  ??????????????????????????

---

### Post by sandyd on 2009-04-10
try this....

```

sudo dpkg-reconfigure -phigh xserver-xorg 

```

then change the driver... again to "nv"

sort of like this....
```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nv"                 
       
Option "RenderAccel" "0"                    
EndSection          

```
but thats just my xorg.conf 
and just a tidbit off the top of my head.

---

### Post by klein de usa on 2009-04-10
hi 
i don't think that will work, i need to make it look at my ini file for my 17" flat panel. and the configuration program that come up when the low graphics warning comes up is the only way i know to load the ini file for a monitor.

---

