---
title: "monitor driver seems to have been deleted"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by mrmgh1 on 2010-05-14
I use a NEC lcd 1770gx monitor and until 2 days ago all was well, however two days ago I booted up and every thing has gone mad. The system seems to think the desktop is 3 times its actual size and I can only see part of the desktop. Every thing (icons, windows) is huge. 
from what I can see on here I have a driver problem, but have no idea how to find the correct driver , let alone install it and make it work. 
I get an error message referring to ubuntu running on low graphics mode, and messages about NVIDIA drivers, but I don't have the technical knowledge to resolve this.   PLEASE Help. 
I dont recall downloading anything new, or changing any settings but ....

---

### Post by cariboo on 2010-05-14
Open a terminal and type:

```
sudo nvidia-xconfig
```

the above command will recreate your /etc/X11/xorg.conf

Once the command has completed, reboot your system, and you should end up with a working desktop again if you haven't changed anything else.

---

### Post by mrmgh1 on 2010-06-17
sorry for the long delay. 
seems I changed something else then as that made no difference .

---

