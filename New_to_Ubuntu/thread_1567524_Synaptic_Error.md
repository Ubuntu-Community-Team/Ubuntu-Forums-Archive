---
title: "Synaptic Error"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by BJones007 on 2010-09-03
Tried downloading cheese through synaptic, but my pc froze so I had to turn it off holding down the power button and now i'm getting this error message whenever I open synaptic: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." and then then the window closes. Help please.

---

### Post by kroq-gar78 on 2010-09-03
you have to boot into recovery mode (option at the grub bootloader where it says different linux images/headers; will say grub at the top) of the latest image (top-most) and select "run dpkg to fix broken packages" or something similar to that in the recovery menu. Also update your grub there too and select "clean" to make some space. Then reboot by going into the "root shell prompt" (option at the recovery mode menu) and do

```
sudo shutdown -r 0
```to reboot the system. Just go back into the regular system and have fun!

EDIT: You don't HAVE to go into recovery mode but it's much easier to do so in my opinion

---

### Post by Old *ix Geek on 2010-09-03
> **BJones007 said:**
> Tried downloading cheese through synaptic, but my pc froze so I had to turn it off holding down the power button and now i'm getting this error message whenever I open synaptic: "E: dpkg was interrupted, you must manually **run 'sudo dpkg --configure -a'** to correct the problem. 
E: _cache->open() failed, please report." and then then the window closes. Help please.From a command line you need to run:
```
sudo dpkg --configure -a
```

---

### Post by BJones007 on 2010-09-04
Thanks dude, worked exactly as you said (y)

---

### Post by kroq-gar78 on 2010-09-04
mark the thread as solved (thread tools (upper-right) => Mark thread as solved)

---

