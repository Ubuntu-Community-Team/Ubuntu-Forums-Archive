---
title: "Ubuntu and nVidia GTX 240 graphic drivers"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by Cha0sBG on 2010-08-03
Hello i'm having trouble installing the nVidia drivers for linux. It says it can't open the file. File format: .run Any suggestions or tutorials ?

---

### Post by sikander3786 on 2010-08-03
Hi.

Did you try installing the latest version from System >>> Administration >>> Hardware Drivers?

I think you should install the driver packages from repositories instead of downloading the .run from manufacturers website.

If you still want to install the .run package there should be installation instruction on the manufacturer's website. This is also a good how to for .run

[http://ubuntuforums.org/showthread.php?t=239797](http://ubuntuforums.org/showthread.php?t=239797)

Regards.

---

### Post by realzippy on 2010-08-03
+1 on that.Choose the "current" driver.

If you install from nvidia's .run file,you have to repeat installation after every kernel-update.

---

### Post by Cha0sBG on 2010-08-03
Thank you for the link, i was able to open it, but the problem is i'm trying to install it on a virtual machine for testing purposes and the installer says it has to be run as root. May telling me how to do that?

---

### Post by realzippy on 2010-08-03
You **CANNOT** install Nvidia graphics driver on a virtual machine.
The machine is virtual,so it's graphics card is also virtual of course.

If you want some (poor) 3D acceleration in a virtual machine,you can install the "guest additions" if using *virtual box*.

---

### Post by Cha0sBG on 2010-08-03
Oh i didn't realize that. I'm kinda new to all this. Thank you for all your help :)

---

### Post by realzippy on 2010-08-03
So set thread as "solved" please...have fun!

---

