---
title: "Beryl Help"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by friyia@hotmail.com on 2009-04-13
Hey ubuntu users out there I have heard of this program Beryl that makes  the Ubuntu Desktop look pretty sick. I was curious as to how you install and use it

---

### Post by Jakey_TheSnake on 2009-04-13
Beryl is deprecated and unsupported, compiz has replaced it. Open up Synaptic Package Manager from System > Administration, search for "compiz" and install "CompizConfig Settings Manager". 

Afterwards, access it via Systems > Preferences.

Play with the effects!

---

### Post by lovinglinux on 2009-04-13
Recommended reading

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by skymera on 2009-04-13
Compiz Fusion is enabled by default providing you have a graphics card that can handle it and the correct graphics driver installed.

Quick question, what graphics do you have?
This will help troubleshooting if any problems occur.

---

### Post by friyia@hotmail.com on 2009-04-13
> **skymera said:**
> Compiz Fusion is enabled by default providing you have a graphics card that can handle it and the correct graphics driver installed.

Quick question, what graphics do you have?
This will help troubleshooting if any problems occur.

I dunno man :( it's not working

cause like when I go to set my effects on the like Visual Effects thingy From Normal to like one of the other options it fails :(

---

### Post by Jakey_TheSnake on 2009-04-14
Try going to System > Administration > Hardware Drivers, does it say you can use any restricted drivers? 

Otherwise, post output of:

```
lspci -v | grep VGA
```

You most likely need to install the linux drivers for your graphics card, this should tell you what it is.

---

