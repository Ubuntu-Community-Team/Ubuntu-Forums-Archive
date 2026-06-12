---
title: "Command line for wi/fi adapter chipset all need help installing RT73 chipset driver"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by arce on 2009-05-03
What is the command line in terminal to look at my current wi/fi adapter chipset?


I'm having a very hard figuring out how to install my Wireless AWUS036s RT73 chipset USB adapter.


Is the driver needed? or is the driver supplied by Ubuntu 9.04 by default?


I want to try this tutorial:[http://ubuntuforums.org/showthread.php?t=848445&highlight=diepruis](http://ubuntuforums.org/showthread.php?t=848445&highlight=diepruis)

I just found this tutorial today and need help installing.

---

### Post by cariboo on 2009-05-04
To see if your wireless device is detected and the driver loaded open a terminal and type:

```
sudo lshw -C netwrk
```

---

### Post by arce on 2009-05-04
Thanks for the command.

---

