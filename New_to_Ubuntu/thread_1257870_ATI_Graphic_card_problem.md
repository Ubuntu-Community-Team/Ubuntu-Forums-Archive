---
title: "ATI Graphic card problem"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by MelDJ on 2009-09-04
hi there. recently my compiz stopped working. i installed my ati graphic card following the steps here: [http://ubuntuforums.org/showthread.php?t=1235530](http://ubuntuforums.org/showthread.php?t=1235530)
 i then installed my ati graphic card from the hardware drivers and now my system runs on  low resolution. should i reinstall the driver the 1st way or is there another way to solve this problem? i have a dell studio 1555 laptop with a ATI HD4570

---

### Post by halitech on 2009-09-04
after you did the install, did you run
```
sudo aticonfig --initial
```

---

### Post by MelDJ on 2009-09-04
no..

---

### Post by Mortus Pryde on 2009-09-04
You may also want to check what version of ATIs Driver you are trying to install and see if your card is still supported under that driver. ATI dumped support for almost all but their most recent cards, some no longer supported are also still being used in currently sold machines. If this is the case for you, then you will have to find the older driver unfortunately.

---

### Post by halitech on 2009-09-04
the 4570 should work under the new 9.8 drivers

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.39&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.39&lang=English)

---

### Post by MelDJ on 2009-09-04
so should i disable the driver in hardware driver? and how do i uninstall my current ati control centre? when i run it, it says no graphic card is installed or the graphic card is not working properly

---

