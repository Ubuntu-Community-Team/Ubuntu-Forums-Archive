---
title: "How do i create a blacklist file?"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by ludu900 on 2008-09-29
I am a complete noob.
I am trying to follow the directions in the sticky for enabling my bcm4328 network card but i do not know how to create a blacklist file or what a blacklist file even is.
Can anyone tell me how to get past the first step???

---

### Post by eldragon on 2008-09-29
im not sure how to get the broadcomm chipset wireless working. but if you are installing another kernel module for it, then you need to blacklist the modules included with ubuntu.
you need to add them to the end of the file /etc/modprobe.d/blacklist

to do this you need to do:
```

$ sudo echo "module_name" >> /etc/modprobe.d/blacklist

```

or edit the file with gedit and add it that way, remember you need to be root to do that.

---

