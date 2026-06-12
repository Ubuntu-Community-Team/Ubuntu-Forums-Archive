---
title: "Nvidia card with Ubuntu 8.1"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by pearlbeer on 2008-12-14
I just upgraded to 8.1 and it will not load the gnome interfaace...when I boot it goes straight to terminal and says: Failed to load module "Nvidia" No drivers available.

I am a bit of a commandline-tard so any help would be appreciated. I think my card is a Gforce 7500.

---

### Post by dwasifar on 2008-12-14
Well, since you only have commandline available to you:

```
sudo apt-get install envyng-core
sudo envyng -t
```

This will walk you through downloading and installing the appropriate nvidia driver for your hardware.  After that, reboot, and all should be well.

---

### Post by Shhnap on 2008-12-14
I think I had the same problem. Try uninstalling the nvidia drivers and then see if it will run with the lowest graphics settings. Just do a sudo apt-get remove yourNvidiaDriver from the terminal that appears.

That is not really a fix though so you might want to wait for somebody to help you that has more experiance with intrepid.

---

### Post by pearlbeer on 2008-12-14
dwasifar-
thanks much. that worked great. i think last time i installed ubuntu before i installed the card...then i mjust used the graphical envy to get it right...just command line now...not my forte. anyway, thanks much. worked like a charm.

---

