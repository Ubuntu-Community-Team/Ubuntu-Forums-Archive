---
title: "ndiswrapper"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by unisol on 2007-08-02
im going to use ndiswrapper for my wireless card which use the rt61 driver. what do you suggest? the ndiswrapper that comes with the distro, or the latest version from sourceforge? im using feisty.

---

### Post by kevdog on 2007-08-02
You could use ndiswrapper, but suggest compiling the rt61 drivers from source code found at the serial monkey website.


Use this guide as a general guide of how to do this, but be mindful that you are using rt61 and not rt73:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

---

### Post by renzokuken on 2007-08-02
if you are comfortable compiling from source then use the latest version from sourceforge.

EDIT: what kevdog said

---

### Post by unisol on 2007-08-05
will i need to add te firmware?

---

### Post by kevdog on 2007-08-05
Just compile the driver and then load the module into the kernel, modify the /etc/network/interfaces file and thats it.  No additional steps for the wireless.

---

