---
title: "screen resolution"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by albatro on 2009-04-03
i recently installed ubuntu 8.10 with the intention to switch over step by step and finally forget about windows. i am pretty happy with the results until now but i can't adjust the screen resolution to the desired level. the only alternatives offered in preferences are 640x480 and 800x600. but my screen can manage 1024x768. how can i adjust? the grafics card is from nvidia model GeForce 6100 nForce 405. hope this gives enough info for fixing the problem. thanks for your suggestions.

---

### Post by Volt9000 on 2009-04-03
Install the nvidia graphics driver. Click System > Administration > Hardware Driver and install the recommended driver. Then restart X (Ctrl+Alt+Backspace) and you should be able to access higher resolutions.

---

### Post by Temposs on 2009-04-03
You probably just need to fix up your graphics settings. 


After trying the post before mine, if that doesn't work, try booting into recovery mode by pressing escape at the GRUB countdown. Then choose the second option in the list which should be recovery mode. At the recovery mode menu, choose xfix. You can see if that fixes your problems.

If that doesn't do anything, then at a command prompt, type:

```
sudo nvidia-xconfig
```

See if that does anything. You'll need to restart after both of these options.

---

### Post by albatro on 2009-04-07
thank you both for your help. downloading the correct driver solved the whole problem. could not imagine it was this simple. thanks again.

---

